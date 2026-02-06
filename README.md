# pdfcrop-lua5-port

A pure Lua 5.4 port of the [pdfcrop](https://ctan.org/pkg/pdfcrop) tool by Heiko Oberdiek.

## Description

`pdfcrop` calculates and removes page margins from PDF files. This port rewrites the original Perl script in pure Lua 5.4, making it more portable and easier to embed in other applications.

## Features

- Pure Lua 5.4 implementation (no FFI required)
- Cross-platform support (Windows and Unix)
- Automatic Ghostscript detection (including Windows Registry lookup)
- Support for pdfTeX, XeTeX, and LuaTeX backends
- Per-page or global bounding box overrides
- Margin adjustment with optional clipping
- PDF version control

## Requirements

- Lua 5.4
- Ghostscript
- A TeX engine (pdfTeX, XeTeX, or LuaTeX)

## Usage

```
pdfcrop [options] <input.pdf> [output.pdf]
```

### Options

| Option | Description |
|--------|-------------|
| `--help` | Print usage information |
| `--version` | Print version number |
| `--verbose` / `--noverbose` | Enable/disable verbose output |
| `--quiet` / `--noquiet` | Enable/disable normal output |
| `--debug` / `--nodebug` | Enable/disable debug information |
| `--gscmd <name>` | Specify Ghostscript command |
| `--pdftex` / `--xetex` / `--luatex` | Select TeX engine |
| `--margins "<l> <t> <r> <b>"` | Add extra margins (in bp) |
| `--clip` / `--noclip` | Enable/disable clipping |
| `--hires` / `--nohires` | Use HiResBoundingBox |
| `--ini` / `--noini` | Use iniTeX variant |

### Expert Options

| Option | Description |
|--------|-------------|
| `--restricted` | Enable restricted mode |
| `--papersize <size>` | Set Ghostscript paper size |
| `--resolution <dpi>` | Set Ghostscript resolution |
| `--bbox "<l> <b> <r> <t>"` | Override bounding box for all pages |
| `--bbox-odd "<l> <b> <r> <t>"` | Override bounding box for odd pages |
| `--bbox-even "<l> <b> <r> <t>"` | Override bounding box for even pages |
| `--pdfversion <ver>` | Set PDF version (e.g., 1.4, auto, none) |
| `--uncompress` | Create uncompressed PDF |

## Examples

Basic cropping:
```bash
lua pdfcrop.lua input.pdf output.pdf
```

Add 10bp margins on all sides:
```bash
lua pdfcrop.lua --margins 10 input.pdf output.pdf
```

Crop with clipping and custom margins:
```bash
lua pdfcrop.lua --clip --margins "5 10 5 10" input.pdf output.pdf
```

Use XeTeX backend:
```bash
lua pdfcrop.lua --xetex input.pdf output.pdf
```

## Credits

- Original pdfcrop: Heiko Oberdiek, Oberdiek Package Support Group
- Lua port: Li Ruijie

## License

This work is licensed under the LaTeX Project Public License (LPPL) version 1.3c or later.
See the [LICENSE](LICENSE) file for details.
