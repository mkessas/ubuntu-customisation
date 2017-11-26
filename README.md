# Customising Ubuntu

## Packages

Install the following packages using `apt`:

- gnome-tweak-tool
- arc-theme
- vim
- git

Install the following packages manually:

- [Visual Studio Code](https://go.microsoft.com/fwlink/?LinkID=760868 "Visual Studio Code")
- [Google Chrome](https://www.google.com/chrome/ "Google Chrome")
- [Postman](https://app.getpostman.com/app/download/linux64 "Postman REST Client")

## Miscellaneous

### High CPU Bug

The bug is present if you run `top` and find a `kworker` process consuming high CPU even when idle.

Identify the `gpe` with the highest CPU usage.  Run this command

```sh
# grep -r . /sys/firmware/acpi/interrupts/
```

then locate the `gpe??` file which has the highest first column.

Add the following `crontab` entry under `root`.  Change `gpe66` to the correct value acquired from the previous step.

```sh
@reboot	echo "disable" > /sys/firmware/acpi/interrupts/gpe66
```

## Look and Feel

### Backgrounds

Install the backgrounds in the `backgrounds/` directory by putting them in the `Pictures` folder then pointing to them from `Backgrounds` menu

### Fonts

Copy the fonts in the `fonts/` directory to `/usr/local/share/fonts/` directory then run the `fc-cache -fv` command to reload the cache.

### Icons

Adding a new Ubuntu _Launcher_ application is a matter of adding a new `.desktop` file and the associated icon files.

#### Adding .desktop file

Create a new Launcher definition file and give it the `.desktop` extension, then place it in the `/usr/local/share/applications` directory.

A typical example is as follows:

```conf
[Desktop Entry]
Version=1.0
Name=Postman
GenericName=Postman
Comment=REST API Client
Exec=/usr/local/bin/postman %U
Terminal=false
Icon=postman
Type=Application
Categories=Network;
MimeType=application/json;
Actions=NewWindow;

[Desktop Action NewWindow]
Name=New Window
Exec=/usr/local/bin/postman
```

#### Adding Icon Files

Add icons to the `/usr/share/icons/hicolor` directory.  For each color resolution, add a new file under the _resolution_/`apps` directory (eg: `512x512/apps`).

Once this is done, reload the icon cache using:

```sh
$ sudo update-icon-caches /usr/share/icons/*
```

### Behavior

General behavior settings.

#### Dock

Go to *Settings* > *Dock* and set the **Icon Size** to `24`

#### Terminal

Import the terminal configuration using `dconf`:

```sh
dconf load /org/gnome/terminal/ < conf/terminal.dconf
```

##### General

Set the `Initial terminal size` to `132`columns and `43` rows.

Choose **Custom font** and set the font to `Consolas Regular 9`

##### Colors

Untick **Use colors from system theme** then click the **Text** box for `Default color` and set it to plain white.  Click the **Background** for `Default color` and set the value to `#303030`

#### Gnome Tweak Tool

Open the tool from the *Activities* menu using the `Super` key and search for `tweak`

##### Appearance

Set *Applications* under *Themes* heading to `Arc`

##### Desktop

For *Icons on Desktop* heading, set the values to:

- _Show Icons_ to **On**
- _Home_ to **Off**
- _Network Servers_ to **Off**
- _Trash_ to **On**
- _Mounted Volumes_ to **Off**

##### Fonts

Set the following Values:

- _Window Title_ to `Lato Bold 10`
- _Interface_ to `Lato Regular 9`
- _Document_ to `Sans Regular 10`
- _Monospace_ to `Consolas Regular 10`

##### Keyboard & Mouse

Set the **Overview Shortcut** to `Right Super`

##### Power

Enable the **Suspend when laptop lid is closed** option

##### Top Bar

Set the following values:

- *Application Menu* to **On**
- *Battery Percentage* to **On**
- *Date* under **Clock** to **On**
- *Seconds* under **Clock** to **Off**

##### Windows

Set the value for **Window Action Key** to `Super`

##### Workspaces

Click _Static Workspaces_ and set the **Number of Workspaces** to `3`
