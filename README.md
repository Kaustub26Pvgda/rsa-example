# Python RSA: A Simple Implementation Demo

Assignment work done for the **CS1702** (Network Security) course of our 6th Semester.

## Table of Contents

- [Python RSA: A Simple Implementation](#python-rsa-a-simple-implementation)
  - [Table of Contents](#table-of-contents)
  - [Aim](#aim)
  - [Implementation](#implementation)
    - [Key Components](#key-components)
    - [Encryption Process](#encryption-process)
    - [Decryption Process](#decryption-process)
    - [Helper Functions](#helper-functions)
  - [Results and Output](#results-and-output)

## Aim

The primary goal of the assignment was to implement the RSA encryption algorithm in Python to understand its core principles and functionality. RSA is a widely used asymmetric encryption technique, relying on the mathematical difficulty of factoring large prime numbers. By implementing RSA, we gain deeper insight into public key cryptography, key generation, and modular arithmetic.

## Implementation

This implementation of RSA follows the standard principles of public-key cryptography. The code is organized to clearly demonstrate each step involved in generating keys, encrypting messages, and decrypting ciphertexts.

### Key Components

1. **Prime Number Generation:** 
   - Large prime numbers are generated using the SymPy library's `randprime()` function within a specified bit size (default: 512 bits).
   
2. **Key Generation:**
   - Two distinct primes (p and q) are generated.
   - The modulus `n = p * q` and Euler’s totient `φ(n) = (p-1)*(q-1)` are calculated.
   - A public exponent `e` is chosen (commonly 65537 for security and efficiency).
   - The private exponent `d` is computed as the modular inverse of `e` modulo `φ(n)`.

3. **Modular Arithmetic:**
   - Encryption and decryption rely on fast modular exponentiation to handle large integers efficiently.

4. **Encoding and Decoding:**
   - Plaintext messages are converted to integers before encryption and back to text after decryption using byte encoding and decoding.

### Encryption Process

The encryption process follows these steps:

1. **Message Preparation:**  
   - The plaintext message is encoded into an integer format.

2. **Ciphertext Generation:**  
   - The ciphertext `c` is computed using modular exponentiation:  
     \[`c = m^e % n`\]
   where `m` is the plaintext integer, `e` is the public exponent, and `n` is the modulus.

### Decryption Process

The decryption process reverses the encryption:

1. **Ciphertext Decryption:**  
   - The original message integer `m` is recovered using:  
     \[`m = c^d % n`\]
   where `d` is the private exponent.

2. **Message Recovery:**  
   - The decrypted integer is converted back to the original plaintext string.

### Helper Functions

- `generate_prime(bits)`: Generates a random prime number of specified bit length.
- `mod_inverse(e, phi)`: Computes the modular inverse using Python's built-in modular inverse function.
- `generate_keys(bits)`: Orchestrates the full key generation process and returns public and private keys.
- `encrypt(message, public_key)`: Encrypts a plaintext string using the provided public key.
- `decrypt(ciphertext, private_key)`: Decrypts a ciphertext integer using the private key.

Additionally, colored output is used to improve readability when displaying the generated keys, ciphertext, and decrypted message.

## Results and Output

The implementation successfully encrypts and decrypts messages using RSA. Testing with sample plaintext inputs verified that the decryption process accurately recovers the original message, ensuring the correctness of the encryption-decryption cycle.

![Output Image](Output%20Image.png)
