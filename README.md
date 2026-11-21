import base64

# Caesar Cipher Encryption
def caesar_encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            start = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - start + shift) % 26 + start)
        else:
            result += char
    return result

# Caesar Cipher Decryption
def caesar_decrypt(text, shift):
    return caesar_encrypt(text, -shift)

# Base64 Encryption
def base64_encrypt(text):
    return base64.b64encode(text.encode()).decode()

# Base64 Decryption
def base64_decrypt(text):
    return base64.b64decode(text, validate=True).decode()

# Main Program
while True:
    print("\n===== CRYPTOGRAPHY TOOL =====")
    print("1. Caesar Cipher Encryption")
    print("2. Caesar Cipher Decryption")
    print("3. Base64 Encoding")
    print("4. Base64 Decoding")
    print("5. Exit")

    choice = input("Enter your choice: ")

    try:
        if choice == "1":
            text = input("Enter your message: ")
            shift = int(input("Enter shift value: "))
            print("Encrypted Message:", caesar_encrypt(text, shift))

        elif choice == "2":
            text = input("Enter encrypted message: ")
            shift = int(input("Enter shift value: "))
            print("Decrypted Message:", caesar_decrypt(text, shift))

        elif choice == "3":
            text = input("Enter your message: ")
            print("Encoded Message:", base64_encrypt(text))

        elif choice == "4":
            text = input("Enter encoded message: ")
            print("Decoded Message:", base64_decrypt(text))

        elif choice == "5":
            print("Thank you for using Cryptography Tool!")
            break

        else:
            print("Invalid choice! Try again.")

    except (ValueError, UnicodeDecodeError):
        print("Invalid input! Please try again.")


