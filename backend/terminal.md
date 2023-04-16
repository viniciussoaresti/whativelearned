# Terminal

# Contents:

- [Terminal](#terminal)
- [Contents:](#contents)
- [Man(ual) command:](#manual-command)
- [Commands:](#commands)
  - [pwd:](#pwd)
  - [ls:](#ls)
  - [file:](#file)
  - [stat:](#stat)
  - [mkdir:](#mkdir)
  - [touch:](#touch)
  - [cp](#cp)
  - [\* and ? wildcards:](#-and--wildcards)
  - [find:](#find)
  - [less:](#less)
  - [Cat:](#cat)


# Man(ual) command:

We can type `man (command)` to understand more about some commands, for example:

`man ls`

# Commands:

## pwd:

Informs the current directory:

`pwd`

## ls:

Lists files and folders:

`ls`

Accepts as arguments:

- `-l`: more information;
- `-a`: lists all files even hidden ones;
- `-h`: more human-readable content;
- `-R`: recursive (shows folder contents and such);
- `-S`: orders by size.

Example:

`ls -laRhS` 

## file:

Informs some file specific information like file type and format specific info:

`file test.json`

## stat:

Informs some general file information like owner, modifications and size: 

`stat test.json`

## mkdir:

Makes directories:

`mkdir test`

Accepts as arguments:

- `-p`: creates parent folders also:

`mkdir -p test/test2/test3 test/test4`

## touch:

Changes file time registry when the file already exists, and creates files:

`touch test.json test1.json test2.json`

## cp

Copies files, but to copy directories, accepts the `-r` argument:

`cp -r testFolder testFile destinationFolder`

## * and ? wildcards:

They're used when we need to copy files and folders following the name specified,
or with a character after it:

`mv fil* directoryToCopy`

`mv fil? directoryToCopy`

## find:

Finds files and directories:

Accepts as arguments:

- `-type`: `d` for directory, `f` for file;
- `-name`: receives the search 'query'.
- `-iname`: same as name but independent of letter cases.

Example:

`find . -type f -name "*.mp4"`

## less:

View file content navigating through it:

`less file.json`

## Cat:

View file content printed on the terminal:

`cat file.json`