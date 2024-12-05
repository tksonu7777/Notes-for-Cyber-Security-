 # 1. Breaking the Shift Cipher
 

```python
def encrypt_shift_cipher(plaintext, key):
    """
    Encrypts a plaintext using a shift cipher with the given key.
    
    :param plaintext: The message to be encrypted (string)
    :param key: The shift key (integer)
    :return: The encrypted ciphertext (string)
    """
    ciphertext = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97  # For uppercase and lowercase letters
            encrypted_char = chr((ord(char) - shift + key) % 26 + shift)
            ciphertext += encrypted_char
        else:
            # Non-alphabet characters are added to ciphertext as-is
            ciphertext += char
    return ciphertext


def decrypt_shift_cipher(ciphertext, key):
    """
    Decrypts a ciphertext using a given shift cipher key.
    
    :param ciphertext: The encrypted message (string)
    :param key: The shift key (integer)
    :return: The decrypted plaintext (string)
    """
    plaintext = ""
    for char in ciphertext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97  # For uppercase and lowercase letters
            decrypted_char = chr((ord(char) - shift - key) % 26 + shift)
            plaintext += decrypted_char
        else:
            # Non-alphabet characters are added to plaintext as-is
            plaintext += char
    return plaintext


def break_shift_cipher(ciphertext, original_plaintext=None):
    """
    Breaks the shift cipher by trying all possible keys (0-25) and printing the result.
    
    :param ciphertext: The encrypted message (string)
    :param original_plaintext: The original plaintext to check against (string, optional)
    """
    print("\n--- Decryption Results ---")
    print(f"Ciphertext: {ciphertext}")
    print("\nPossible Plaintexts (using brute-force decryption):\n")
    
    # Flag to track if the correct decryption has been found
    found = False
    
    for key in range(26):
        plaintext = decrypt_shift_cipher(ciphertext, key)
        print(f"Key {key}: {plaintext}")
        
        # If correct decryption is found, print the "Found" message and continue printing all keys
        if original_plaintext and plaintext == original_plaintext and not found:
            print(f"Key {key}: {plaintext}  -------------------------> Found")
            found = True  # Mark that we found the correct decryption
    
    # If no match found after trying all keys, print the appropriate message
    if not found:
        print("\nBrute-force decryption complete. No exact match found.")


def main():
    # Taking user input for plaintext
    plaintext = input("Enter the plaintext: ")

    # Taking user input for the shift key to encrypt the plaintext
    key = int(input("Enter the shift key (integer between 0 and 25): "))
    
    # Encrypting the plaintext using the given key
    ciphertext = encrypt_shift_cipher(plaintext, key)
    print(f"\nEncrypted Ciphertext: {ciphertext}")
    
    # Now breaking the shift cipher (brute-forcing decryption)
    print("\nNow attempting to break the cipher...")
    break_shift_cipher(ciphertext, original_plaintext=plaintext)


if __name__ == "__main__":
    main()

```

# Output 
```
Enter the plaintext: Musraf khan
Enter the shift key (integer between 0 and 25): 3

Encrypted Ciphertext: Pxvudi nkdq

Now attempting to break the cipher...

--- Decryption Results ---
Ciphertext: Pxvudi nkdq

Possible Plaintexts (using brute-force decryption):

Key 0: Pxvudi nkdq
Key 1: Owutch mjcp
Key 2: Nvtsbg libo
Key 3: Musraf khan
Key 3: Musraf khan  -------------------------> Found
Key 4: Ltrqze jgzm
Key 5: Ksqpyd ifyl
Key 6: Jrpoxc hexk
Key 7: Iqonwb gdwj
Key 8: Hpnmva fcvi
Key 9: Gomluz ebuh
Key 10: Fnlkty datg
Key 11: Emkjsx czsf
Key 12: Dljirw byre
Key 13: Ckihqv axqd
Key 14: Bjhgpu zwpc
Key 15: Aigfot yvob
Key 16: Zhfens xuna
Key 17: Ygedmr wtmz
Key 18: Xfdclq vsly
Key 19: Wecbkp urkx
Key 20: Vdbajo tqjw
Key 21: Ucazin spiv
Key 22: Tbzyhm rohu
Key 23: Sayxgl qngt
Key 24: Rzxwfk pmfs
Key 25: Qywvej oler









```
