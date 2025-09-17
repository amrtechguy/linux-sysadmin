# LINUX: PRINTING

**Notes**
- character-based vs graphical-based printers.
- some of control codes or the ascii chars (0-31) used to control the printer.
- send text to print as stream of bytes.
- send PostScript file to the printer to interpret and print.
- CUPS (Common Unix Printing System) is the prinitng system for Linux and includes `lp`, `lpr`, `lpq`, `lprm`, `cancel`.

## Stat

**lpstat**

```bash
# cups status
lpstat

# list printers
lpstat -a

# print system
lpstat -s
```

## Prepare and Print

**pr**

```bash
# prepare text for printing
pr -w 65 -l 66 article.txt
```

**lpr**

```bash
# send paginated text to printer
pr -w 65 -l 66 article.txt | lpr

# use specific printer
pr -w 65 -l 66 article.txt | lpr -P printer_name
```

**lp**

```bash
# send paginated text to printer
pr -w 65 -l 66 article.txt | lp
```

**a2ps**

```bash
# convert and print
a2ps -o article.ps

# convert text into PostScript format
cat article.txt | a2ps -o article.ps
```

## Monitor and Control

**lpq**

```bash
# printer queue
lpq
```

**lprm**

```bash
# cancel all print jobs
lprm -

# cancel specific printer
lprm -P <destination>
```

**cancel**

```bash
# cancel
cancel <print-job-id>
```
