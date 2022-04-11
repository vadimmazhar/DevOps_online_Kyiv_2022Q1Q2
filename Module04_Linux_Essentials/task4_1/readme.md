# Task1.Part1
### 1) Log in to the system as root (or sudo-er). 
### 2) Use the passwd command to change the password. Examine the basic parameters of the command. What system file does it change *? 

```
login as: Vadim
vadim@192.168.56.101's password:
Last failed login: Fri Mar 25 23:00:35 EET 2022 from 192.168.56.1 on ssh:notty
There were 2 failed login attempts since the last successful login.
Last login: Thu Mar 24 19:41:26 2022

[vadim@ep-ol-vm01 ~]$ sudo -s
[sudo] password for vadim:
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]# id
uid=0(root) gid=0(root) groups=0(root) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]# passwd vadim
Changing password for user vadim.
New password:
BAD PASSWORD: The password fails the dictionary check - it is based on a dictionary word
Retype new password:
passwd: all authentication tokens updated successfully.
[root@ep-ol-vm01 vadim]#

[root@ep-ol-vm01 vadim]# passwd vadim
Changing password for user vadim.
New password:
BAD PASSWORD: The password fails the dictionary check - it is based on a dictionary word
Retype new password:
passwd: all authentication tokens updated successfully.
[root@ep-ol-vm01 vadim]#

```
####  Lock  user password  “-l”  && Unlock user password “-u”
```
[root@ep-ol-vm01 vadim]# passwd -l vadim2
Locking password for user vadim2.
passwd: Success
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]# cat /etc/shadow| grep vadim2
vadim2:!!$6$DxmtCv/E$f.F7.yLPsMXsOT0ZgZZOUNFCT/MAabxzonjVG6PxGZ6AA2ujmP3STgvwv3zkmAgQloV9i2YUTPPq15iMzQFHm1:19076:0:99999:7:::
[root@ep-ol-vm01 vadim]#

```
```
[root@ep-ol-vm01 vadim]# passwd -u vadim2
Unlocking password for user vadim2.
passwd: Success
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]# cat /etc/shadow| grep vadim2
vadim2:$6$DxmtCv/E$f.F7.yLPsMXsOT0ZgZZOUNFCT/MAabxzonjVG6PxGZ6AA2ujmP3STgvwv3zkmAgQloV9i2YUTPPq15iMzQFHm1:19076:0:99999:7:::
[root@ep-ol-vm01 vadim]#
```

#### Delete user password 
```
-d, --delete  This  is a quick way to delete a password for an account. It will set the named account passwordless. Available to root only.

[root@ep-ol-vm01 vadim]# cat /etc/shadow| grep vadim2
vadim2:$6$DxmtCv/E$f.F7.yLPsMXsOT0ZgZZOUNFCT/MAabxzonjVG6PxGZ6AA2ujmP3STgvwv3zkmAgQloV9i2YUTPPq15iMzQFHm1:19076:0:99999:7:::
[root@ep-ol-vm01 vadim]#
 [root@ep-ol-vm01 vadim]# passwd -d vadim2     <-!!!
Removing password for user vadim2.
passwd: Success
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]# cat /etc/shadow| grep vadim2
vadim2::19076:0:99999:7:::
[root@ep-ol-vm01 vadim]#
```

## 3) Determine the users registered in the system, as well as what commands they execute. What additional information can be gleaned from the command execution?
```
[vadim@ep-ol-vm01 ~]$ cut -d : -f 1 /etc/passwd
root
bin
daemon
adm
lp
sync
shutdown
halt
mail
operator
games
ftp
nobody
systemd-network
dbus
polkitd
libstoragemgmt
rpc
abrt
sshd
postfix
chrony
ntp
tcpdump
vadim
vadim2
[vadim@ep-ol-vm01 ~]$

[vadim@ep-ol-vm01 ~]$ id
uid=1000(vadim) gid=1000(vadim) groups=1000(vadim),10(wheel) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
[vadim@ep-ol-vm01 ~]$
[vadim@ep-ol-vm01 ~]$ su - vadim2
Last login: Fri Mar 25 23:41:58 EET 2022 from 192.168.56.1 on pts/4
Last failed login: Fri Mar 25 23:48:00 EET 2022 from 192.168.56.1 on ssh:notty
There were 5 failed login attempts since the last successful login.
[vadim2@ep-ol-vm01 ~]$
[vadim2@ep-ol-vm01 ~]$
[vadim2@ep-ol-vm01 ~]$ id
uid=1001(vadim2) gid=1001(vadim2) groups=1001(vadim2) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
[vadim2@ep-ol-vm01 ~]$
[vadim2@ep-ol-vm01 ~]$
[vadim2@ep-ol-vm01 ~]$ history
    1  [root@ep-ol-vm01 vadim]# cat /etc/shadow| grep vadim2
    2  vadim2:$6$DxmtCv/E$f.F7.yLPsMXsOT0ZgZZOUNFCT/MAabxzonjVG6PxGZ6AA2ujmP3STgvwv3zkmAgQloV9i2YUTPPq15iMzQFHm1:19076:0:99999:7:::
    3  [root@ep-ol-vm01 vadim]#
    4  [root@ep-ol-vm01 vadim]# passwd -d vadim2
    5  Removing password for user vadim2.
    6  passwd: Success
    7  [root@ep-ol-vm01 vadim]#
    8  [root@ep-ol-vm01 vadim]# cat /etc/shadow| grep vadim2
    9  vadim2::19076:0:99999:7:::
   10  [root@ep-ol-vm01 vadim]#
   11  passwd vadim2
   12  passwd
   13  passwd -k
   14  id
   15  history
[vadim2@ep-ol-vm01 ~]$


[vadim2@ep-ol-vm01 ~]$ type passwd
passwd is /bin/passwd
[vadim2@ep-ol-vm01 ~]$
[vadim2@ep-ol-vm01 ~]$ type echo
echo is a shell builtin
[vadim2@ep-ol-vm01 ~]$

[vadim@ep-ol-vm01 ~]$ su - vadim2
Last login: Sun Mar 27 08:43:10 EEST 2022 on pts/0
[vadim2@ep-ol-vm01 ~]$
[vadim2@ep-ol-vm01 ~]$ history
    1  [root@ep-ol-vm01 vadim]# cat /etc/shadow| grep vadim2
    2  vadim2:$6$DxmtCv/E$f.F7.yLPsMXsOT0ZgZZOUNFCT/MAabxzonjVG6PxGZ6AA2ujmP3STgvwv3zkmAgQloV9i2YUTPPq15iMzQFHm1:19076:0:99999:7:::
    3  [root@ep-ol-vm01 vadim]#
    4  [root@ep-ol-vm01 vadim]# passwd -d vadim2
    5  Removing password for user vadim2.
    6  passwd: Success
    7  [root@ep-ol-vm01 vadim]#
    8  [root@ep-ol-vm01 vadim]# cat /etc/shadow| grep vadim2
    9  vadim2::19076:0:99999:7:::
   10  [root@ep-ol-vm01 vadim]#
   11  passwd vadim2
   12  passwd
   13  passwd -k
   14  id
   15  history
   16  type passwd
   17  type echo
   18  exit
   19  history
[vadim2@ep-ol-vm01 ~]$

```





