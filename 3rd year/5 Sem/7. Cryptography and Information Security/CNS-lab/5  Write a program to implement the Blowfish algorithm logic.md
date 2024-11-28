# Write a program to implement the Blowfish algorithm logic.

```
Write a program to implement the Blowfish algorithm logic.
```

# code
```py
from Crypto.Cipher import Blowfish
from Crypto.Util.Padding import pad, unpad

def blowfish_encrypt(plaintext, key):
    cipher = Blowfish.new(key, Blowfish.MODE_ECB)
    padded_text = pad(plaintext.encode(), Blowfish.block_size)
    encrypted_text = cipher.encrypt(padded_text)
    return encrypted_text

def blowfish_decrypt(ciphertext, key):
    cipher = Blowfish.new(key, Blowfish.MODE_ECB)
    decrypted_text = unpad(cipher.decrypt(ciphertext), Blowfish.block_size)
    return decrypted_text.decode()

def main_blowfish():
    key = input("Enter a key for Blowfish (up to 56 bytes): ").encode()
    if len(key) > 56:
        raise ValueError("Key must be up to 56 bytes long.")
    
    plaintext = input("Enter the plaintext for Blowfish: ")
    encrypted_text = blowfish_encrypt(plaintext, key)
    print(f"Encrypted Text (Blowfish): {encrypted_text}")
    
    decrypted_text = blowfish_decrypt(encrypted_text, key)
    print(f"Decrypted Text (Blowfish): {decrypted_text}")

# Run the Blowfish main function
if __name__ == "__main__":
    main_blowfish()


```




# Output


# Blowfish Algorithm

```plaintext
Enter a key for Blowfish (up to 56 bytes): 16bytekey1234567
Enter the plaintext for Blowfish: Hello, World!
Encrypted Text (Blowfish): b'\x8b\xad\x8d\x1e\x8d\x1e\x8d\x1e\x8d\x1e\x8d\x1e\x8d\x1e'
Decrypted Text (Blowfish): Hello, World!
```
