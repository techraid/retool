# Retool

Retool is a command line tool that creates 1G1R versions of
[Redump](http://redump.org/) dats. This is not an official Redump project.

## Installation

There are two ways you can install and run Retool.

### Binaries

If Git and Python aren't your thing, you can download ZIP files containing
Windows and macOS binaries from the
[dist](https://github.com/unexpectedpanda/retool/tree/master/dist) folder. Make
sure to grab the clonelists + config ZIP file as well, and extract them both
into the same folder to install.

### Python

For more code-savvy users, you can clone Retool from this repo and run it with
[Python](https://www.python.org/), which will give you better performance.
Retool requires a minimum of Python 3.8, and needs three additional modules.

To install the modules, assuming you already have Python installed, open
Terminal, Command Prompt, or whatever the CLI is on your system, and type:

```
pip install bs4
pip install lxml
pip install strictyaml
```

## Usage

Retool is a command line tool. If you have Python, you use it with the
following syntax:

```
python retool.py -i <input dat/folder> <options>
```

Or for the binary version:

```
retool -i <input dat/folder> <options>
```

A new file is automatically generated, the original file isn't altered.
Edit the `user-config.yaml` file to set region order and filter languages.
Remove languages or regions by adding a `#` to the beginning of the relevant
line.

### Options

* `-o` \<output folder\> Set an output folder
* `-x` Export dat in legacy parent/clone format
  (for use with Clonerel, not dat managers)
* `-v` Verbose mode: report clone list errors
* `-l` Filter languages using a list (see user-config.yaml)
* `-g` Enable most filters (-a -b -c -d -e -m -p -s)
* `-s` Enable supersets: special editions, game of the year
  editions, and collections replace standard editions
* `-a` Exclude applications
* `-b` Exclude coverdiscs
* `-c` Exclude compilations with no unique titles
* `-d` Exclude demos
* `-e` Exclude educational titles
* `-m` Exclude multimedia titles
* `-p` Exclude preproduction titles (alphas, betas, prototypes)
* `-u` Exclude unlicensed titles

You can learn more about
[Retool's options](https://github.com/unexpectedpanda/retool/wiki/Usage-and-options#More-options-information)
and how it works on the [wiki](https://github.com/unexpectedpanda/retool/wiki/).

## Clone lists

While Retool is smart enough to automatically match certain types of parents and
clones, there are certain situations that require manual assignment. To achieve
this, Retool keeps clone lists.

Clone lists are updated independently of the program, and are formatted as JSON
files. You can either download them manually from the
[clonelists folder](https://github.com/unexpectedpanda/retool/tree/master/clonelists),
pull everything into your local repo, or download the clonelists + config ZIP file
from the
[dist](https://github.com/unexpectedpanda/retool/tree/master/dist) folder. The
JSON files must be uncompressed, and stored in a folder called `clonelists` in the
same folder as Retool for them to be recognized.

<hr>

# Clonerel

Clonerel generates an Excel file from a parent/clone dat file that has been
generated by Retool using the `-x` option. It helps you to more easily
visualize parent/clone relationships, and track down titles that haven't
been assigned parents yet.

## Installation

Clonerel uses openpyxl to generate an Excel file. You'll need at least OpenPyxl
v3.03 to avoid a fun crash bug. Install it with `pip`.

```
pip install openpyxl
```

If you haven't already installed them for Retool, you'll need also lxml and
bs4.

```
pip install bs4
pip install lxml
```

## Usage

```
python clonerel.py <input dat>
```