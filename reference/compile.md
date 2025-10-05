# LINUX: COMPILE

**Notes**
- Tools: `gcc`, `make`.

## Source Code

```bash
# download
wget https://ftp.gnu.org/gnu/diction/diction-1.11.tar.gz

# check contents
tar -tzvf diction-1.11.tar.gz

# decompress, extract
tar -xzf diction-1.11.tar.gz
```

## Compile, Install

```bash
# generate Makefile
./configure

# compile, link
make Makefile

# install on system -> /usr/local/bin
make install
```
