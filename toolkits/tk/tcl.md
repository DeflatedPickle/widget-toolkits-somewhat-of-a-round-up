# Tcl

## Demo Application

{% code-tabs %}
{% code-tabs-item title="tkdemo.tcl" %}
```text
package require Tk

# Edit the window (it's created by default)
wm title . "Demo"
wm geometry . 300x150

set channels [list "python" "ruby" "cpp"]

# Login function
proc login {} {
	variable user
	variable chan_
	variable channels

	if {$user == "" || $chan_ ni $channels} {
		puts "Invalid username or channel"
		return
	}

	puts "Logged in to $chan_ as $user!"
}

# Check password function
proc check_password {} {
	variable pass
	variable strength

	set add 0

	foreach i {$pass} {
		incr add 4
	}

	# .frame.user_label configure -text $add
	set strength $add
}

# Show password function
proc show_pass {} {
	variable is_pass

	if {$is_pass} {
		.frame.pass_entry configure -show ""
	} else {
		.frame.pass_entry configure -show "*"
	}
}

# Make the frame
pack [ttk::frame .frame] -expand true

# Make the username label and entry
grid [ttk::label .frame.user_label -text "Username:"] -row 0 -column 0 -sticky w
set user ""
grid [ttk::entry .frame.user_entry -textvariable user] -row 0 -column 1 -columnspan 2 -padx 3 -pady 1

# Make the password label and entry
grid [ttk::label .frame.pass_label -text "Password:"] -row 1 -column 0 -sticky w
set pass ""
grid [ttk::entry .frame.pass_entry -textvariable pass -show "*"] -row 1 -column 1 -columnspan 2 -padx 3 -pady 1
bind .frame.pass_entry <KeyRelease> check_password

# Make show password checkbutton
set is_pass false
grid [ttk::checkbutton .frame.pass_check -text "Show password" -variable is_pass -command show_pass] -row 2 -column 0 -columnspan 2 -sticky w
# Make strength progressbar
grid [ttk::progressbar .frame.pass_strength -variable strength] -row 2 -column 2 -sticky we

# Add a separator
grid [ttk::separator .frame.separator] -row 3 -column 0 -columnspan 3 -pady 3 -sticky we

# Make the channel label and entry
grid [ttk::label .frame.channel_label -text "Channel:"] -row 4 -column 0 -sticky w
set chan_ ""
grid [ttk::entry .frame.channel_entry -textvariable chan_] -row 4 -column 1 -columnspan 2 -padx 3 -pady 1

# Make remember me checkbutton
set is_remind false
grid [ttk::checkbutton .frame.remember -text "Remember me" -variable is_remind] -row 5 -column 0 -columnspan 2 -sticky w

# Make login button
grid [ttk::button .frame.login_button -text "Login" -default "active" -command login] -row 5 -column 2 -sticky e

# Create the main menu
menu .menu_

# Create the file menu
menu .menu_.file_
.menu_.file_ add command -label "Login"
.menu_.file_ add separator
.menu_.file_ add command -label "Exit"
.menu_ add cascade -label "File" -menu .menu_.file_

# Create the edit menu
menu .menu_.edit
.menu_.edit add command -label "Channels"
.menu_ add cascade -label "Edit" -menu .menu_.edit

# Configure the menu
. configure -menu .menu_

```
{% endcode-tabs-item %}
{% endcode-tabs %}

* [x] Login function
* [x] Check password function
* [x] Show pass function 
* [x] Username label and entry
* [x]  Password label and entry, entry bound to `check_password` function on key releases
* [x]  Show password checkbox, which runs the `show_pass` function
* [x]  Password strength progressbar \(bug - only updates once\)
* [x]  Separator
* [x]  Channel label and entry
* [x]  Remember me checkbox
* [x]  Login button, which triggers the `login` function
* [x]  File menu, consisting of commands for login and exit, separated by a separator
* [x]  Edit menu, consisting of a channels command that lists the channels, each on a new line

### Run Command

```text
wish tkdemo.tcl
```

## Ranking

### Pros

* Tk is implicitly imported
* The root window is implicitly created
* Widgets can be created and put on the grid in the same line

### Cons

* To use variables in procedures, you have to refer to them with the "`variable`" statement first
* Widgets have to be named

