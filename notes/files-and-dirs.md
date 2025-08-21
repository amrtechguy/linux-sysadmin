# Files and Directories

## Notes
- `wildcards` are special characters that the shell can understand and interpret for matching filename patterns.
- `globbing` is the process of using wildcards.
- `wildcards` could be used with any command that accepts a filename as an argument e.g `cat *.txt`.

## Create

```bash
# create a dir.
mkdir dir1

# create multiple dirs.
mkdir dir1 dir2 dir3

# create a file if not exists.
touch file1

# create multiple files.
touch file1 file2 file3

# input, CTRL+D to save.
cat > file1

# input, save.
nano file1
```

## Copy

```bash
# copy a dir.
cp -r dir1 dir2

# copy a file.
cp file1 filecopy1

# copy multiple files into a dir.
cp file1 file2 file3 dir1

# copy files with a pattern into a dir.
cp file[[:digit]] dir1
```

## Move/Rename

```bash
# rename a dir.
mv dir1 dir2

# move a dir into a dir.
mv dir1 existed_dir

# move rename a file.
mv file1 file2

# move multiple files into a dir.
mv file1 file2 file3 dir1
```

## Remove

```bash
# remove multiple files
rm -i file1 file2 file3

# remove a pattern of files, prompt each one.
rm -i *.html

# remove a dir, don't prompt.
rm -rf dir1
```

## Links

```bash
# create a hard link.
# Note: different names, same inode.
ln file1 hard1

# symlink -> relative path.
ln -s file1 sym1

# symlink -> absolute path.
ln -s /home/user/file1 sym1

# indexes
ls -li

# copy the original file.
cp sym1 file1_copy

# append to the original file.
echo "New data..." >> sym1
```

## Gaps
- [ ] Are wildcards and globbing used with filenames only, not with directory names?
- [ ] Are wildcards are used only for files selection, not for file creation?
- [ ] Can I use wildcards with files and directories creation? What is `touch file{1..3}`?
- [ ] Does `cp` command modify the destination file's attributes?
- [ ] Does `mv` command modify the destination file's attributes?
- [ ] Do all operations happen to the symbolic link happen to the link's target (file or dir)?
- [ ] What are `GNOME` and `KDE`?