# **2. Breaking the Mono-alphabetic Substitution Cipher**

### We are able to break the shift cipher because of it's small key space. In general, we learnt that the large key space is necesary for secrecy. However, we will now see that large key space is not always sufficient either.

## **About the experiment**:

### In this experiment, we work with another well-known historical encryption scheme, namely the mono-alphabetic substitution cipher, that has a very large key space. However, it is quite easily broken using "Frequency analysis" methods. Your task is to break this cipher. Specifically, given (only) the ciphertext in some instance of a mono alphabetic substitution cipher, you need to find the plaintext and the secret key.





# Code 
```py
import string
from collections import Counter

# English letter frequencies (from https://en.wikipedia.org/wiki/Letter_frequency)
ENGLISH_FREQ = {
    'E': 12.702,
    'T': 9.056,
    'A': 8.167,
    'O': 7.507,
    'I': 6.966,
    'N': 6.749,
    'S': 6.327,
    'H': 6.094,
    'R': 5.987,
    'D': 4.253,
    'L': 4.025,
    'C': 2.782,
    'U': 2.758,
    'M': 2.406,
    'W': 2.309,
    'F': 2.247,
    'G': 2.015,
    'Y': 1.974,
    'P': 1.929,
    'B': 1.492,
    'V': 0.978,
    'K': 0.772,
    'J': 0.153,
    'X': 0.150,
    'Q': 0.095,
    'Z': 0.074
}

def calculate_frequencies(text):
    """Calculate the frequency of each letter in the given text."""
    text = text.upper()
    freq = Counter(text)
    total = sum(freq.values())
    return {char: count / total * 100 for char, count in freq.items() if char in string.ascii_uppercase}

def match_frequencies(freq1, freq2):
    """Match the frequencies of two texts."""
    matches = {}
    for char1, freq1_val in freq1.items():
        best_match = None
        best_diff = float('inf')
        for char2, freq2_val in freq2.items():
            diff = abs(freq1_val - freq2_val)
            if diff < best_diff:
                best_diff = diff
                best_match = char2
        matches[char1] = best_match
    return matches

def decrypt_monoalphabetic(ciphertext, key):
    """Decrypt the mono-alphabetic substitution cipher using the given key."""
    plaintext = ''
    for char in ciphertext:
        if char in string.ascii_uppercase:
            plaintext += key[char]
        else:
            plaintext += char
    return plaintext

def encrypt_monoalphabetic(plaintext, key):
    """Encrypt the mono-alphabetic substitution cipher using the given key."""
    ciphertext = ''
    for char in plaintext:
        if char in string.ascii_uppercase:
            for k, v in key.items():
                if v == char:
                    ciphertext += k
        else:
            ciphertext += char
    return ciphertext

def break_monoalphabetic(ciphertext):
    """Break the mono-alphabetic substitution cipher using frequency analysis."""
    ciphertext_freq = calculate_frequencies(ciphertext)
    key = match_frequencies(ciphertext_freq, ENGLISH_FREQ)
    plaintext = decrypt_monoalphabetic(ciphertext, key)
    return plaintext, key

# Example usage
plaintext = "THERE IS WORLD WITHOUT WORLD"
key = {}
for i in range(len(plaintext)):
    key[chr(ord('A') + i % 26)] = plaintext[i]
ciphertext = encrypt_monoalphabetic(plaintext, key)

print("Plaintext:", plaintext)
print("Key:", key)
print("Ciphertext:", ciphertext)

broken_plaintext, broken_key = break_monoalphabetic(ciphertext)
print("Broken Plaintext:", broken_plaintext)
print("Broken Key:", broken_key)


```

# Output
```
Plaintext: THERE IS WORLD WITHOUT WORLD
Key: {'T': 'T', 'H': 'H', 'E': 'E', 'R': 'R', 'I': 'I', 'S': 'S', 'W': 'W', 'O': 'O', 'L': 'L', 'D': 'D', 'N': 'N', 'U': 'U', 'B': 'B', 'Y': 'Y', 'A': 'A'}
Ciphertext: WKHUH LV ZRUOG ZLWKRXW ZRUOG
Broken Plaintext: THERE IS WORLD WITHOUT WORLD
Broken Key: {'W': 'T', 'K': 'H', 'H': 'E', 'U': 'R', 'L': 'I', 'V': 'S', 'Z': 'W', 'R': 'O', 'O': 'U', 'G': 'L', 'X': 'D', 'Q': 'N', 'J': 'F',

```
















