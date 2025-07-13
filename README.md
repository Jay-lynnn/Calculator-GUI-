from tkinter import *
window = Tk()
window.title ("First ever GUI cause i gave up on the first one")
window.geometry("300x500")

def create_screen():
    global screen
    screen = Entry(window, width=23, font=("Arial", 16))
    screen.grid(row=1, column=0, columnspan=6, padx=5, pady=10)

def number(num):
    current = screen.get()
    screen.delete(0, END)
    screen.insert(0, current + num)

def calculate():
    try:
        result=eval(screen.get())
        screen.delete(0, END)
        screen.insert(0, str(result))
    except:
        screen.delete(0, END)
        screen.insert(0, "Error ki Bos <3")

def delete():
    screen.delete(0, END)

def backspace():
    current=screen.get()
    screen.delete(0, END)
    screen.insert(0, current[:-1])

Button_frame= Frame(window)
Button_frame.grid(row=3, column=0)

Frame_Features= Frame(window)
Frame_Features.grid(row=2, column=0)

Button_action= Frame(window)
Button_action.grid(row=3, column=1)

Button(Button_action, text="+", command=lambda: number("+"), width=2, height=2).grid(row=3, column=3, columnspan=2)
Button(Button_action, text="-", command=lambda: number("-"), width=2, height=2).grid(row=4, column=3, columnspan=2)
Button(Button_action, text="x", command=lambda: number("*"), width=2, height=2).grid(row=5, column=3, columnspan=2)
Button(Button_action, text="÷", command=lambda: number("/"), width=2, height=2).grid(row=6, column=3, columnspan=2)
Button(Button_action, text="=", command=calculate, width=2, height=3).grid(row=7, column=3, columnspan=2)

Button(Frame_Features, text="AC", command=delete, width=3, height=1).grid(row=2, column=1)
Button(Frame_Features, text=".", command=lambda: number("."), width=3, height=1).grid(row=2, column=2)
Button(Frame_Features, text="⌫", command=backspace, width=3, height=1).grid(row=2, column=3)

Button(Button_frame, text="1", command=lambda: number("1"), width=3, height=1).grid(row=1, column=1, padx=4, pady=4)
Button(Button_frame, text="2", command=lambda: number("2"), width=3, height=1).grid(row=2, column=1, padx=0, pady=0)
Button(Button_frame, text="3", command=lambda: number("3"), width=3, height=1).grid(row=3, column=1, padx=4, pady=4)
Button(Button_frame, text="4", command=lambda: number("4"), width=3, height=1).grid(row=4, column=1, padx=0, pady=0)
Button(Button_frame, text="5", command=lambda: number("5"), width=3, height=1).grid(row=5, column=1, padx=4, pady=4)
Button(Button_frame, text="6", command=lambda: number("6"), width=3, height=1).grid(row=1, column=2, padx=0, pady=0)
Button(Button_frame, text="7", command=lambda: number("7"), width=3, height=1).grid(row=2, column=2, padx=4, pady=4)
Button(Button_frame, text="8", command=lambda: number("8"), width=3, height=1).grid(row=3, column=2, padx=0, pady=0)
Button(Button_frame, text="9", command=lambda: number("9"), width=3, height=1).grid(row=4, column=2, padx=4, pady=4)
Button(Button_frame, text="0", command=lambda: number("0"), width=3, height=1).grid(row=5, column=2, padx=0, pady=0)

button = Button(window, text="Start", command=create_screen)
button.grid(row=0, column=1, columnspan=2)

label = Label(window, text="Calculator")
label.grid(row=0, column=0)

window.mainloop()
