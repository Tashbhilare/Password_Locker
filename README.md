# Password_Locker
The project is a GUI application using Tkinter in Python for text encryption and decryption. It allows the user to enter text, a secret key, and perform encryption or decryption based on the entered password. The encryption uses base64 encoding and decoding for securing the text.


from tkinter import *
from tkinter import messagebox
import base64

def decrypt():
    password = code.get()

    if password == "1234":
        screen2 = Toplevel(screen)
        screen2.title("decryption")
        screen2.geometry("400x200")
        screen2.configure(bg="#00bd56")

        message = text1.get(1.0, END)
        base64_bytes = message.encode("ascii")
        decoded_bytes = base64.b64decode(base64_bytes)
        decrypt = decoded_bytes.decode("ascii")

        Label(screen2, text="Decrypted message: " + decrypt, font="arial", fg="white", bg="#00bd56").place(x=10, y=10)
        text2 = Text(screen2, font="Roboto", bg="white", relief=GROOVE, wrap=WORD, bd=0)
        text2.place(x=10, y=50, width=380, height=150)

        text2.insert(END, decrypt)

    elif password == "":
        messagebox.showerror("decryption", "Input Password")

    elif password != "1234":
        messagebox.showerror("decryption", "Wrong Password")

def encrypt():
    password = code.get()

    if password == "1234":
        screen1 = Toplevel(screen)
        screen1.title("encryption")
        screen1.geometry("400x200")
        screen1.configure(bg="#ed3833")

        message = text1.get(1.0, END)
        encode_message = message.encode("ascii")
        base64_bytes = base64.b64encode(encode_message)
        encrypt_message = base64_bytes.decode("ascii")

        Label(screen1, text="Encrypted message: " + encrypt_message, font="arial", fg="white", bg="#ed3833").place(x=10, y=10)
        text2 = Text(screen1, font="Roboto", bg="white", relief=GROOVE, wrap=WORD, bd=0)
        text2.place(x=10, y=50, width=380, height=150)

        text2.insert(END, encrypt_message)

    elif password == "":
        messagebox.showerror("encryption", "Input Password")

    elif password != "1234":
        messagebox.showerror("encryption", "Wrong Password")

def main_screen():
    global screen
    global code
    global text1

    screen = Tk()
    screen.geometry("375x375")

    def reset():
        code.set("")
        text1.delete("1.0", END)

    screen.title("Password Locker")

    Label(text="Enter text for encryption and decryption", fg="black", font=("calibri", 12)).place(x=10, y=10)
    text1 = Text(font="Roboto", bg="white", relief=GROOVE, wrap=WORD, bd=0)
    text1.place(x=10, y=50, width=355, height=100)

    Label(text="Enter secret key for encryption and decryption", fg="black", font=("calibri", 12)).place(x=10, y=170)

    code = StringVar()
    Entry(textvariable=code, width=19, bd=0, font=("arial", 25), show="*").place(x=10, y=200)

    Button(text="Encrypt", height="2", width=23, bg="#ed3833", fg="white", bd=0, highlightbackground="#ed3833", command=encrypt).place(x=10, y=250)
    Button(text="Decrypt", height="2", width=23, bg="#00bd56", fg="white", bd=0, highlightbackground="#00bd56", command=decrypt).place(x=275, y=250)
    Button(text="Reset", height="2", width=50, bg="aqua", fg="white", bd=0, highlightbackground="aqua", command=reset).place(x=10, y=300)

    screen.mainloop()

main_screen()
