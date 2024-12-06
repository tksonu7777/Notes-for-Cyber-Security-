# 5 Cryptographic Hash Functions and Applications (HMAC)

### SHA-1 is a popular heuristic hash function that is currently in vogue. In this experiment, we shall familiarize ourselves with SHA-1 as well as look at one important application of hashing, namely, the HMAC algorithm, which is currently used in the Internet to achieve data integrity.






# code 
  ```py

import hashlib
import hmac

def hmac_sha1(key, message):
    # Create a new HMAC object using SHA-1
    hmac_object = hmac.new(key.encode(), message.encode(), hashlib.sha1)
    # Return the hexadecimal representation of the HMAC
    return hmac_object.hexdigest()

# Example usage
if __name__ == "__main__":
    key = "secret_key"
    message = "Hello, World!"
    
    hmac_tag = hmac_sha1(key, message)
    print("HMAC-SHA1 Tag:", hmac_tag)


```

# output 

```
HMAC-SHA1 Tag: 3157fbd8e785592b16c4f87ac8bfd65d804ecd67
```






