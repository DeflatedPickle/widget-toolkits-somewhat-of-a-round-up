# Ruby

## Demo Application

{% code-tabs %}
{% code-tabs-item title="tkdemo.rb" %}
```ruby
# Import Tk
require 'tk'
require 'tkextlib/tile'

# Create window
$root = TkRoot.new
$root.title = 'Demo'
$root.geometry = '300x150'

# Make channels
$channels = %w{python ruby cpp}

# Login function
def login
  if $user.to_s == "" or not $channels.include?($chan.to_s)
    puts('Invalid username or channel')
    return
  end

  puts("Logged into #{$chan} as #{$user}!")
  $root.destroy
end

# Check password function
def check_password
  add = 0

  $pass.to_s.split('').each {|_|
    add += 4
  }

  $strength.set_numeric(add)
end

# Show password function
def show_pass
  if $is_pass.bool
    $pass_entry.configure(:show => "")
  else
    $pass_entry.configure(:show => "*")
  end
end

# Make the frame
frame = Tk::Tile::Frame.new($root).pack(:expand => true)

# Make the username label and entry
Tk::Tile::Label.new(frame, :text => "Username:").grid(:row => 0, :column => 0, :sticky => "w")
$user = TkVariable.new
Tk::Tile::Entry.new(frame, :textvariable => $user).grid(:row => 0, :column => 1, :columnspan => 2, :padx => 3, :pady => 1)

# Make the password label and entry
Tk::Tile::Label.new(frame, :text => "Password:").grid(:row => 1, :column => 0, :sticky => "w")
$pass = TkVariable.new
$pass_entry = Tk::Tile::Entry.new(frame, :textvariable => $pass, :show => "*").grid(:row => 1, :column => 1, :columnspan => 2, :padx => 3, :pady => 1)
$pass_entry.bind('KeyRelease', proc {check_password})

# Make show password checkbutton
$is_pass = TkVariable.new
Tk::Tile::Checkbutton.new(frame, :text => "Show password", :variable => $is_pass, :command => proc {show_pass}).grid(:row => 2, :column => 0, :columnspan => 2, :sticky => "w")
# Make strength progressbar
$strength = TkVariable.new
Tk::Tile::Progressbar.new(frame, :variable => $strength).grid(:row => 2, :column => 2, :sticky => "we")

# Add a separator
Tk::Tile::Separator.new(frame).grid(:row => 3, :column => 0, :columnspan => 3, :pady => 3, :sticky => "we")

# Make the channel label and entry
Tk::Tile::Label.new(frame, :text => "Channel:").grid(:row => 4, :column => 0, :sticky => "w")
$chan = TkVariable.new
Tk::Tile::Entry.new(frame, :textvariable => $chan).grid(:row => 4, :column => 1, :columnspan => 2, :padx => 3, :pady => 1)

# Make remember me checkbutton
$is_remind = TkVariable.new
Tk::Tile::Checkbutton.new(frame, :text => "Remember me", :variable => $is_remind).grid(:row => 5, :column => 0, :columnspan => 2, :sticky => "w")

# Make login button
Tk::Tile::Button.new(frame, :text => "Login", :default => "active", :command => proc {login}).grid(:row => 5, :column => 2, :sticky => "e")
$root.bind('Return', proc {login})

# Create the main menu
menu = TkMenu.new($root)

# Create the file menu
file = TkMenu.new(menu)
file.add_command(:label => "Login")
file.add_separator
file.add_command(:label => "Exit")
menu.add_cascade(:label => "File", :menu => file)

# Create the edit menu
edit = TkMenu.new(menu)
edit.add_command(:label => "Channels")
menu.add_cascade(:label => "Edit", :menu => edit)

# Configure the menu
$root.configure(:menu => menu)

# Keep the menu open
Tk.mainloop
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
ruby tkdemo.rb
```

## Rankings

### Pros

* Widgets can be assigned to variables and put on the grid in the same line

### Cons

* 
