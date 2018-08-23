# Perl 5

## Demo Application

{% hint style="info" %}
The original way works, but it's far better to use the object method. I didn't realize this until I had written out the original method, I thought I'd include it to help showcase.
{% endhint %}

{% tabs %}
{% tab title="Original" %}
{% code-tabs %}
{% code-tabs-item title="tkdemo.pl" %}
```perl
use strict;

use Tkx;

# Create window
Tkx::wm_title(".", "Demo");
Tkx::wm_geometry(".", "300x150");

# Make channels
my @channels = ("python", "ruby", "cpp");

# Make the frame
Tkx::pack(Tkx::ttk__frame(".frame"), -expand => 1);

# Make the username label and entry
Tkx::grid(Tkx::ttk__label(".frame.user_label", -text => "Username:"), -row => 0, -column => 0, -sticky => "w");
my $user;
Tkx::grid(Tkx::ttk__entry(".frame.user_entry", -textvariable => \$user), -row => 0, -column => 1, -columnspan => 2, -padx => 3, -pady => 1);

# Make the password label and entry
Tkx::grid(Tkx::ttk__label(".frame.pass_label", -text => "Password:"), -row => 1, -column => 0, -sticky => "w");
my $pass;
Tkx::grid(Tkx::ttk__entry(".frame.pass_entry", -textvariable => \$pass, -show => "*"), -row => 1, -column => 1, -columnspan => 2, -padx => 3, -pady => 1);
Tkx::bind(".frame.pass_entry", "<KeyRelease>", sub {check_password();});

# Make show password checkbutton
my $is_pass;
Tkx::grid(Tkx::ttk__checkbutton(".frame.pass_check", -text => "Show password", -variable => $is_pass, -command => sub {show_pass();}), -row => 2, -column => 0, -columnspan => 2, -sticky => "w");
# Make strength progressbar
my $strength;
Tkx::grid(Tkx::ttk__progressbar(".frame.strength", -variable => \$strength), -row => 2, -column => 2, -sticky => "we");

# Add a separator
Tkx::grid(Tkx::ttk__separator(".frame.separator"), -row => 3, -column => 0, -columnspan => 3, -pady => 3, -sticky => "we");

# Make the channel label and entry
Tkx::grid(Tkx::ttk__label(".frame.channel_label", -text => "Channel:"), -row => 4, -column => 0, -sticky => "w");
my $chan;
Tkx::grid(Tkx::ttk__entry(".frame.channel_entry", -textvariable => \$chan), -row => 4, -column => 1, -columnspan => 2, -padx => 3, -pady => 1);

# Make remember me checkbutton
my $is_remind;
Tkx::grid(Tkx::ttk__checkbutton(".frame.remember", -text => "Remember me", -variable => \$is_remind), -row => 5, -column => 0, -columnspan => 2, -sticky => "w");

# Make login button
Tkx::grid(Tkx::ttk__button(".frame.login_button", -text => "Login", -default => "active", -command => sub {login();}), -row => 5, -column => 2, -sticky => "e");
Tkx::bind(".frame.login_button", "<Return>", sub {login();});

# Login function
sub login {
	if ($user == "" || $chan ~~ @channels) {
		print "Invalid username or channel";
		return;
	}

	print "Logged into $chan as $user!";
}

# Check password function
sub check_password {
	my $add = 0;

	foreach my $i (split(//, $pass)) {
		$add += 4;
	}

	$strength = $add;
}

# Show password function
sub show_pass {
	if ($is_pass) {
		# Can't configure, need to use objects
	} else {
		# Can't configure, need to use objects
	}
}

Tkx::MainLoop;

```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}

{% tab title="Using Objects" %}
{% code-tabs %}
{% code-tabs-item title="tkdemo.pl" %}
```perl
use strict;

use Tkx;

# Create window
my $root = Tkx::widget->new(".");
$root->g_wm_title("Demo");
$root->g_wm_geometry("300x150");

# Make channels
my @channels = ("python", "ruby", "cpp");

# Make the frame
my $frame = $root->new_ttk__frame;
$frame->g_pack(-expand => 1);

# Make the username label and entry
$frame->new_ttk__label(-text => "Username:")->g_grid(-row => 0, -column => 0, -sticky => "w");
my $user;
$frame->new_ttk__entry(-textvariable => \$user)->g_grid(-row => 0, -column => 1, -columnspan => 2, -padx => 3, -pady => 1);

# Make the password label and entry
$frame->new_ttk__label(-text => "Password:")->g_grid(-row => 1, -column => 0, -sticky => "w");
my $pass;
my $pass_entry = $frame->new_ttk__entry(-textvariable => \$pass, -show => "*");
$pass_entry->g_grid(-row => 1, -column => 1, -columnspan => 2, -padx => 3, -pady => 1);
$pass_entry->g_bind("<KeyRelease>", sub {check_password();});

# Make show password checkbutton
my $is_pass;
$frame->new_ttk__checkbutton(-text => "Show password", -variable => \$is_pass, -command => sub {show_pass();})->g_grid(-row => 2, -column => 0, -columnspan => 2, -sticky => "w");
# Make strength progressbar
my $strength;
$frame->new_ttk__progressbar(-variable => \$strength)->g_grid(-row => 2, -column => 2, -sticky => "we");

# Add a separator
$frame->new_ttk__separator()->g_grid(-row => 3, -column => 0, -columnspan => 3, -pady => 3, -sticky => "we");

# Make the channel label and entry
$frame->new_ttk__label(-text => "Channel:")->g_grid(-row => 4, -column => 0, -sticky => "w");
my $chan;
$frame->new_ttk__entry(-textvariable => \$chan)->g_grid(-row => 4, -column => 1, -columnspan => 2, -padx => 3, -pady => 1);

# Make remember me checkbutton
my $is_remind;
$frame->new_ttk__checkbutton(-text => "Remember me", -variable => \$is_remind)->g_grid(-row => 5, -column => 0, -columnspan => 2, -sticky => "w");

# Make login button
my $login_button = $frame->new_ttk__button(-text => "Login", -default => "active");
$login_button->g_grid(-row => 5, -column => 2, -sticky => "e");
$login_button->g_bind("<Return>", sub {login();});

# Login function
sub login {
	if ($user == "" || $chan ~~ @channels) {
		print "Invalid username or channel";
		return;
	}

	print "Logged into $chan as $user!";
}

# Check password function
sub check_password {
	my $add = 0;

	foreach my $i (split(//, $pass)) {
		$add += 4;
	}

	$strength = $add;
}

# Show password function
sub show_pass {
	if ($is_pass) {
		$pass_entry->m_configure(-show => "");
	} else {
		$pass_entry->m_configure(-show => "*");
	}
}

# Keep the menu open
Tkx::MainLoop;

```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}
{% endtabs %}

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
* [ ]  File menu, consisting of commands for login and exit, separated by a separator
* [ ]  Edit menu, consisting of a channels command that lists the channels, each on a new line

### Run Command

```text
perl tkdemo.pl
```

## Ranking

### Pros

* Comes with ActivePerl
* Widget functions work in an OOP sense \(if using objects\)

### Cons

* Messy function names \(if not using objects\)
* Widgets assigned to variables and put in the grid in the same line are none types \(if using objects\)

