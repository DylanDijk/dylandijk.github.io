---
layout: post
title: Linux Commands
date: 2023-02-16 14:41 +0000
---

Basic Commands:

Correct grammar of command is: `verb adverb object`  
where `adverb` is the flag you add to a command e.g `-hl` in `ls -hl` 

To view the flags for a command use `man` e.g `man ls`

- `cd -` go back to previous directory you were in
- `ls` list files in a directory
    - `ls -hl` more human readable version of `ls -l`
    - `ls -t` order by modification date, newest first
- `cp` copy a file
    - `cp data1 data3` copies a `data1` file to `data3` 
- `cp -r` to copy a folder with files inside 
- `rm` remove a file
- `mv` changes a file name
- `cat` output contents of the file
    - `head` output top part of the file
        - use `-n` flag to choose the number of lines e.g `-5`
    - `tail` print top part of the file
- `less` opens a pager to view a file
    - within the pager can use `/` to search in the file then press `n` to search for the next file.
- `grep` is used to search a file e.g `grep "fish" king-lear.txt`
    - to count the number of lines in a text file add `-c` `tag grep -c  "fish" king-lear.txt`
