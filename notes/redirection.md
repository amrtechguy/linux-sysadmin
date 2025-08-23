# Redirection

## Notes
- The program has 3 default streams (`stdin`, `stdout`, `stderr`).
- The `stdin` is linked to the keyboard by default.
- The `stdout` of program's data and `stderr` of status and error messages are linked to the screen by default.

## Redirection

```bash
# redirect `stdout` to file.
ls . >> output.txt

# redirect `stderr` to file.
ls missing_dir 2>> output.txt

# redirect `stdout` and `stderr` to file.
ls . &>> output.txt

# redirect `stdout` to file.
# redirect `stderr` to file.
ls . >> data.txt 2>> errors.txt

# redirect `stderr` to `bit bucket` device.
ls missing_dir 2> /dev/null

# redirect `stdin` to file.
cat < output.txt
```

## Pipelines

```bash
# load contents, sort lines, ommit adjacent duplicates, store in file.
cat usernames | sort | uniq > unique_usernames

# duplicate usernames count.
cat usernames_1.txt usernames_2.txt | sort | uniq -d | wc -l

# list all commands without `disk` term.
ls /usr/bin /usr/sbin | grep -i -v disk

# keep displaying appended lines
tail -f logs

# ...
echo "log ..." | sudo tee -a /var/log/myapp/logs.log

# list all binaries, append them to 2 files, display lines with `disk` term.
ls /usr/bin /usr/sbin | tee -a bins_1 bins_2 | grep disk
```

## Gaps
- [ ] What are the streams `stdin`, `stdout`, `stderr`?
- [ ] Are they stored on hard disk as files or in memory?
- [ ] Do they exist only in Unix programs or in any program of any other system like Windows?
- [ ] Are the command's options and arguments considered stdin?
- [ ] Are there global system streams for all programs?
- [ ] What does this ` ls -l /bin/usr > ls-output.txt 2>&1` do?
- [ ] The command reading from `arguments list` vs `stdin`.
- [ ] `ls . > output.txt` why each item's name is stored in a single line, unlike the screen output?
- [ ] `ls -l /bin` vs `ls -l /usr/bin`.
- [ ] Can use `wildcards` with `grep`?