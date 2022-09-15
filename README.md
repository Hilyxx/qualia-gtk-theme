<div align="center">

# dg GNOME Theme
**A Libadwaita + macOS + Yaru theme designed to provide a consistent experience on GNOME 42+**

*Other desktops should work, see [this section](#other-desktop-environments) for more information.*

![Screenshot of the dark theme](.github/images/dark.png)

![Screenshot of the light theme](.github/images/light.png)

**This repo contains a GTK3 theme, a configuration for Libadwaita, a Firefox theme, and a GNOME Shell theme. The Yaru icon, cursor, and sound themes are also included.**

# How to Install

</div>

## Installing Dependencies

- Arch based distros: `sudo pacman -S sassc git gnome-shell-extensions ninja meson`

- Debian based distros: `sudo apt install sassc git gnome-shell-extensions ninja-build meson`

- Fedora: `sudo dnf install sassc git gnome-shell-extension-user-theme ninja-build meson`

- openSUSE: `sudo zypper install sassc git gnome-shell-extension-user-theme ninja meson`

**If `gnome-shell-extensions` / `gnome-shell-extension-user-theme` wasn't already installed, log out and log back in before you proceed. If you aren't using GNOME or aren't going to install the GNOME Shell theme, you can skip installing it.**

## Downloading and Installing
Download the repository and run the install script with no options to configure and install the theme.

When configuring the theme you get to choose an [accent color](#available-accent-colors), choose between the light/dark variant, and choose which themes you want to install.
```
git clone https://github.com/dgmarie/dg-gnome-theme -b main && cd dg-gnome-theme
```
```
./install.sh
```
```
Usage: ./install.sh [OPTION]...

OPTIONS:
  -r, --reconfigure   Reconfigure the theme.
  -f, --force         Force reinstall the theme.
  -c, --clean         Clean build directories and exit.
  -v, --verbose       Show full meson output.
  -h, --help          Show this screen.

This script allows you to configure, install, and update the theme.
```

#### Available accent colors:
![Accent Colors](.github/images/accents.png)

### Important!
The themes won't automatically update if you change the light/dark theme preference in GNOME. You will either have to use `./install.sh --reconfigure` to switch between the light/dark themes, or if you set the theme to `auto` during configuration, just run `install.sh` and it will update the themes using the current light/dark preference in GNOME.

## Updating
The install script will handle updating the themes.

Your previous configuration will be used again unless you use the `--reconfigure` option.

Only the themes that have changes will be updated, if you want to reinstall all of the themes, use the `--force` option.
```
git pull
```
```
./install.sh
```

## Uninstalling
Before uninstalling, use GNOME Tweaks to change the themes to something else to avoid any issues. 

After doing that, run the uninstall script:
```
./uninstall.sh
```
```
Usage: ./uninstall.sh [OPTION]...

OPTIONS:
  -f, --firefox [standard|flatpak|snap]
        Uninstall dg-firefox-theme.
        Using no arguments will remove all variants.
  -g, --gnome-shell
        Uninstall dg-yaru GNOME Shell theme.
  -i, --icons
        Uninstall dg-yaru icon theme.
  -c, --cursors
        Uninstall dg-yaru cursor theme.
  -s, --sounds
        Uninstall dg-yaru sound theme.
      --gtk3
        Uninstall dg-adw-gtk3.
      --gtk4
        Uninstall dg-libadwaita.
      --snap
        Uninstall dg-adw-gtk3-theme Snap.
  -h, --help
        Show this screen.

Run './uninstall.sh' with any number of the above options to choose which parts of the theme to uninstall."
Or run './uninstall.sh' with no arguments to uninstall the entire theme."
```

## Flatpak Apps
Run this command once to let all Flatpak apps access the themes:
```
flatpak override --user --filesystem=xdg-config/gtk-4.0 --filesystem=xdg-data/themes
```

## Snap Apps
If Snap is installed you can enable Snap support when configuring the theme.

If you really want Snaps to access the GTK4/Libadwaita configuration, you will have to run this command, replacing `SNAP-NAME` with the name of the Snap:
```
sudo mount --bind --mkdir ~/.config/gtk-4.0 ~/snap/SNAP-NAME/current/.config/gtk-4.0
```
For this to persist after reboot, you need to add the following line to /etc/fstab. Replace `USERNAME` and `SNAP-NAME` with the correct information.
```
/home/USERNAME/.config/gtk-4.0  /home/USERNAME/snap/SNAP-NAME/current/.config/gtk-4.0  none  bind  0  0
```

## GDM Theme
I recommend using [gdm-tools](https://github.com/realmazharhussain/gdm-tools) or [Login Manager Settings](https://flathub.org/apps/details/io.github.realmazharhussain.GdmSettings) to change the GDM theme to dg-yaru.

If you change the GDM theme and later choose to uninstall the theme, reset the GDM theme to default first or you might encounter issues.

## Other Desktop Environments
GNOME versions before 42 and other DEs should work as well, the GNOME Shell theme just won't be installed. If your desktop doesn't use gsettings, the install script will also skip enabling most of the themes.

## Copying
The scripts in this repository are licensed under the GPL v3.0, but the themes each have their own licensing (you can access each repository through GitHub under the src directory).

## Issues
If you have any issues, open one here and specify which part of the theme is causing it. Please try to make sure it is only an issue with one of my themes and not with the upstream project it is based on. If the issue also exists upstream, open it there instead.

## Credits
A huge thanks to:
- [Ubuntu](https://ubuntu.com/) for [Yaru](https://github.com/ubuntu/yaru)
- [vinceliuice](https://github.com/vinceliuice) for [WhiteSur-gtk-theme](https://github.com/vinceliuice/WhiteSur-gtk-theme) and [Colloid-gtk-theme](https://github.com/vinceliuice/Colloid-gtk-theme)
- [rafaelmardojai](https://github.com/rafaelmardojai) for [firefox-gnome-theme](https://github.com/rafaelmardojai/firefox-gnome-theme)
- [lassekongo83](https://github.com/lassekongo83) for [adw-gtk3](https://github.com/lassekongo83/adw-gtk3)
