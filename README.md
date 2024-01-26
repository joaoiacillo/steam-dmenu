# steam-dmenu

A dmenu wrapper for launching Steam applications more easily.

## Motivation

Launching Steam just to run a single game can be quite an adventure, specially if you are on a slow computer.

That's why this project aims at providing a simple implementation of a launcher for Steam applications through the `dmenu`
interface.

Steam will silently run on the background, and only your game screen will pop out after Steam's load time.

## Install

Since steam-dmenu is just a Bash script, you can either move, copy or link it directly into a
folder located in the `$PATH` env variable (such as `/usr/bin/`).

The `dmenu_run` Bash script that comes shipped in the official dmenu package inserts
itself into `/usr/bin/`. That's why we recommend **moving** steam-dmenu
into it as well.

```bash
$ git clone https://github.com/joaoiacillo/steam-dmenu
$ chmod +x steam-dmenu/steam-dmenu
$ sudo mv steam-dmenu/steam-dmenu /usr/bin
$ rm -fr steam-dmenu/
```

## Usage

You can run `steam-dmenu` directly from the terminal or dmenu, as well as bind a
keymap in your desktop environment. Every argument that comes after the script
name will be directed to dmenu, so customization is possible.

```bash
# Runs steam-dmenu on a separate thread
$ steam-dmenu &
```

### Integrating with i3wm

You can configure your i3wm to run steam-dmenu after some key combination was
pressed. The default we recommend is `$mod+Shift+s`, which stands for "(S)tart
(S)team [App]".

Append the following lines to `~/.config/i3/config` file:

```bash
# Launch steam-dmenu
bindsym $mod+Shift+s exec --no-startup-id steam-dmenu
```

### Case-insensitive search

For compatibility reasons, the default mode for searching in steam-dmenu is the
same as dmenu: case-sensitive. This means that `Terraria` differs from
`terraria` and `tERRaRIA`. That's why we recommend toggling the `-i`
(case-insensitive) option.

```bash
# Runs steam-dmenu in case-insensitive mode
$ steam-dmenu -i &
```

## Configuration

You can configure steam-dmenu through environment variables. Below is a table of
the variables you can modify.

| Name      | Type     | Description                                           |
| --------- | -------- | ----------------------------------------------------- |
| STEAMROOT | `String` | Steam's root folder. Used to get steamapps directory. |

## Customization

This project is literally just a wrapper to dmenu. That's why it is possible to
customize the way it displays. You can use all dmenu customization options.

> Run `man dmenu` for listing all customization options. Use the letter `q` to
> exit the manual.

Below are some common customization options:

### Setting Fira Code as default font

```bash
$ steam-dmenu -fn "Fira Code"
```

### Showing the panel at the bottom

```bash
$ steam-dmenu -b
```

### Modifying the default prompt

```bash
$ steam-dmenu -p "[steam]:"
```

## Contributions

We welcome and appreciate contributions to this project. Feel free to use,
redistribute, and edit the source code under the following guidelines:

1. **Freedom to Use:** You can use the software for any purpose without any restrictions.

2. **Freedom to Modify:** You have the right to modify the source code to suit your needs.

3. **Freedom to Share:** You can distribute your modified or unmodified version of the software.

4. **Open Source:** Any projects derived from this codebase must be free and open-source.

5. **Proper Credits:** When using or redistributing the code, ensure that proper credits are provided to the original authors. This helps acknowledge the contributors and promotes a collaborative community.

If you make enhancements, bug fixes, or other modifications, we encourage you to contribute them back to this project by creating a pull request. By doing so, you help improve the software for everyone.

For major contributions, please reach out to us beforehand to discuss the changes and ensure alignment with the project's goals.

Thank you for considering contributing to our project!

## License

This project is licensed under the GNU GPL v3 license - see the
[LICENSE](./LICENSE) file for more details.
