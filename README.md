# Password_Locker
The project is a GUI application using Tkinter in Python for text encryption and decryption. It allows the user to enter text, a secret key, and perform encryption or decryption based on the entered password. The encryption uses base64 encoding and decoding for securing the text.


Features/Characteristics:
Encryption and Decryption:
The application provides two main functionalities: encryption and decryption.
Encryption involves taking the user-entered text, encoding it in ASCII, performing base64 encoding, and displaying the result.
Decryption reverses the process by taking the encoded message, decoding base64, and then decoding ASCII to retrieve the original text.
Password Protection:
The user must enter a password (currently set as "1234") to access both encryption and decryption features.
Incorrect password attempts are handled with appropriate error messages.
GUI Elements:
The GUI consists of a main screen with text entry, password input, and buttons for encryption, decryption, and reset.
Separate Toplevel windows are created for encryption and decryption results.

