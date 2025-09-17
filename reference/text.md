# LINUX: TEXT

**Notes**
- Unix end of line: `\n`.
- MS-DOS (Windows) end of line: `\r\n`.

## Display

**cat**

```bash
# globbing
cat *.txt

# non-printable chars
cat -A topic.txt

# number lines
cat -n topic.txt

# override/create file with content
cat > file.txt
input...
<CTRL+D>

# append/create file with content
cat >> file.txt
input...
<CTRL+D>
```

## Search


## Edit


## Compare


## Join


## Format

**ln**

```bash
# number non-blank lines
ln report.txt
```

**fold**

```bash
# limit line width, break at spaces
fold -w 30 -s report.txt
```

**fmt**

```bash
# format paragraphs
fmt -cw 50 article.txt
```

**pr**

```bash
# paginate text file
pr -l 22 -w 65 article.txt
```

**printf**

```bash
# format, convert, insert -> args in string based on specifier type (%)
printf "My name is %s\n" "First Second"
printf "%s %d %f %o %x %X\n" 255 255 255 255 255 255
printf "Balance: %.2f\n" 65000.55686
```

**groff**

```bash
# PostScript document
zcat /usr/share/man/man1/ls.1.gz  | groff -mandoc > ls.ps

# convert .ps to .pdf
ps2pdf ls.ps ls.pdf

# convert .ps to ascii
ps2ascii ls.ps ls.txt
```