
```py
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
from Crypto.Random import get_random_bytes

def encrypt(plaintext, key):
    cipher = AES.new(key, AES.MODE_CBC)
    iv = cipher.iv
    ciphertext = cipher.encrypt(pad(plaintext.encode(), AES.block_size))
    return iv + ciphertext

def decrypt(ciphertext, key):
    iv = ciphertext[:AES.block_size]
    cipher = AES.new(key, AES.MODE_CBC, iv)
    plaintext = unpad(cipher.decrypt(ciphertext[AES.block_size:]), AES.block_size)
    return plaintext.decode()

# Example usage
key = get_random_bytes(16)  # AES-128
plaintext = "This is a secret message"
ciphertext = encrypt(plaintext, key)
print(f"Ciphertext: {ciphertext}")

decrypted_text = decrypt(ciphertext, key)
print(f"Decrypted text: {decrypted_text}")


```


# Output

```
Enter the ciphertext: gsv jfrxp yildm ulc qfnkh levi gsv ozab wlt
Estimated Key: gedplqnrfazyuishwxjvmocbkt
Decrypted Plaintext: aot sihrd lnecu mew figyp ebtn aot vkjx qez


```
