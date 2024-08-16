# Task-01-Encryption-decryption

def caesar_cipher(text, shift, mode='encrypt'):
    result = ""
    
    # Adjust the shift value for decryption
    if mode == 'decrypt':
        shift = -shift

    # Loop through each character in the text
    for char in text:
        if char.isalpha():  # Check if the character is a letter
            shift_base = 65 if char.isupper() else 97  # Determine ASCII base for uppercase/lowercase
            # Shift the character and wrap around using modulo
            result += chr((ord(char) - shift_base + shift) % 26 + shift_base)
        else:
            result += char  # Non-alphabet characters remain the same

    return result

def main():
    # Get user input for message, shift value, and mode
    mode = input("Do you want to encrypt or decrypt? (enter 'encrypt' or 'decrypt'): ").strip().lower()
    message = input("Enter your message: ")
    shift = int(input("Enter the shift value: "))

    # Perform encryption or decryption
    if mode in ['encrypt', 'decrypt']:
        result = caesar_cipher(message, shift, mode)
        print(f"The {mode}ed message is: {result}")
    else:
        print("Invalid mode selected. Please enter 'encrypt' or 'decrypt'.")

if __name__ == "__main__":
    main()
