# How To?

- [x] Extract a specific field of each line.

```bash
cut -d ':' -f 1 < /etc/passwd
cat /etc/passwd | cut -d ':' -f 1
```

- [x] List only files, dirs, or links.

```bash
find ~/data/*.bak -maxdepth 1 -type f
```

- [x] Using xargs to pass args.

```bash
find /etc/*disk* -maxdepth 1 -type f -print0 | xargs -0 ls -l
```

