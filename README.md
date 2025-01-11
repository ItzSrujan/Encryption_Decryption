## Encryption and Decryption System

This project is a simple encryption and decryption system implemented in Python using the `cryptography` library. It allows users to securely encrypt a message and decrypt it using a generated key.

## Features
- **Encrypt Messages:** Securely encrypt a message using the `Fernet` symmetric encryption.
- **Decrypt Messages:** Decrypt the previously encrypted message using the same key.
- **Interactive Menu:** User-friendly interface with options to encrypt, decrypt, or exit the program.

## Prerequisites
Before running the program, ensure you have Python installed and the `cryptography` library installed. You can install it using pip:
```bash
pip install cryptography
```

## How to Use

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/encryption-decryption-system.git
   cd encryption-decryption-system
   ```

2. **Run the Program:**
   Execute the script using Python:
   ```bash
   python encryption_decryption.py
   ```

3. **Choose an Option:**
   - Press `1` to encrypt a message.
     - Enter the message to encrypt.
     - The program will display the original message, encrypted message, and the key to save for decryption.
   - Press `2` to decrypt a message.
     - Ensure the encrypted message and key are available from a previous encryption.
   - Press `3` to exit the program.

## Code Explanation

### Encrypt Function
The `encrypt` function generates a unique encryption key using `Fernet.generate_key()`. It encrypts the message using this key and prints the encrypted message and the key.

```python
def encrypt(message):
    key = Fernet.generate_key()
    fernet = Fernet(key)
    enc_msg = fernet.encrypt(message.encode())
    print(f"Original message: {message}")
    print(f"Encrypted message: {enc_msg}")
    print(f"Key (save this for decryption): {key}")
    return enc_msg, key
```

### Decrypt Function
The `decrypt` function decrypts the encrypted message using the saved key. The original message is printed after decryption.

```python
def decrypt(enc_msg, key):
    fernet = Fernet(key)
    dec_msg = fernet.decrypt(enc_msg).decode()
    print(f"Decrypted message: {dec_msg}")
```

### Menu System
The program includes a while-loop-based menu for user interaction. Users can choose to encrypt, decrypt, or exit the program.

## Example Usage

### Encryption:
```
Choose an option:
1. Encrypt a message
2. Decrypt a message
3. Exit
Enter your choice: 1
Enter the message to encrypt: Hello, World!
------------------------------------------------------------------
Original message: Hello, World!
Encrypted message: b'gAAAAABlYkP...'
Key (save this for decryption): b'GJk92hQo0w...'
------------------------------------------------------------------
```

### Decryption:
```
Choose an option:
1. Encrypt a message
2. Decrypt a message
3. Exit
Enter your choice: 2
------------------------------------------------------------------
Decrypted message: Hello, World!
------------------------------------------------------------------
```

## Notes
- Always save the encryption key generated during the encryption process. Without the key, decryption is not possible.
- This script only works for encryption and decryption during the same runtime. For production, consider saving encrypted messages and keys securely.
- 
## Contributing
Contributions are welcome! If you'd like to enhance the functionality or fix any issues, please open an issue or submit a pull request.


