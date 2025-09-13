# Text Processing

## Notes
- ...

## cat

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
nour
muhammed
adam
samy
adam
Adam
<CTRL-D>

sort usernames.txt | uniq -i
sort -fu usernames.txt
```

## Gaps
- [ ] Does <CTRL-D> send a signal to the `shell` or the `command` for `EOF` character?
- [ ] What is `b` used for in `sort -k 3.7nb -k 3.1nb -k 3.4nb distros.txt`?
- [ ] Does `n` in `3.7nb` stop the sorting at `/` in `SUSE 10.2 12/07/2006`?