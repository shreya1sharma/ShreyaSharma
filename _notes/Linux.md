---
layout : page
title: Linux

---
**find**: to locate a specific file by name or extension 

- syntax: \
find options starting/path expression
- example
```bash
find /home -name *.jpg 	# to find all .jpg files in the /home and sub-directories.
```
**cp** : to copy a file from one place to another

- syntax:\
cp SOURCE DEST\
cp SOURCE DIRECTORY\
cp SOURCE1 SOURCE2 SOURCE3 SOURCEn DIRECTORY\
cp [OPTION] SOURCE DEST\
cp [OPTION] SOURCE DIRECTORY\

- example:\
```bash
cp file.doc newfile.doc       #to make copy of a file
cp file.doc /temp             #to copy file to another directory
cp main.c demo.h lib.c /temp  #to copy multiple files
cp * /temp                    #to copy all files
```

