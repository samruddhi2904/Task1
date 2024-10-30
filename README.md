# Task1
def caesar_cipher(text, shift, mode):
    result = ""

    # Adjust the shift for decryption
    if mode == "decrypt":
        shift = -shift

    # Loop through each character in the text
    for char in text:
        if char.isalpha():  # Check if the character is a letter
            # Handle uppercase letters
            if char.isupper():
                result += chr((ord(char) + shift - 65) % 26 + 65)
            # Handle lowercase letters
            else:
                result += chr((ord(char) + shift - 97) % 26 + 97)
        else:
            # Non-alphabetic characters remain unchanged
            result += char

    return result

# Main program loop
while True:
    print("\nOptions: \n1. Encrypt \n2. Decrypt \n3. Exit")
    mode = input("Choose an option (1 for encrypt, 2 for decrypt, 3 to exit): ").strip()

    if mode == "1":
        mode = "encrypt"
    elif mode == "2":
        mode = "decrypt"
    elif mode == "3":
        print("Exiting the program.")
        break
    else:
        print("Invalid option. Please choose 1, 2, or 3.")
        continue

    # Get user input for the message and shift value
    message = input("Enter the text: ")
    shift = int(input("Enter the shift value: "))

    # Perform the encryption or decryption
    result = caesar_cipher(message, shift, mode)
    print(f"Result: {result}")
