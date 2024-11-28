# Write a program to perform  encryption and decryption using the following algorithms
### a. Ccascr Cipher 
### b. Substitution Cipher 
### c. Hill Cipher
```
Write a program to perform  encryption and decryption using the following algorithms
a. Ccascr Cipher 
b. Substitution Cipher 
c. Hill Cipher
```

#  code
```py
import string
import numpy as np

# === Caesar Cipher ===
def caesar_encrypt(plaintext, shift):
    return ''.join(
        chr((ord(char) - (65 if char.isupper() else 97) + shift) % 26 + (65 if char.isupper() else 97)) if char.isalpha() else char
        for char in plaintext
    )

def caesar_decrypt(ciphertext, shift):
    return caesar_encrypt(ciphertext, -shift)

# === Substitution Cipher ===
def substitution_encrypt(plaintext, key):
    if len(key) != 26 or len(set(key)) != 26:
        raise ValueError("Key must be a 26-letter string with unique characters.")
    
    key_dict = {char: key[i] for i, char in enumerate(string.ascii_lowercase)}
    return ''.join(
        key_dict[char.lower()].upper() if char.isupper() else key_dict[char.lower()] if char.isalpha() else char
        for char in plaintext
    )

def substitution_decrypt(ciphertext, key):
    if len(key) != 26 or len(set(key)) != 26:
        raise ValueError("Key must be a 26-letter string with unique characters.")
    
    key_dict = {key[i]: char for i, char in enumerate(string.ascii_lowercase)}
    return ''.join(
        key_dict[char.lower()].upper() if char.isupper() else key_dict[char.lower()] if char.isalpha() else char
        for char in ciphertext
    )

# === Hill Cipher ===
def create_matrix(key):
    if len(key) != 4:
        raise ValueError("Key must be a string of 4 characters.")
    return np.array([[ord(char) % 65 for char in key[i:i+2]] for i in range(0, len(key), 2)])

def mod_inverse(matrix, mod=26):
    det = int(np.linalg.det(matrix)) % mod
    det_inv = pow(det, -1, mod)
    return (np.linalg.inv(matrix) * det_inv) % mod

def hill_encrypt(plaintext, key):
    key_matrix = create_matrix(key)
    plaintext = [ord(char) - 65 for char in plaintext]
    if len(plaintext) % 2 != 0:
        plaintext.append(ord('X') - 65)
    plaintext_matrix = np.array(plaintext).reshape(-1, 2)
    encrypted_matrix = np.dot(plaintext_matrix, key_matrix) % 26
    return ''.join(chr(int(num) + 65) for num in encrypted_matrix.flatten())

def hill_decrypt(ciphertext, key):
    key_matrix = create_matrix(key)
    key_matrix_inv = mod_inverse(key_matrix)
    ciphertext = [ord(char) - 65 for char in ciphertext]
    ciphertext_matrix = np.array(ciphertext).reshape(-1, 2)
    decrypted_matrix = np.dot(ciphertext_matrix, key_matrix_inv) % 26
    return ''.join(chr(int(num) + 65) for num in decrypted_matrix.flatten())

# === Main Function to Select Cipher ===
def main():
    print("Select Cipher Algorithm:")
    print("1. Caesar Cipher")
    print("2. Substitution Cipher")
    print("3. Hill Cipher")
    
    try:
        choice = int(input("Enter your choice (1/2/3): "))
        
        if choice == 1:
            plaintext = input("Enter the plaintext: ")
            shift = int(input("Enter the shift value: "))
            encrypted_text = caesar_encrypt(plaintext, shift)
            print(f"Encrypted Text: {encrypted_text}")
            decrypted_text = caesar_decrypt(encrypted_text, shift)
            print(f"Decrypted Text: {decrypted_text}")
            
        elif choice == 2:
            plaintext = input("Enter the plaintext: ")
            key = input("Enter the substitution key (26-letter string): ")
            encrypted_text = substitution_encrypt(plaintext, key)
            print(f"Encrypted Text: {encrypted_text}")
            decrypted_text = substitution_decrypt(encrypted_text, key)
            print(f"Decrypted Text: {decrypted_text}")
            
        elif choice == 3:
            plaintext = input("Enter the plaintext: ")
            key = input("Enter the key (a string of 4 characters): ")
            encrypted_text = hill_encrypt(plaintext, key)
            print(f"Encrypted Text: {encrypted_text}")
            decrypted_text = hill_decrypt(encrypted_text, key)
            print(f"Decrypted Text: {decrypted_text}")
            
        else:
            print("Invalid choice. Please select a valid option.")
    except ValueError as e:
        print(f"Error: {e}")

# Run the main function
if __name__ == "__main__":
    main()


 ```

# Output 

 

```plaintext
Select Cipher Algorithm:
1. Caesar Cipher
2. Substitution Cipher
3. Hill Cipher
Enter your choice (1/2/3): 1
Enter the plaintext: HELLO
Enter the shift value: 3
Encrypted Text: KHOOR
Decrypted Text: HELLO
```

```plaintext
Select Cipher Algorithm:
1. Caesar Cipher
2. Substitution Cipher
3. Hill Cipher
Enter your choice (1/2/3): 2
Enter the plaintext: HELLO
Enter the substitution key (26-letter string): QWERTYUIOPLKJHGFDSAZXCVBNM
Encrypted Text: ITSSG
Decrypted Text: HELLO
```

```plaintext
Select Cipher Algorithm:
1. Caesar Cipher
2. Substitution Cipher
3. Hill Cipher
Enter your choice (1/2/3): 3
Enter the plaintext: HELLO
Enter the key (a string of 4 characters): GYBN
Encrypted Text: ILBDA
Decrypted Text: HELLO
```
 
