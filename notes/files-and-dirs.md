# Files and Directories

## Notes
- Learning how to work with files and directories.

## Wildcards
- `**wildcards**` are special characters that the shell can understand and interpret for matching filename patterns.
- `**globbing**` is the process of using wildcards.
- `wildcards` could be used with any command that accepts a filename as an argument e.g `cat *.txt`.

### Wildcard Characters

| Character | Meaning |
| --- | --- |
| * | Matches any characters of any type with any count. |
| ? | Matches a single character. |
| [charachters] | Matches a single character from the set. |
| ![charachters] | Matches a single character outside the set. |
| [[:class]] | Matches a single character from a character class. |
| [![:class]] | Matches a single character outside a character class. |

### Character Classes

| Class | Meaning |
| --- | --- |
| [[:alphnum]] | Matches a single alphanumeric character. |
| [[:alpha]] | Matches a single alphabetic character. |
| [[:digit]] | Matches a single numeral character. |
| [[:upper]] | Matches a single upercase letter. |
| [[:lower]] | Matches a single lower letter. |

### Character Ranges

| Range | Meaning |
| --- | --- |
| [a-z] | Matches a single lowercase letter. |
| [A-Z] | Matches a single uppercase letter. |
| [0-9] | Matches a single numeral character. |
| [0-9a-zA-Z] | Matches a single alphanumeric character. |

### Examples

```bash
# Matches any filename ending by `.txt`.
*.txt

# Matches any file name begins with any 3 characters and ends with `.txt`.
???.txt
```

## Create

### Dirictory

```bash
# creates a directory.
mkdir dir1

# creates multiple directories.
mkdir dir1 dir2 dir3
```

### File

```bash
# creates a file if not exists.
touch file1

# creates multiple files.
touch file1 file2 file3

# will display a prompt for receiving input as the file's content.
# press `CTRL+D` to save and close.
cat > file1

# opens a commandline text editor named `nano` to add the file's content.
nano file1
```

## Copy
- `cp` command overwrites the destination file by default without notifying the user, so I can use `cp -i`.
- `cp` command changes some of the destination file's attributes e.g. `user`, `group`, `last modified date and time`.

### Options

| Option | Meaning |
| --- | --- |
| a ,--archive | Copy the attributes of the original file too. |
| i, --interactive | If the file exists in the destination, then prompt the user and continue if the answer is `y` or `yes`. |
| u, --update | Copy the file only if not exists in the destination or the exisiting file has an older last modified date. |
| r, --recursive | Copy recursively all a directory contents, including the subdirectories. |
| v, --verbose | Display informative messages as the copy is performed. |

### Directory

```bash
# copy recursively all contents of `dir1` to `dir2`.
# if `dir2` exists, `dir1` will be copied inside `dir2` with the name `dir1`.
cp -r dir1 dir2
```

### File

```bash
# copy `file1` to the same directory with a different name `filecopy1`.
# if `filecopy1` exists and is a directory, the `file1` will be copied with the same name inside the directory.
cp file1 filecopy1

# copy multiple files to a directory.
# directory must exist.
cp file1 file2 file3 dir1

# copy all files that begin with file then a numeral character to `dir1`.
cp file[[:digit]] dir1
```

## Move/Rename
- Using the command `mv` with operations similar to `cp` command.
- Supports the options `-i`, `-u`, `-v`.
- `mv` does not changes the `last modified date and time` of the directory or its contents.

### Directory

```bash
# move `dir1` to the same directory with a different name.
mv dir1 dir2

# if the directory `existed_dir` does exist, then `dir1` will be moved with its contents to `existed_dir`.
mv dir1 existed_dir
```

### File

```bash
# move the `file1` to the same directory with a different name.
mv file1 file2

# move the files to the exisiting directory.
# the directory must exist.
mv file1 file2 file3 dir1
```

## Gaps
[ ] Are wildcards and globbing used with filenames only, not with directory names?
[ ] Are wildcards are used only for files selection, not for file creation?
[ ] Can I use wildcards with files and directories creation? What is `touch file{1..3}`?
[ ] Does `cp` command modify the destination file's attributes?
[ ] Does `mv` command modify the destination file's attributes?