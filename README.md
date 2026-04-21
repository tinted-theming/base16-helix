# Tinted Helix

[Tinted Theming] templates for the [Helix] text editor supporting [Base16],
[Base24] and [Tinted8] color schemes.

## Supported Systems

| System    | Template                      | Description                                                              |
| --------- | ----------------------------- | ------------------------------------------------------------------------ |
| [Tinted8] | `templates/tinted8.mustache`  | Semantic theming with named palette colors and rich syntax/UI properties |
| [Base16]  | `templates/base16.mustache`  | 16-color schemes with semantic mapping                                   |
| [Base24]  | `templates/base24.mustache`   | Extends Base16 with 8 bright color variants and darker backgrounds       |

## Usage

### Manual

Copy the generated `.toml` theme files from the `themes/` directory to your
Helix themes directory:

- **Linux/macOS**: `~/.config/helix/themes/`
- **Windows**: `%AppData%\helix\themes\`

Then set your theme in `~/.config/helix/config.toml`:

```toml
theme = "base16-ayu-dark"
```

### Tinty

[Tinty] is a theming manager for [Tinted Theming] that can apply themes across
multiple applications with a single command. To use it with Helix, add the
following to your Tinty `config.toml`:

```toml
[[items]]
name = "tinted-helix"
path = "https://github.com/tinted-theming/tinted-helix"
themes-dir = "themes"
hook = "cp -f \"%f\" ~/.config/helix/themes/ && helix --health > /dev/null 2>&1"
supported-systems = ["tinted8", base16", "base24"]
```

Then apply a theme:

```sh
tinty sync # Required on first run and after config changes
tinty apply base16-ayu-dark
```

To select a theme interactively with [fzf]:

```sh
tinty apply $(tinty list | fzf)
```

See the [Tinty README] for installation and further configuration.

## Theme Features

All templates provide styling for:

- **Syntax highlighting**: comments, strings, constants, keywords, functions,
  types, variables, operators, and more
- **UI elements**: background, cursor, gutter, statusline, menus, popups,
  selections, and indent guides
- **Markup**: bold, italic, headings, links, lists, quotes, and code blocks
- **Diff indicators**: inserted, deleted, and changed lines
- **Diagnostics**: hint, info, warning, and error underlines

## Contributing

See the [Tinted Theming contribution guidelines].

## License

This project is licensed under the [MIT License](LICENSE).

[Base16]: https://github.com/tinted-theming/home/blob/main/styling.md
[Base24]: https://github.com/tinted-theming/base24/blob/main/styling.md
[Tinted8]: https://github.com/tinted-theming/home/blob/main/specs/tinted8/styling.md
[Helix]: https://github.com/helix-editor/helix
[Tinted Theming]: https://github.com/tinted-theming
[Tinted Theming contribution guidelines]: https://github.com/tinted-theming/home/blob/main/CONTRIBUTING.md
[fzf]: https://github.com/junegunn/fzf
[Tinty]: https://github.com/tinted-theming/tinty
[Tinty README]: https://github.com/tinted-theming/tinty/blob/main/README.md
[tinted-builder-rust]: https://github.com/tinted-theming/tinted-builder-rust
