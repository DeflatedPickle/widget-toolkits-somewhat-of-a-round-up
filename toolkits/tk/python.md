# Python

## Demo Application

{% code-tabs %}
{% code-tabs-item title="tkdemo.py" %}
```python
# Import Tk
import tkinter as tk
from tkinter import ttk

# Create window
root = tk.Tk()
root.title("Demo")
root.geometry("300x150")

# Make channels
channels = ["python", "ruby", "cpp"]


# Login function
def login(event=None):
    if user.get() == "" or chan.get() not in channels:
        print("Invalid username or channel")
        return

    print(f"Logged in to {chan.get()} as {user.get()}!")
    root.destroy()


# Check password function
def check_password(event=None):
    add = 0

    for i in passw.get():
        add += 4

    strength.set(add)


# Show password function
def show_pass():
    if is_pass.get():
        pass_entry.configure(show="")

    else:
        pass_entry.configure(show="*")


# Make the frame
frame = ttk.Frame(root)

# Make the username label and entry
ttk.Label(frame, text="Username:").grid(row=0, column=0, sticky="w")
user = tk.StringVar()
ttk.Entry(frame, textvariable=user).grid(row=0, column=1, columnspan=2, padx=3, pady=1)

# Make the password label and entry
ttk.Label(frame, text="Password:").grid(row=1, column=0, sticky="w")
passw = tk.StringVar()
pass_entry = ttk.Entry(frame, textvariable=passw, show="*")
pass_entry.grid(row=1, column=1, columnspan=2, padx=3, pady=1)
pass_entry.bind("<KeyRelease>", check_password)

# Make show password checkbutton
is_pass = tk.BooleanVar()
ttk.Checkbutton(frame, text="Show password", variable=is_pass, command=show_pass).grid(row=2, column=0, columnspan=2, sticky="w")
# Make strength progressbar
strength = tk.IntVar()
ttk.Progressbar(frame, variable=strength).grid(row=2, column=2, sticky="we")

# Add a separator
ttk.Separator(frame).grid(row=3, column=0, columnspan=3, pady=3, sticky="we")

# Make the channel label and entry
ttk.Label(frame, text="Channel:").grid(row=4, column=0, sticky="w")
chan = tk.StringVar()
ttk.Entry(frame, textvariable=chan).grid(row=4, column=1, columnspan=2, padx=3, pady=1)

# Make remember me checkbutton
is_remind = tk.BooleanVar()
ttk.Checkbutton(frame, text="Remember me", variable=is_remind).grid(row=5, column=0, columnspan=2, sticky="w")

# Make login button
log = ttk.Button(frame, text="Login", default="active", command=login).grid(row=5, column=2, sticky="e")
root.bind("<Return>", login)

# Pack the frame
frame.pack(expand=True)

# Create the main menu
menu = tk.Menu()

# Create the file menu
file = tk.Menu(menu)
file.add_command(label="Login")
file.add_separator()
file.add_command(label="Exit")
menu.add_cascade(label="File", menu=file)

# Create the edit menu
edit = tk.Menu(menu)
edit.add_command(label="Channels", command=lambda: print([i for i in channels]))
menu.add_cascade(label="Edit", menu=edit)

# Configure the menu
root.configure(menu=menu)

# Keep the menu open
root.mainloop()

```
{% endcode-tabs-item %}
{% endcode-tabs %}

* [x] Login function
* [x] Check password function
* [x] Show pass function 
* [x] Username label and entry
* [x]  Password label and entry, entry bound to `check_password` function on key releases
* [x]  Show password checkbox, which runs the `show_pass` function
* [x]  Password strength progressbar
* [x]  Separator
* [x]  Channel label and entry
* [x]  Remember me checkbox
* [x]  Login button, which triggers the `login` function
* [x]  File menu, consisting of commands for login and exit, separated by a separator
* [x]  Edit menu, consisting of a channels command that lists the channels, each on a new line

### Run Command

```text
python tkdemo.py
```

## Ranking

### Pros

* Comes with Python
* Widgets don't have to be named

### Cons

* Widgets assigned to variables and put on the grid in the same line, are none type
* Widget variables have to be created as instances of Var \(StringVar, IntVar, etc\) classes from the package
* Many parts of Tkinter changed from Python 2 to Python 3

