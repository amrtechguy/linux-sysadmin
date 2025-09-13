# Regular Expressions

## Notes
- Regex: `metacharacters` vs `literals`.
- Regex:`basic regular expressions` -> `^$.[]*` vs `extended regular expressions` -> `(){}?+|`

## grep

```bash
ls /usr/bin bin.txt
ls /usr/sbin sbin.txt

grep -n zip bin.txt sbin.txt
grep -n zip *bin.txt

grep '^$' *bin.txt # blank lines
grep '^l..ht$' /usr/share/dict/american-english

grep '[bg]zip' *bin.txt
grep '[^bg]zip' *bin.txt
grep '[b^g]zip' *bin.txt

grep '[a-z]zip' *bin.txt
grep '[-az]zip' *bin.txt

locale
export LANG=POSIX

grep -E '^(gz|bz)' *bin.txt # Extended Regex

zgrep -Eil 'regex|regular expression' /usr/share/man/man1/*.gz
```

## Examples

### find malformed phone numbers 

***phonelist.txt***

```bash
(232) 298-2265
(624) 381-1078
(540) 126-1980
(874) 163-2885
(286) 254-2860
(458) 273-1642
(686) 299-8268
(198) 307-2440
```

```bash
grep -vE '^\([0-9]{3}\) [0-9]{3}-[0-9]{4}$' phonelist.txt
```

### find ugly filenames with find

```bash
find . -regex '.*[^-_./a-zA-Z0-9].*' # find's regex -> full path
```

### searching for files with locate

```bash
locate --regex 'bin/(bz|gz|zip)' # locate's regex -> partial path
```

## Gaps
- [ ] `ascii` vs `utf-8`.