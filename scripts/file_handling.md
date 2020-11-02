# File Handling
Bash commands presented in this file are to make easier working with files from the terminal.

### Count files in a directory
```bash
find . -type f | wc -l
```
### Count files in a directory and add current time
```bash
find . -type f | wc -l && date +%H:%M:%S
```
### List folders name and size of a directory 
```bash
for i in `ls`
do
du -hs $i
done
```