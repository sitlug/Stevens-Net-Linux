# Stevens-Net-Linux
A guide to configuring Stevens-Net on Linux. TLDR: the script depends on one of gnome-shell or xwininfo as well as xdg-open, and NetworkManager. Install gnome, boot into it, and run from there.

_This guide isn't 100% tested, and is based mostly my and others' experience in setting this up. YMMV. If you're really, really stuck, you can go to the TRAC and they'll probably just let you connect to the IoT network_

## 1. Connect to Stevens-Connect
From here, there should be a sign-in page that looks something like this:

![image](https://user-images.githubusercontent.com/113066497/213235449-2eb2eb57-1188-4a99-861e-b5d442d0cbd6.png)


Download the script.

## Installing GNOME
The wifi script depends on gnome-shell, which should be a part of GNOME. Installation depends on what distributsion

__Debian/Ubuntu__
You're probably using GNOME already if you installed default Ubuntu, but if you installed Lubuntu or something of the sort, run `sudo apt install gnome-desktop gnome`

__Arch/Manjaro__
Run `sudo pacman -S gnome-desktop gnome-shell`

__TODO: Add more distros, verify functionality__

## Getting into GNOME
Depending on your current desktop environment, you may be able to reboot and select GNOME before logging in to log into a GNOME session (using either X11 or Wayland is fine). This is true for XFCE and KDE.

If this isn't the case, login, open a terminal, and run `sudo systemctl disable [Display Manager]` and then `sudo systemctl enable gdm.service`. If you don't know your desktop environment's display manager, you can type the second one, and you'll get an error, from which you can find the name of your display manager. For example:
```
$ sudo systemctl enable gdm
[sudo] password for <user>: 
Failed to enable unit: File /etc/systemd/system/display-manager.service already exists and is a symlink to /usr/lib/systemd/system/lightdm.service.
$ 
```
In this case, we'd disable `lightdm.service`.

Next, reboot, login, and our desktop should look very different from before.

## Running the script

Now, we can take our previously downloaded script and run it (TODO: insert instructions from TRAC on how to run). Sometimes, Stevens-Connect likes to not resolve the Okta login page the script pulls up, so if the script doesn't work on Stevens-Connect and you get some sort of 'page not found' or 'could not resolve url' error from firefox (or whatever web browser you're using), try to do this from a hotspot.

## If all else fails
At the moment, because everything about Stevens IT is dumb and broken, you can ask them for access to the IoT network.
