import tkinter as tk

root = tk.Tk()
root.title("Simple Calculator")
root.geometry("570x600+100+200")
root.resizable(False, False)
root.configure(bg="#17161b")

equation = ""

def show(value):
    global equation
    equation += value
    label_result.config(text=equation)

def clear():
    global equation
    equation = ""
    label_result.config(text=equation)

def calculate():
    global equation
    result = ""
    if equation != "":
        try:
            result = eval(equation)
            if result == float('inf') or result == float('-inf'):
                result = "Error: Division by zero"
        except Exception as e:
            result = "Error"
        equation = str(result)
    label_result.config(text=result)

label_result = tk.Label(root, width=25, height=2, text="", font=("Arial", 30))
label_result.pack()

Buttons = [
    (root, "C", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#3697f5", lambda: clear(), 10, 100),
    (root, "/", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("/"), 150, 100),
    (root, "%", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("%"), 290, 100),
    (root, "", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show(""), 430, 100),

    (root, "7", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("7"), 10, 200),
    (root, "8", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("8"), 150, 200),
    (root, "9", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("9"), 290, 200),
    (root, "-", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("-"), 430, 200),

    (root, "4", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("4"), 10, 300),
    (root, "5", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("5"), 150, 300),
    (root, "6", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("6"), 290, 300),
    (root, "+", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("+"), 430, 300),

    (root, "1", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("1"), 10, 400),
    (root, "2", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("2"), 150, 400),
    (root, "3", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("3"), 290, 400),
    (root, "0", 11, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("0"), 10, 500),

    (root, ".", 5, 1, ("arial", 30, "bold"), 1, "#fff", "#2a2d36", lambda: show("."), 290, 500),
    (root, "=", 5, 3, ("arial", 30, "bold"), 1, "#fff", "#fe9037", lambda: calculate(), 430, 400)
]

for (root, text, width, height, font, bd, fg, bg, command, x, y) in Buttons:
    btn = tk.Button(root, text=text, width=width, height=height, font=font, bd=bd,
                    fg=fg, bg=bg, command=command)
    btn.place(x=x, y=y)

root.mainloop()

