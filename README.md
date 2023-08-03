# Task-2---Calculator-
import tkinter as tk

def on_button_click(event):
    current_text = result_var.get()
    button_text = event.widget.cget("text")

    if button_text == "=":
        try:
            result = eval(current_text)
            result_var.set(result)
        except Exception as e:
            result_var.set("Error")
    elif button_text == "C":
        result_var.set("")
    else:
        result_var.set(current_text + button_text)

# Create the main application window
root = tk.Tk()
root.title("Simple Calculator")
root.geometry("300x400")

# Create the display area
result_var = tk.StringVar()
result_var.set("")
display = tk.Entry(root, textvariable=result_var, font="Arial 20", justify="right")
display.pack(fill=tk.BOTH, expand=True)

# Create buttons for the calculator
buttons = [
    ("7", "8", "9", "/"),
    ("4", "5", "6", "*"),
    ("1", "2", "3", "-"),
    ("C", "0", "=", "+")
]

for row in buttons:
    button_frame = tk.Frame(root)
    button_frame.pack(fill=tk.BOTH, expand=True)

    for button_text in row:
        button = tk.Button(button_frame, text=button_text, font="Arial 20", padx=20, pady=20)
        button.pack(side=tk.LEFT, fill=tk.BOTH, expand=True)
        button.bind("<Button-1>", on_button_click)

# Start the main event loop
root.mainloop()
