# Networking

## Examine & Monitor

```bash
ping www.google.com # ICMP ECHO_REQUEST

tracepath www.google.com
traceroute www.google.com
traceroute -I www.google.com # ICMP
traceroute -T www.google.com # TCP

ip a # replacement to `ifconfig`

sudo apt install net-tools
netstat -ie # network interfaces info
netstat -r # routing table
```

## Transporting Files

```bash
ftp

lftp # better ftp

wget -O example.html https://example.com
```

## Secure Communication with Remote Hosts

```bash
ssh user@host
ssh user@host 'ls -alh' > host_ls.txt
ssh -X user@host
ssh -Y user@host

scp user@host:.bashrc . # uses ssh, similar to cp

sftp user@host # uses ssh, same ftp commands
```

## Notes

```bash
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:ff:cb:90 brd ff:ff:ff:ff:ff:ff
    altname enp2s1
    altname enx000c29ffcb90
    inet 192.168.245.128/24 brd 192.168.245.255 scope global dynamic noprefixroute ens33
       valid_lft 1323sec preferred_lft 1323sec
    inet6 fe80::20c:29ff:feff:cb90/64 scope link proto kernel_ll 
       valid_lft forever preferred_lft forever
```

- `lo` -> virtual interface for the system to talk to itself.
- `up` -> the network interface is enabled.

## Gaps
- [ ] What are the networking config files? and how to read and modify them? 
- [ ] Does `hops` mean routers only?
- [ ] Understand this routing table.

```bash
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         _gateway        0.0.0.0         UG        0 0          0 ens33
192.168.245.0   0.0.0.0         255.255.255.0   U         0 0          0 ens33
```

- [ ] How to list open ports and connected services?
- [ ] How to open/close ports?