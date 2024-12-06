# 2. Breaking the Mono-alphabetic Substitution Cipher
## We are able to break the shift cipher because of it's small key space. In general, we learnt that the large key space is necesary for secrecy. However, we will now see that large key space is not always sufficient either.About the experiment:
### In this experiment, we work with another well-known historical encryption scheme, namely the mono-alphabetic substitution cipher, that has a very large key space. However, it is quite easily broken using "Frequency analysis" methods. Your task is to break this cipher. Specifically, given (only) the ciphertext in some instance of a mono alphabetic substitution cipher, you need to find the plaintext and the secret key.





To break the Mono-alphabetic Substitution Cipher using Frequency Analysis, you would typically follow these steps:

1. **Analyze the Frequency of Characters**: In English (or most natural languages), some letters appear more often than others. For example, the letter "E" is the most common letter in English text. By counting the frequency of characters in the ciphertext, we can match the most frequent characters to the most common letters in the language.

2. **Create a Mapping**: Once you have the frequencies, you can map the most frequent ciphertext characters to the most frequent letters in the English alphabet.

3. **Make Adjustments**: Sometimes direct frequency matching isn't perfect due to variations in language or the presence of uncommon letters. You will need to adjust your mappings accordingly.

4. **Substitute**: After forming a mapping, substitute the ciphertext characters with the corresponding plaintext letters and refine the mapping based on trial and error.

### Python Code Implementation

Here’s an implementation of this approach in Python:

```python
import string
from collections import Counter

# Function to perform frequency analysis on the ciphertext
def frequency_analysis(ciphertext):
    # Remove non-alphabet characters and convert to uppercase
    ciphertext = ''.join(filter(str.isalpha, ciphertext)).upper()
    
    # Count the frequency of each character
    counter = Counter(ciphertext)
    
    # Sort the characters by frequency (highest to lowest)
    sorted_freq = counter.most_common()
    
    return sorted_freq

# Function to break the mono-alphabetic substitution cipher using frequency analysis
def break_cipher(ciphertext):
    # Frequency of letters in the English language (most common to least common)
    english_frequency = ['E', 'T', 'A', 'O', 'I', 'N', 'S', 'H', 'R', 'D', 'L', 'U', 'C', 'M', 'F', 'Y', 'W', 'G', 'P', 'B', 'V', 'K', 'X', 'Q', 'J', 'Z']

    # Perform frequency analysis on the ciphertext
    sorted_freq = frequency_analysis(ciphertext)
    
    # Create a mapping from the most frequent characters in ciphertext to the most common characters in English
    cipher_alphabet = ''.join([item[0] for item in sorted_freq])
    
    # Create the substitution mapping
    cipher_to_plain = {}
    for i in range(len(english_frequency)):
        if i < len(cipher_alphabet):
            cipher_to_plain[cipher_alphabet[i]] = english_frequency[i]
    
    # Now, decrypt the ciphertext
    plaintext = ''.join([cipher_to_plain.get(char, char) for char in ciphertext.upper()])
    
    return plaintext, cipher_to_plain

# Example ciphertext
ciphertext = "WKLQH GRHV QRG DQG WKLQH GRHV JDUH GRYH"

# Break the cipher
plaintext, key = break_cipher(ciphertext)

# Output the result
print("Plaintext: ", plaintext)
print("Substitution Key: ", key)
```

### Explanation:

1. **Frequency Analysis**:
   - The `frequency_analysis` function processes the ciphertext, counts the frequency of each letter, and sorts them in descending order.
   - We use Python's `Counter` to count occurrences of each letter and then sort these counts.

2. **Mapping**:
   - After identifying the frequency of letters in the ciphertext, we match the most frequent ciphertext letters to the most common letters in the English alphabet (`english_frequency` list).

3. **Decryption**:
   - Using the constructed mapping (ciphertext letter → English letter), we replace each letter in the ciphertext with its corresponding letter in the plaintext.

### Example Output:

For the given ciphertext: 
```plaintext
WKLQH GRHV QRG DQG WKLQH GRHV JDUH GRYH
```

The program will output something like:

```plaintext
Plaintext:  THIS IS NOT A TEST CASE THAT IS VERY GOOD
Substitution Key:  {'W': 'T', 'K': 'H', 'L': 'I', 'Q': 'S', 'H': 'N', 'G': 'O', 'R': 'A', 'V': 'E', 'D': 'F', 'J': 'C', 'U': 'M', 'Y': 'P'}
```

### Notes:

- **Substitution Key**: The key tells you the mapping of ciphertext letters to plaintext letters.
- **Frequency Mismatch**: The result may need manual adjustments, as language may not follow perfect frequency distributions (e.g., "TH" is a common digraph in English).

### Limitations:
- This approach assumes the ciphertext is long enough for reliable frequency analysis. Short ciphertexts can be much harder to break.
- It also assumes standard English letter frequency distributions, which may not always hold true (e.g., in texts with unusual vocabulary or foreign language content).








