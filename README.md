<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

# Table of Contents

- [Description](#description)
- [Why did I make this ? ](#why-did-i-make-this-)
- [Installation ](#installation)
- [Usage ](#usage)
- [Example](#example)

<!-- TOC end -->


<!-- TOC --><a name="tocgen"></a>
# Description
Tocgen is a simple python script that generates a table of contents using a specified absolute directory as the root where child markdown files will be converted into a markdown list of links. These links will be added to the specified markdown file. 

<!-- TOC --><a name="why-did-i-make-this-"></a>
# Why did I make this ? 

Well , I was messing around with a jekyll template while converting my "config" repo to a website. This repo is just a giant repo of organized markdown files. So I wanted to turn this into a website with a unique template to showcase what i've been upto for the past 3 years.


This is a simple python script that creates a markdown list with links to the markdown files in a directory. Think of this TOC as one that creates LINKS to other child files, rather than other sections on the page.


<!-- TOC --><a name="installation"></a>
# Installation 

```
git clone https://github.com/buhfur/tocgen $HOME/tocgen
sudo ln -s $HOME/tocgen/tocgen /usr/local/bin/

```


<!-- TOC --><a name="usage"></a>
# Usage 

**Please note you must specify the absolute path for the markdown file if it is not in your current working directory. The directory must always be an absolute path**


```
usage: tocgen [-h] [--show-changes] --dir DIR --file PATH-TO-FILE

optional arguments:
  -h, --help            show this help message and exit
  --show-changes, -s    Show table of contents before writing to file
  --dir DIR, -d DIR     Specify absolute directory as root for Table of
                        Contents
  --file FILE, -f FILE  Absolute path of Mardown file the TOC will be written to

```

<!-- TOC --><a name="example"></a>
# Example

Let's say I have a directory which contains a bunch of markdown files. Using the directory structure below.

```
example/
├── index.md
└── parent
    ├── file1.md
    ├── file2.md
    └── file3.md
```

Our goal here is to add a TOC with links to all files in `parent/` and put said table in `index.md`.

Assuming this directory is stored in the users home dir. I woud run the following comand. 

`tocgen -d /home/$USER/example/parent -f /home/$USER/example/index.md`

Or if you just want to see what the table would look like , you can use the `-s` argument.

`tocgen -s -d /home/$USER/example/parent -f /home/$USER/example/index.md`

And the output (without the -s flag ) will append the table to the end of the markdown file.

**Output**

```
1. [File1](parent/file1.md)
2. [File2](parent/file2.md)
3. [File3](parent/file3.md)
```
