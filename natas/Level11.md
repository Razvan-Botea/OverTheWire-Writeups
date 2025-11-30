```
Username: natas11
Password: UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk
URL:      http://natas11.natas.labs.overthewire.org
```

- for this level, we get a simple page where we can imput a RGB value to change the backgorund color
- looking at the source code, i can see a PHP script that implements an authentication system using XOR encryption with cookies
```PHP
$defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");

function xor_encrypt($in) {
    $key = '<censored>';
    $text = $in;
    $outText = '';

    // Iterate through each character
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}

function loadData($def) {
    global $_COOKIE;
    $mydata = $def;
    if(array_key_exists("data", $_COOKIE)) {
    $tempdata = json_decode(xor_encrypt(base64_decode($_COOKIE["data"])), true);
    if(is_array($tempdata) && array_key_exists("showpassword", $tempdata) && array_key_exists("bgcolor", $tempdata)) {
        if (preg_match('/^#(?:[a-f\d]{6})$/i', $tempdata['bgcolor'])) {
        $mydata['showpassword'] = $tempdata['showpassword'];
        $mydata['bgcolor'] = $tempdata['bgcolor'];
        }
    }
    }
    return $mydata;
}

function saveData($d) {
    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
}

$data = loadData($defaultdata);

if(array_key_exists("bgcolor",$_REQUEST)) {
    if (preg_match('/^#(?:[a-f\d]{6})$/i', $_REQUEST['bgcolor'])) {
        $data['bgcolor'] = $_REQUEST['bgcolor'];
    }
}

saveData($data);

if($data["showpassword"] == "yes") {
    print "The password for natas12 is <censored><br>";
}

```

- `xor_encrypt`: XORs each character with the corresponding key character. If the input is longer than the key, the key repeats. Because of the way XOR works, the same function can be used for decryption
- `loadData`: checks if "data" cookie exists; decodes the content; validates the structure and format of the content
- `saveData`: saves data to cookie

- using this information, i created the following python script that uses the original cookie to find the key for the XOR encryption and create a malicious cookie with the showpassword parameter set to yes
```Python
import base64
import json
import urllib.parse

def xor_transform(data, key):
    """XOR encrypt/decrypt on bytes"""
    out = bytearray()
    for i in range(len(data)):
        out.append(data[i] ^ key[i % len(key)])
    return bytes(out)

def get_raw_key_stream(ciphertext, plaintext):
    """Recover the raw XOR stream (ciphertext ^ plaintext)"""
    length = min(len(ciphertext), len(plaintext))
    key_stream = bytearray()
    for i in range(length):
        key_stream.append(ciphertext[i] ^ plaintext[i])
    return bytes(key_stream)

def auto_find_repeating_key(key_stream):
    """
    Finds the shortest repeating pattern in a byte stream.
    Ex: b'eDWoeDWoeD' -> returns b'eDWo'
    """
    length = len(key_stream)
    
    for candidate_len in range(1, length + 1):
        candidate = key_stream[:candidate_len]
        
        repeats_needed = (length // candidate_len) + 2
        test_stream = (candidate * repeats_needed)[:length]

        if test_stream == key_stream:
            return candidate
            
    return key_stream

if __name__ == "__main__":
    print("=== NATAS 11 AUTOMATIC SOLVER ===")

    encoded_cookie = "HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D"
    
    encrypted_bytes = base64.b64decode(urllib.parse.unquote(encoded_cookie))

    default_data = {"showpassword": "no", "bgcolor": "#ffffff"}
    plaintext_str = json.dumps(default_data, separators=(',', ':'))
    plaintext_bytes = plaintext_str.encode('utf-8')

    full_key_stream = get_raw_key_stream(encrypted_bytes, plaintext_bytes)
    print(f"[+] Full Key Stream recovered: {full_key_stream}")

    key = auto_find_repeating_key(full_key_stream)
    print(f"[+] Pattern Detected: {key.decode()}")

    malicious_data = {"showpassword": "yes", "bgcolor": "#ffffff"}
    malicious_json = json.dumps(malicious_data, separators=(',', ':')).encode('utf-8')

    new_encrypted = xor_transform(malicious_json, key)
    
    final_cookie = base64.b64encode(new_encrypted).decode()
    
    print("\n=== MALICIOUS COOKIE ===")
    print(final_cookie)
```

- i can replace the old cookie with this one in the browser dev tools and refresh the page to get the password for the next level

# Password

- **yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB**
