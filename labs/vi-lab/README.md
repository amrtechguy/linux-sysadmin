# vi Lab

## Initial Files

#### story1.txt

```bash
Linux was created by Linus Torvalds.
It is one of the most popular operating systems.
Many servers run Linux.
```

#### story2.txt

```bash
Some users prefer Windows.
Others enjoy macOS.
Open source software is powerful.
```

## Tasks

### Starting & Navigation

- [x] Open `story1.txt` in vi.

```bash
vi story1.txt
```

- [x] Move cursor to the first line.

```bash
# mode: command
1G #gg
```

- [x] Move cursor to the last line.

```bash
# mode: command
G
```

- [x] Move cursor word by word until you reach the word popular.

```bash
# mode: command
2G
7w
```

- [x] Move cursor jump directly to line 2.

```bash
# mode: command
2G
```

### Insert & Append

- [x] Insert a new line at the top of the file: `Author: User`

```bash
# mode: command
1G
O
# mode: insert
Author: User
```

- [x] Append this line at the end of the file: `Date: 2025-08-31`

```bash
# mode: command
G
o
# mode: insert
Date: 2025-08-31
```

- [x] In line 2, after the word `popular`, add the word: `Linux`

```bash
# mode: command
/popular
ea
# mode: insert
 Linux
```

### Deleting & Changing

- [x] Delete the second line entirely.

```bash
# mode: command
2G
dd
```

- [x] In the first line, delete the word `Linus`.

```bash
# mode: command
1G
4w
dw
```

- [x] In the third line, replace the word `servers` with `computers`.

```bash
# mode: command
:s/servers/computers/
```

### Undo & Redo

- [x] Undo the change you just made (`servers → computers`).

```bash
# mode: command
u
```

- [x] Redo it again so the line reads: `Many computers run Linux.`

```bash
# mode: command
<CTRL+R>
```

### Copying & Pasting

- [x] Copy the entire first line (`Linux was created by Linus Torvalds.`) and paste it at the bottom of the file.

```bash
# mode: command
1G
yy
G
p
```

- [x] Copy just the word `Linux` and paste it after the word `computers` in the third line, so it becomes: `Many computers Linux run Linux.`

```bash
# mode: command
/Linux
yw
/computers
ea
<ESC>
<SPACE>
p
```

### Searching & Replacing

- [x] Search for the word `Linux` and move through each occurrence.

```bash
<ESC>
/Linux
<ENTER>
n
```

- [x] On the current line, replace the first `Linux` with `GNU/Linux`.

```bash
<ESC>
:s/Linux/GNU\/Linux/
```

- [x] Replace all occurrences of `Linux` in the entire file with `GNU/Linux`.

```bash
<ESC>
:%s/Linux/GNU\/Linux/g
```

### Saving & Quitting

- [x] Save the file without quitting.

```bash
<ESC>
:w
```

- [x] Quit vi without saving, then reopen `story1.txt` to confirm the last saved state.

```bash
<ESC>
:q!
vi story1.txt
```

- [x] Save and quit normally.

```bash
<ESC>
:wq
```

### Working with Multiple Files

- [x] Open both `story1.txt` and `story2.txt` together in vi.

```bash
vi story1.txt story2.txt
```

- [x] Switch from `story1.txt` to `story2.txt`.

```bash
<ESC>
bn
```

- [x] Copy the line `Open source software is powerful` from `story2.txt` and paste it at the bottom of `story1.txt`.

```bash
<ESC>
/Open source
yy
:bp
G
p
```

- [x] Save both files and quit vi.

```bash
<ESC>
wqa
```
