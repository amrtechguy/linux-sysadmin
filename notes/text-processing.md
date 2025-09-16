# Text Processing

## Notes
- ...

## cat, sort, uniq

```bash
# create a file + content
cat > foo.txt
    The quick brown fox jumped over the lazy dog. 
<CTRL-D>
cat -A foo.txt

ls /usr/bin > bin.txt
cat -ns bin.txt

du -s /var/log/*log* | sort -nr | head
ls -l /var/log/*log* | sort -nrk 5 | head

cat > distros.txt
SUSE 10.2 12/07/2006
Fedora 10 11/25/2008
SUSE 11.0 06/19/2008
Ubuntu 8.04 04/24/2008
Fedora 8 11/08/2007
SUSE 10.3 10/04/2007
Ubuntu 6.10 10/26/2006
Fedora 7 05/31/2007
Ubuntu 7.10 10/18/2007
Ubuntu 7.04 04/19/2007
SUSE 10.1 05/11/2006
Fedora 6 10/24/2006
Fedora 9 05/13/2008
Ubuntu 6.06 06/01/2006
Ubuntu 8.10 10/30/2008
Fedora 5 03/20/2006
<CTRL-D>

sort -k 1,1 -k 2n distros.txt
sort -k 3.7nbr -k 3.1nbr -k 3.4nbr distros.txt

head /etc/passwd | sort -t ':' -k 7

cat > usernames.txt
adam
samy
sarah
muhammed
adam
samy
adam
Adam
<CTRL-D>

sort usernames.txt | uniq -i
sort -fu usernames.txt
```

## slicing and dicing: cut, paste, join

```bash
expand distros.txt | cut -d ' ' -f 3 | cut -c 7-10
expand distros.txt | cut -d ' ' -f 3 | cut -d '/' -f 1,3

sort -k 3.7nbr -k 3.1nbr -k 3.4nbr distros.txt  > distros_by_date.txt
cut -d ' ' -f 1,2 distros_by_date.txt > distros_versions.txt
cut -d ' ' -f 3 distros_by_date.txt > distros_dates.txt
paste -d ' ' distros_dates.txt distros_versions.txt

paste -d ' ' distros_dates.txt distros_names.txt > distros_key_names.txt
paste -d ' ' distros_vernums.txt distros_dates.txt > distros_key_vernums.txt
join -i -1 1 -2 2 distros_key_names.txt distros_key_vernums.txt
```

## Comparing text: comm, diff, patch

```bash
comm file1.txt file2.txt # compare sorted files

diff -c file.conf.bak file.conf # context format
diff -u file.conf.bak file.conf # unified format

diff -Naur .profile.bak .profile > patchfile.txt # diff file
patch < patchfile.txt # updates .profile.bak
```

## Editing on the fly: tr, sed, aspell

```bash
cat > topic.txt
tr—Transliterate or Delete Characters
The	tr	program is used to transliterate characters. We can think of this as a
sort of character-based search-and-replace operation. Transliteration is the
process of changing characters from one alphabet to another. For example,
converting characters from lowercase to uppercase is transliteration.
Numbers:	225896654-85596-114568
<CTRL-D>

# tr
cat topic.txt | tr [0-9] '*'
cat topic.txt | tr [:digit:] \*
cat topic.txt | tr 0123456789 \*
cat topic.txt | tr '\t' ' '
cat topic.txt | tr -d '\r'

cat topic.txt | tr a-zA-Z n-za-mN-ZA-M > rot13.txt
cat rot13.txt | tr a-zA-Z n-za-mN-ZA-M

# sed
sed '1,5s/tr/********/' topic.txt
sed 'y/S/X/' distros.txt # tr
sed '/SUSE/p' # grep
grep -E '[0-9]{2}/[0-9]{2}/[0-9]{4}$' distros.txt
sed 's/\([0-9]\{2\}\)\/\([0-9]\{2\}\)\/\([0-9]\{4\}\)$/\3-\1-\2/g' distros.txt # 12/07/2006 -> 2006-12-07
sed 's/\([0-9]\{2\}\)\/\([0-9]\{2\}\)\/\([0-9]\{4\}\)$/\3-\1-\2/g' distros.txt | sed 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/'
sed 's/SUSE/SUSe/' distros.txt

# aspell
aspell check article.txt
aspell -H check index.html 
```

## Gaps
- [ ] Does <CTRL-D> send a signal to the `shell` or the `command` for `EOF` character?
- [ ] What is `b` used for in `sort -k 3.7nb -k 3.1nb -k 3.4nb distros.txt`?
- [ ] Does `n` in `3.7nb` stop the sorting at `/` in `SUSE 10.2 12/07/2006`?
- [ ] `comm` practical examples.