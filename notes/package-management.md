# Package Management

## Notes
- Major packaging systems: 
    - `debian-style`: `.deb` → Debian, Ubuntu, Linux Mint.
        - low-level tool: `dpkg`
        - high-level tools: `apt-get`, `apt`, `aptitude`
    - `red hat-style`: `.rpm` → Red Hat Enterprise, Fedora, CentOS, OpenSUSE.
        - low-level tool: `rpm`
        - high-level tools: `yum`, `dnf`
- Package:
    - content → `compiled program`, `data files`, `metadata`.
    - maintainer → who builds the package + modifies the source code when needed.
    - upstream provider → the author of the source code.

## Subtopic Title

```bash
# Note: All focus for now on Debian-style packaging system

# update & upgrade → repo
apt-get update && apt-get upgrade
apt update && apt upgrade
# search → repo
apt-cache search plocate
apt search plocate
# install → repo
apt-get install plocate
apt install plocate
# install → package file
# Note: does not handle dependency resolution
dpkg -i package.deb
# remove
apt-get remove plocate
apt remove plocate
# upgrade → not from repo
dpkg -i package.deb
# list
dpkg -l
# pkg status  
dpkg -s plocate
apt-cache show plocate
apt show plocate
# which pkg(s) owning file(s)
dpkg -S file_name
```

## Gaps
- [ ] `apt-get` vs `apt`.
- [ ] Can I remove a package installed by `dpkg` by `apt` or the opposite?