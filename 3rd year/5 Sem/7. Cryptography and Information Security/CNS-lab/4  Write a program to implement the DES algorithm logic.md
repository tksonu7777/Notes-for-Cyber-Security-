# Write a program to implement the DES algorithm logic
```
Write a program to implement the DES algorithm logic
```

# code 
```py
!pip install pycryptodome
```


```py
from Crypto.Cipher import DES
from Crypto.Util.Padding import pad, unpad

def des_encrypt(plaintext, key):
    cipher = DES.new(key, DES.MODE_ECB)
    padded_text = pad(plaintext.encode(), DES.block_size)
    encrypted_text = cipher.encrypt(padded_text)
    return encrypted_text

def des_decrypt(ciphertext, key):
    cipher = DES.new(key, DES.MODE_ECB)
    decrypted_text = unpad(cipher.decrypt(ciphertext), DES.block_size)
    return decrypted_text.decode()

def main_des():
    key = input("Enter an 8-byte key for DES: ").encode()
    if len(key) != 8:
        raise ValueError("Key must be 8 bytes long.")
    
    plaintext = input("Enter the plaintext for DES: ")
    encrypted_text = des_encrypt(plaintext, key)
    print(f"Encrypted Text (DES): {encrypted_text}")
    
    decrypted_text = des_decrypt(encrypted_text, key)
    print(f"Decrypted Text (DES): {decrypted_text}")

# Run the DES main function
if __name__ == "__main__":
    main_des()
```
