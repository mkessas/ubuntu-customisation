# Customising Ubuntu

## Packages

Install the following packages using `apt`:

- gnome-tweak-tool
- vim
- git

Install the following packages manually:

- [Visual Studio Code](https://go.microsoft.com/fwlink/?LinkID=760868)
- [Google Chrome](https://www.google.com/chrome/)

## Miscellaneous

### High CPU Bug

```sh
# grep -r . /sys/firmware/acpi/interrupts/
```

```sh
@reboot	echo "disable" > /sys/firmware/acpi/interrupts/gpe66
```

## Look and Feel

### Backgrounds

Install the backgrounds in the `backgrounds/` directory by putting them in the `Pictures` folder then pointing to them from `Backgrounds` menu

### Fonts

Copy the fonts in the `fonts/` directory to `/usr/local/share/fonts/` directory then run the `fc-cache -fv` command to reload the cache.

### Behavior
