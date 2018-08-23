# Introduction

This book is a personal round-up of different toolkits for different languages that I've found, tested and evaluated for others to use to find a good toolkit to use, rather than having to research a ton into each one, and in some cases, researching more into what distribution/wrapper to use for a toolkit.

For each toolkit and language, I will write a demo application for each implemented language, based on the image below, share the code and list the pros and cons of the toolkit. The different implementations will have their own page, with their own pros and cons. I will be ignoring any GUI builders the toolkit may have when making the demo, though I will list them in the feature set.

![The demo application \(implemented in Tk\)](.gitbook/assets/image%20%283%29.png)

The demo consists of:

* Login function, checks if the username is nothing, checks if the channel is in the channel list, if not, prints that it's invalid and returns, if so, prints that the user was logged in and destroys the window
* Check password function, creates an "add" variable, runs a for loop through each item in the password, adds 4 to the add variable for each item and then sets the strength variable to "add"
* Show pass function, if `is_pass` is true, configure the `pass_entry` to show characters, if not, configure the entry to show the password as asterisks
* Username label and entry
* Password label and entry, entry bound to `check_password` function on key releases
* Show password checkbox, which runs the `show_pass` function
* Password strength progressbar
* Separator
* Channel label and entry
* Remember me checkbox
* Login button, which triggers the `login` function
* File menu, consisting of commands for login and exit, separated by a separator
* Edit menu, consisting of a channels command that lists the channels, each on a new line

{% hint style="info" %}
Bold indicates the implementation language. Italic indicates that the toolkit or implementation have been finished. Strike-through indicates that the toolkit or implementation exist, but won't be written about
{% endhint %}

| **Toolkit** | **Languages** |
| :--- | :--- |
| [wxWidgets](https://en.wikipedia.org/wiki/WxWidgets) | **C++**, Python, Perl, Ruby, D |
| [Qt](https://en.wikipedia.org/wiki/Qt_%28software%29) | **C++**, Python, Ruby |
| [Tk](https://en.wikipedia.org/wiki/Tk_%28software%29) | **C**, _Tcl_, _Python_, [_Ruby_](https://github.com/ruby/tk), _Perl 5_, D, [C++](http://cpptk.sourceforge.net/), R, [PHP](http://php-tk.sourceforge.net/), Lua, Prolog, OCaml, Ada, Dylan, Erlang, FORTH, FORTRAN, Guile, Haskell, Java, Ksh, Lisp, Mercury, Mozart, Phantom, Rexx, Scheme, SNOBOL, Yorick |
| [FLTK](https://en.wikipedia.org/wiki/FLTK) | **C++**,  |
| [GTK+](https://en.wikipedia.org/wiki/GTK%2B) | **C**, C++, Rust,  |
| [Shoes](https://en.wikipedia.org/wiki/Shoes_%28GUI_toolkit%29) | **Ruby**,  |
| [JUICE](https://en.wikipedia.org/wiki/JUCE) | **C++**,  |
| [AWT](https://en.wikipedia.org/wiki/Abstract_Window_Toolkit) | **Java**,  |
| [Swing](https://en.wikipedia.org/wiki/Swing_%28Java%29) | **Java**,  |
| [SWT](https://en.wikipedia.org/wiki/Standard_Widget_Toolkit) | **Java**, D |
| [GWT](https://en.wikipedia.org/wiki/Google_Web_Toolkit) | **Java**,  |
| [FOX](https://en.wikipedia.org/wiki/Fox_toolkit) | **C++**,  |
| [LEGUI](https://github.com/LiquidEngine/legui) | **Java**,  |
| [FireMonkey](https://en.wikipedia.org/wiki/FireMonkey) | **Delphi**,  |
| [VLC](https://en.wikipedia.org/wiki/Visual_Component_Library) | **Object Pascal**,  |
| [MFC](https://en.wikipedia.org/wiki/Microsoft_Foundation_Class_Library) | **C++**,  |
| [XWT](https://github.com/mono/xwt) | **C\#**,  |
| [IUP](https://en.wikipedia.org/wiki/IUP_%28software%29) | **C++**,  |
| [CEGUI](https://en.wikipedia.org/wiki/CEGUI) | **C++**,  |
| [ImGUI](https://github.com/ocornut/imgui) | **C++**, Rust, D |

