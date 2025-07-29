# Alternative Estonian keyboard configuration by GKalmus 

This repository contains an alternative xkb symbols file eeKalmus for customizing keyboard layouts 
on Linux systems using the X Keyboard Extension (XKB). 

## Introduction

The X Keyboard Extension (XKB) is a powerful tool for configuring keyboard layouts on Linux 
systems. This repository provides an alternative symbols file that can be used to customize 
your keyboard layout beyond the default options provided by your distribution.

## Installation

To use the alternative symbols file eeKalmus eeKalmus, follow these steps:

1. Clone the repository:
```sh
git clone https://github.com/GKalmus/eeKalmus.git
cd eeKalmus
```

2. Copy the alternative symbols file into xkb's symbols directory:
```sh
sudo cp eeKalmus /usr/share/X11/xkb/symbols/
```

3. Set the eeKalmus symbols file into permanent keyboard layout:
```sh
sudo localectl --no-convert set-x11-keymap eeKalmus pc104 ,qwerty lv3:ralt_switch
```
>For hyprland setup, just set keyboard layout as eeKalmus. For example:
```
input {
    kb_layout = eeKalmus
    kb_variant =
    kb_model =
    kb_options =
    kb_rules =
    follow_mouse = 0
    sensitivity = 0 # -1.0 - 1.0, 0 means no modification.
    touchpad {
        natural_scroll = false
    }
}
```

## Usage

You can set the layout temporarily using the setxkbmap command. For example:
```sh
setxkbmap eeKalmus 
```

These are the remappings, all also apply when Shift-key is pressed with the combination:
```
Alt-gr + w = š

Alt-gr + a = {
Alt-gr + s = }
Alt-gr + d = [
Alt-gr + f = ]
Alt-gr + j = |
Alt-gr + k = <
Alt-gr + l = >
```

## Customization

If you want to further customize the symbols file, you can edit the symbols/eeKalmus file. 
The XKB symbols file uses a straightforward syntax for defining key mappings. Refer to the 
XKB documentation (https://www.x.org/wiki/XKB/) for more details on how to modify the file.

### Example Customization

To add a custom key mapping, you can edit the symbols file as follows:
```cpp
xkb_symbols "typeName" {
    include "filename(typeName)" 
    // These will replace the keys of "filename(typeName)". For example, "ee(nodeadkeys)"
    key <keycode> { [ key, Shift+key, alt-gr+key, Alt-gr+Shift+key ] };
    // For example, key <AC01>	{ [ a, A, braceleft, braceleft ] }; 
    // Add more custom mappings here
};
```

## Contributing

Contributions are welcome! If you have improvements or additional layouts to share, 
please open an issue or submit a pull request. 

## License

This project is licensed under the GPL-3.0 License. See the [LICENSE](LICENSE) file for more details.
