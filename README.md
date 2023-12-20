# KiCad Libraries

This repository contains a library of electronic components for use with
[KiCad 7.0][kicad]. This library is developed primarily for my own projects, and
is not as extensive as the standard KiCad library. Any repositories hosted by me
will use this library if they contain KiCad projects.

## Adding the library to your project

Carry out the following steps to add this library to your KiCad project. If you
use Linux, simply open a terminal to enter the commands listed below. If you use
Windows, make sure you run these commands from Git Bash (the usual Windows
command line does not recognize these commands). You may also need to enable
[developer mode][win-dev-mode] on Windows, to be able to create symbolic links.

Navigate to your KiCad project directory. This is the directory containing the
`*.kicad_pro` file for your project.

```
cd /path/to/your/KiCad/project
```

If your project is not itself maintained as a Git repository, simply clone this
library into a directory named `library`.

```
git clone https://github.com/Kenneth-Goveas/KiCad-Libraries.git library
```

Chances are however, that your project is indeed maintained as a Git repository
itself. If so, clone this library as a Git submodule instead.

```
git submodule add https://github.com/Kenneth-Goveas/KiCad-Libraries.git library
```

Finally, create symbolic links to the symbol and footprint library tables, so
that KiCad can locate this library in your project.

```
ln -s ./library/fp-lib-table fp-lib-table
ln -s ./library/sym-lib-table sym-lib-table
```

Note that the target directory for cloning must necessarily be named `library`.
The library will not work if the target directory is named differently.

If the above steps were successfully completed, you should end up with the
following directory structure.

```
project-directory/
|__ project-name.kicad_pro
|__ project-name.kicad_sch
|__ project-name.kicad_pcb
|__ fp-lib-table -> ./library/fp-lib-table
|__ sym-lib-table -> ./library/sym-lib-table
|__ library/
    |__ symbols/
    |__ footprints/
    |__ models/
    |__ fp-lib-table
    |__ sym-lib-table
```

If so, then the library has successfully been added to your project.

## Nomenclature within the library

To avoid name clashes with the default global KiCad library, all symbol and
footprint libraries from this repository are exposed to KiCad with the prefix
`Local_`. Thus, the `MCU_Microchip.kicad_sym` symbol library will be visible in
KiCad as `Local_MCU_Microchip` and the `Package_QFP.pretty` footprint library
will be visible in KiCad as `Local_Package_QFP`.

## Fonts used in the library

The [Fira Sans Condensed][fira] font was used while creating the symbol library,
instead of the default KiCad font. This is because the default font occupies
more space, making it difficult to fit schematics on the page. It is, therefore,
recommended to install and use the aforementioned font while using this library.
To set up KiCad accordingly, click on *Preferences > Preferences > Schematic
Editor > Display Options* and choose from the *Default font* drop down menu.

[kicad]:        https://www.kicad.org
[win-dev-mode]: https://learn.microsoft.com/en-us/windows/apps/get-started/enable-your-device-for-development
[fira]:         https://fonts.google.com/specimen/Fira+Sans+Condensed
