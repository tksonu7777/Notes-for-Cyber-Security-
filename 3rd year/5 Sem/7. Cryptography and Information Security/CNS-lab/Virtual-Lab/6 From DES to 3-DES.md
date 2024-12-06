# 6 From DES to 3-DES
### In this experiment, you are asked to design the triple DES cryptosystem provided that you are given an implementation of DES.




# code 

```py
from Crypto.Cipher import DES
from Crypto.Random import get_random_bytes

def des_encrypt_decrypt(data, key, mode):
    """Encrypt or decrypt data using DES with the given key."""
    cipher = DES.new(key, DES.MODE_ECB)
    return cipher.encrypt(data) if mode == 'encrypt' else cipher.decrypt(data)

def triple_des(plaintext, key1, key2):
    """Triple DES Encrypt/Decrypt."""
    padded_data = plaintext + b'\x00' * (8 - len(plaintext) % 8)  # Padding
    # EDE (Encrypt-Decrypt-Encrypt)
    return des_encrypt_decrypt(des_encrypt_decrypt(des_encrypt_decrypt(padded_data, key1, 'encrypt'), key2, 'decrypt'), key1, 'encrypt')

# Example usage
key1, key2 = get_random_bytes(8), get_random_bytes(8)  # Random 8-byte keys for DES
plaintext = b"Hello123"  # 8-byte message

ciphertext = triple_des(plaintext, key1, key2)
decrypted_text = des_encrypt_decrypt(des_encrypt_decrypt(des_encrypt_decrypt(ciphertext, key1, 'decrypt'), key2, 'encrypt'), key1, 'decrypt')
print("Ciphertext:", ciphertext.hex())
print("Decrypted text:", decrypted_text.rstrip(b'\x00').decode())  # Remove padding



```




# output 


```
Ciphertext: 2b5ac5077d8f1c043eb9e7390c1d74a9
Decrypted text: Hello123

``
