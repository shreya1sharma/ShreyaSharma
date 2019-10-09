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
**cp**: to copy a file from one place to another
- syntax:\
cp SOURCE DEST\
cp SOURCE DIRECTORY\
cp SOURCE1 SOURCE2 SOURCE3 SOURCEn DIRECTORY\
cp [OPTION] SOURCE DEST\
cp [OPTION] SOURCE DIRECTORY\

- example:
```bash
cp file.doc newfile.doc       #to make copy of a file
cp file.doc /temp             #to copy file to another directory
cp main.c demo.h lib.c /temp  #to copy multiple files
cp * /temp                    #to copy all files
```
**rm**: to remove or delete a file or directory
- syntax:\
rm filename\
rm file1 file2 file3\
rm [OPTION] filename\
rmdir EMPTY_DIRECTORY\
rm -d EMPTY_DIRECTORY\
rm -r NON_EMPTY_DIRECTORY  #r stands for recursive\
rm -r NON_EMPTY_DIR1 NON_EMPTY_DIR2\

- options:\
i : to confirm each file before deleting
f : to remove files without prompting even if files are write-protected

- example:
```bash
rm file.doc
rm file1.doc file2.pdf
rm *.pdf
rm -i file.doc
rm -f file.doc
rm -r temp
rm -rf temp               #VERY DANGEROUS!!! Removes a directory and all its contents without prompting
```
