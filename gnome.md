# Gnome

Gnome is a window manager written by Apple wannabes. Their main competitors, a group of Windows wannabes, develop KDE.

## Terminal

### Tab Visibility

When multiple tabs are open in Terminal, it's impossible to tell which one is selected. To remedy this, add the following entries to *~/.config/gtk-3.0/gtk.css*:

    TerminalWindow .notebook tab:active {
       background-color: #DDDDDD;
    }
    TerminalWindow .notebook tab {
       background-color: #888888;
    }

### Scrolling

Select the *Edit* menu, *Profile Preferences* menu option and *Scrolling* tab and check the *Unlimited* checkbox.
