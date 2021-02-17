# wayland-mouse-mapper

Updated for mx master using [this](https://wiki.archlinux.org/index.php/Talk:Logitech_MX_Master).

A small script for mapping mouse buttons to keystrokes on Wayland.

I made for myself to use my mouse extra buttons for useful stuff.
It's tested and works with Logitech MX Master 2S on Fedora 27 using Gnome,
and works it on my old Logitech Performance MX too.
It probably works on any Wayland and Any Logitech mouse (or any mouse if you edit mappings)
because no other method (xdotools, xbindkeys, etc.) seemed to work.

It works by reading from `libinput debug-events` and triggering key events using `evemu`
depending on the recognized button from the recognized device.

Feel free to make PRs to make it configurable or to add more mappings

## Buttons
These are just the default settings, you can customize them at the start of the mousemapper.sh script.

- Forward: Move to workspace above  (Super+Page up)
- Back: Move to workspace below  (Super+Page down)

## Prerequisites
The script depends on the following executables being available in your PATH:
- libinput
- evemu

to install those just run the following command (with root privileges):
```
sudo apt install evemu-tools libinput-tools
```

## Usage
Run the following command (with root privileges):
```
./mousemapper
```

## Installation (start at boot)
Run the following commands (with root privileges):
```
cp mousemapper /usr/bin/mousemapper
cp mousemapper.service /usr/lib/systemd/system/
systemctl enable mousemapper.service
```
