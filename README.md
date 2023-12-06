# KiCad Libraries

This repository contains a library of electronic components for use with
[KiCad 7.0](https://www.kicad.org). This library is developed primarily for use
in my own projects and might prove limited for general use. It is, however,
meant to be used as a project-specific library, and thus, can be used together
with the default global KiCad library.

# Cloning

This repository must be cloned into the right location in order to be included
in a KiCad project.

- Open a terminal and navigate to your project directory.

  ```
  cd /path/to/your/kicad/project
  ```

- If your project is not itself maintained as a Git repository, simply clone
  this library into a directory called `library`.

  ```
  git clone https://github.com/Kenneth-Goveas/KiCad-Libraries.git library
  ```

  Chances are that your project is itself maintained as a Git repository. In
  this case, add this library as a submodule.

  ```
  git submodule add https://github.com/Kenneth-Goveas/KiCad-Libraries.git library
  ```

  Note that the target directory must necessarily be named `library`. The
  library will not work if the directory is named differently.

- Create symbolic links to the symbol and footprint tables.

  ```
  ln -s ./library/sym-lib-table sym-lib-table
  ln -s ./library/fp-lib-table fp-lib-table
  ```

If the above steps are successfully completed, you should end up with a
directory structure similar to the following.

```
project-directory/
|__ project-name.kicad_pro
|__ project-name.kicad_prl
|__ project-name.kicad_pcb
|__ project-name.kicad_sch
|__ sym-lib-table -> ./library/sym-lib-table
|__ fp-lib-table -> ./library/fp-lib-table
|__ library/
    |__ symbols/
    |__ footprints/
    |__ models/
    |__ sym-lib-table
    |__ fp-lib-table
```

# Usage

To avoid name clashes with the default global library, all symbol and footprint
libraries from this repository are exposed to KiCad with the prefix `Local_`.
Thus, the `MCU_Microchip.kicad_sym` symbol library will be visible in KiCad as
`Local_MCU_Microchip` and the `Package_QFP.pretty` footprint library will be
visible in KiCad as `Local_Package_QFP`.
