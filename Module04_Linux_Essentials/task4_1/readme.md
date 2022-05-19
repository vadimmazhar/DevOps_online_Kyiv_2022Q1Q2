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

## 4) Change personal information about yourself

```
[vadim@ep-ol-vm01 ~]$ sudo usermod -c 'Vadim Original account' vadim
[sudo] password for vadim:
[vadim@ep-ol-vm01 ~]$
[vadim@ep-ol-vm01 ~]$ cat /etc/passwd| grep vadim
vadim:x:1000:1000:Vadim Original account:/home/vadim:/bin/bash

```

## 5) Become familiar with the Linux help system and the man and info commands. Get help on the previously discussed commands, define and describe any two keys for these commands. Give examples.

### [vadim@ep-ol-vm01 ~]$ man usermod
```
USERMOD(8)                                         System Management Commands                                        USERMOD(8)

NAME
       usermod - modify a user account

SYNOPSIS
       usermod [options] LOGIN

DESCRIPTION
       The usermod command modifies the system account files to reflect the changes that are specified on the command line.

OPTIONS
       The options which apply to the usermod command are:

       -a, --append
           Add the user to the supplementary group(s). Use only with the -G option.

       -c, --comment COMMENT
The new value of the user's password file comment field. It is normally modified using the chfn(1) utility.

       -d, --home HOME_DIR
           The user's new login directory.

           If the -m option is given, the contents of the current home directory will be moved to the new home directory, which
           is created if it does not already exist. If the current home directory does not exist the new home directory will not be created.
```

### [vadim@ep-ol-vm01 ~]$ info chage
```
File: *manpages*,  Node: chage,  Up: (dir)

CHAGE(1)                         User Commands                        CHAGE(1)



NAME
       chage - change user password expiry information

SYNOPSIS
       chage [options] LOGIN

DESCRIPTION
       The chage command changes the number of days between password changes
       and the date of the last password change. This information is used by
       the system to determine when a user must change their password.

OPTIONS
       The options which apply to the chage command are:

       -d, --lastday LAST_DAY
           Set the number of days since January 1st, 1970 when the password
           was last changed. The date may also be expressed in the format
           YYYY-MM-DD (or the format more commonly used in your area). If the
           LAST_DAY is set to 0 the user is forced to change his password on
           the next log on.

       -E, --expiredate EXPIRE_DATE
           Set the date or number of days since January 1, 1970 on which the
           user's account will no longer be accessible. The date may also be

```

## 6) Explore the more and less commands using the help system. View the contents of files .bash* using commands.


### [root@ep-ol-vm01 vadim]# more /etc/bashrc
```
# /etc/bashrc

# System wide functions and aliases
# Environment stuff goes in /etc/profile

# It's NOT a good idea to change this file unless you know what you
# are doing. It's much better to create a custom.sh shell script in
# /etc/profile.d/ to make custom changes to your environment, as this
# will prevent the need for merging in future updates.

# are we an interactive shell?
if [ "$PS1" ]; then
  if [ -z "$PROMPT_COMMAND" ]; then
    case $TERM in
    xterm*|vte*)
      if [ -e /etc/sysconfig/bash-prompt-xterm ]; then
          PROMPT_COMMAND=/etc/sysconfig/bash-prompt-xterm
      elif [ "${VTE_VERSION:-0}" -ge 3405 ]; then
          PROMPT_COMMAND="__vte_prompt_command"
      else
          PROMPT_COMMAND='printf "\033]0;%s@%s:%s\007" "${USER}" "${HOSTNAME%%.*}" "${PWD/#$HOME/~}"'
      fi
      ;;
    screen*)
      if [ -e /etc/sysconfig/bash-prompt-screen ]; then
          PROMPT_COMMAND=/etc/sysconfig/bash-prompt-screen
      else
          PROMPT_COMMAND='printf "\033k%s@%s:%s\033\\" "${USER}" "${HOSTNAME%%.*}" "${PWD/#$HOME/~}"'
      fi
      ;;
    *)
      [ -e /etc/sysconfig/bash-prompt-default ] && PROMPT_COMMAND=/etc/sysconfig/bash-prompt-default
      ;;
    esac
  fi
  # Turn on parallel history
  shopt -s histappend
  history -a
  # Turn on checkwinsize
  shopt -s checkwinsize
  [ "$PS1" = "\\s-\\v\\\$ " ] && PS1="[\u@\h \W]\\$ "
  # You might want to have e.g. tty in prompt (e.g. more virtual machines)
--More--(50%)

[root@ep-ol-vm01 vadim]# less .bash_profile
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs

PATH=$PATH:$HOME/.local/bin:$HOME/bin

export PATH
.bash_profile (END)
```

### [root@ep-ol-vm01 vadim]# more  -c -30 /etc/bashrc
```
# /etc/bashrc

# System wide functions and aliases
# Environment stuff goes in /etc/profile

# It's NOT a good idea to change this file unless you know what you
# are doing. It's much better to create a custom.sh shell script in
# /etc/profile.d/ to make custom changes to your environment, as this
# will prevent the need for merging in future updates.

# are we an interactive shell?
if [ "$PS1" ]; then
  if [ -z "$PROMPT_COMMAND" ]; then
    case $TERM in
    xterm*|vte*)
      if [ -e /etc/sysconfig/bash-prompt-xterm ]; then
          PROMPT_COMMAND=/etc/sysconfig/bash-prompt-xterm
      elif [ "${VTE_VERSION:-0}" -ge 3405 ]; then
          PROMPT_COMMAND="__vte_prompt_command"
      else
          PROMPT_COMMAND='printf "\033]0;%s@%s:%s\007" "${USER}" "${HOSTNAME%%.*}" "${PWD/#$HOME/~}"'
      fi
      ;;
    screen*)
      if [ -e /etc/sysconfig/bash-prompt-screen ]; then
          PROMPT_COMMAND=/etc/sysconfig/bash-prompt-screen
      else
          PROMPT_COMMAND='printf "\033k%s@%s:%s\033\\" "${USER}" "${HOSTNAME%%.*}" "${PWD/#$HOME/~}"'
      fi
      ;;
--More--(37%)

```

### 8) * List the contents of the home directory using the ls command, define its files and directories. Hint: Use the help system to familiarize yourself with the ls command.

[root@ep-ol-vm01 vadim]#
### [root@ep-ol-vm01 vadim]# ls -l
```
total 4
-rw-rw-r--. 1 vadim vadim 29 Mar 28 19:29 test_nanofile_1
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]# ls -la
total 28
drwx------. 4 vadim vadim 4096 Mar 28 19:18 .
drwxr-xr-x. 4 root  root    33 Mar 25 23:18 ..
-rw-------. 1 vadim vadim 1671 Apr  1 21:51 .bash_history
-rw-r--r--. 1 vadim vadim   18 Nov 22  2019 .bash_logout
-rw-r--r--. 1 vadim vadim  193 Nov 22  2019 .bash_profile
-rw-r--r--. 1 vadim vadim  231 Nov 22  2019 .bashrc
drwxrwxr-x. 3 vadim vadim   18 Feb 11 18:15 .cache
drwxrwxr-x. 3 vadim vadim   18 Feb 11 18:15 .config
-rw-rw-r--. 1 vadim vadim   29 Mar 28 19:29 test_nanofile_1
-rw-------. 1 vadim vadim  665 Mar 28 19:17 .viminfo
[root@ep-ol-vm01 vadim]#
```
### --- List only directories in /etc   directory 
### [root@ep-ol-vm01 vadim]# ls -ld /etc/*/
```
drwxr-xr-x.  3 root root  101 Feb 10 14:37 /etc/abrt/
drwxr-xr-x.  2 root root 4096 Feb 10 14:39 /etc/alternatives/
drwxr-x---.  3 root root   43 Feb 10 14:39 /etc/audisp/
drwxr-x---.  3 root root   83 Feb 10 14:53 /etc/audit/
drwxr-xr-x.  2 root root   99 Feb 10 14:39 /etc/bash_completion.d/
drwxr-xr-x.  2 root root    6 Oct  2  2020 /etc/binfmt.d/
drwxr-xr-x.  2 root root    6 May 24  2020 /etc/chkconfig.d/
drwxr-xr-x.  2 root root   26 Feb 10 14:39 /etc/cifs-utils/
drwxr-xr-x.  2 root root   54 Feb 10 14:39 /etc/cron.d/
drwxr-xr-x.  2 root root   57 Feb 10 14:39 /etc/cron.daily/
drwxr-xr-x.  2 root root   22 Feb 10 14:37 /etc/cron.hourly/
drwxr-xr-x.  2 root root    6 Apr 29  2014 /etc/cron.monthly/
drwxr-xr-x.  2 root root    6 Apr 29  2014 /etc/cron.weekly/
drwxr-xr-x.  4 root root   78 Feb 10 14:37 /etc/dbus-1/
drwxr-xr-x.  2 root root   44 Feb 10 14:47 /etc/default/
drwxr-xr-x.  2 root root   40 Feb 10 14:37 /etc/depmod.d/
drwxr-x---.  4 root root   53 Feb 10 14:37 /etc/dhcp/
drwxr-xr-x.  2 root root    6 Oct  2  2020 /etc/dracut.conf.d/
drwxr-x---.  7 root root 4096 Feb 10 14:37 /etc/firewalld/
drwxr-xr-x.  2 root root    6 May 26  2017 /etc/gcrypt/
drwxr-xr-x.  2 root root    6 Sep 30  2020 /etc/gdbinit.d/
drwxr-xr-x.  2 root root    6 Jul 11  2018 /etc/gnupg/
drwxr-xr-x.  4 root root   40 Feb 10 14:35 /etc/groff/
drwx------.  2 root root 4096 Feb 10 14:44 /etc/grub.d/
drwxr-xr-x.  3 root root   20 Feb 10 14:36 /etc/gss/
drwxr-xr-x.  2 root root   83 Feb 10 14:37 /etc/init.d/
drwxr-xr-x.  2 root root 4096 Feb 10 14:35 /etc/iproute2/
drwxr-xr-x.  3 root root   24 Feb 10 14:39 /etc/kernel/
drwxr-xr-x.  2 root root    6 Jun  2  2020 /etc/krb5.conf.d/
drwxr-xr-x.  2 root root 4096 Feb 10 14:37 /etc/ld.so.conf.d/
drwxr-xr-x.  2 root root   35 Feb 10 14:35 /etc/libnl/
drwxr-xr-x.  6 root root 4096 Feb 10 14:39 /etc/libreport/
drwxr-xr-x.  2 root root 4096 Feb 10 14:39 /etc/logrotate.d/
drwxr-xr-x.  3 root root   43 Feb 10 14:37 /etc/lsm/
drwxr-xr-x.  6 root root  100 Feb 10 14:37 /etc/lvm/
drwxr-xr-x.  2 root root   81 Feb 10 14:37 /etc/modprobe.d/
drwxr-xr-x.  2 root root    6 Oct  2  2020 /etc/modules-load.d/
drwxr-xr-x.  2 root root   31 Feb 10 14:36 /etc/my.cnf.d/
drwxr-xr-x.  7 root root 4096 Feb 10 14:37 /etc/NetworkManager/
drwxr-xr-x.  2 root root   38 Feb 10 14:39 /etc/ntp/
drwxr-xr-x.  3 root root   36 Feb 10 14:36 /etc/openldap/
drwxr-xr-x.  2 root root    6 Apr 11  2018 /etc/opt/
drwxr-xr-x.  2 root root 4096 Feb 10 14:47 /etc/pam.d/
drwxr-xr-x.  3 root root   21 Feb 10 14:35 /etc/pkcs11/
drwxr-xr-x. 10 root root 4096 Feb 10 14:39 /etc/pki/
drwxr-xr-x.  2 root root   28 Feb 10 14:37 /etc/plymouth/
drwxr-xr-x.  5 root root   52 Feb 10 14:35 /etc/pm/
drwxr-xr-x.  5 root root   72 Feb 10 14:37 /etc/polkit-1/
drwxr-xr-x.  2 root root    6 May  3  2014 /etc/popt.d/
drwxr-xr-x.  2 root root 4096 Feb 10 14:39 /etc/postfix/
drwxr-xr-x.  3 root root 4096 Feb 10 14:37 /etc/ppp/
drwxr-xr-x.  2 root root   78 Feb 10 14:37 /etc/prelink.conf.d/
drwxr-xr-x.  2 root root 4096 Feb 10 14:39 /etc/profile.d/
drwxr-xr-x.  2 root root   35 Feb 10 14:36 /etc/python/
drwxr-xr-x.  3 root root   50 Feb 10 14:39 /etc/qemu-ga/
drwxr-xr-x.  2 root root   61 Feb 10 14:37 /etc/rc0.d/
drwxr-xr-x.  2 root root   61 Feb 10 14:37 /etc/rc1.d/
drwxr-xr-x.  2 root root   61 Feb 10 14:37 /etc/rc2.d/
drwxr-xr-x.  2 root root   61 Feb 10 14:37 /etc/rc3.d/
drwxr-xr-x.  2 root root   61 Feb 10 14:37 /etc/rc4.d/
drwxr-xr-x.  2 root root   61 Feb 10 14:37 /etc/rc5.d/
drwxr-xr-x.  2 root root   61 Feb 10 14:37 /etc/rc6.d/
drwxr-xr-x. 10 root root 4096 Feb 10 14:36 /etc/rc.d/
drwxr-xr-x.  2 root root   66 Feb 10 14:37 /etc/rpm/
drwxr-xr-x.  2 root root   25 Oct  1  2020 /etc/rsyslog.d/
drwxr-xr-x.  2 root root   23 Oct  1  2020 /etc/rwtab.d/
drwxr-xr-x.  2 root root   24 Feb 10 14:39 /etc/sasl2/
drwxr-xr-x.  3 root root   34 Feb 10 14:39 /etc/scl/
drwxr-xr-x.  6 root root 4096 Feb 10 14:36 /etc/security/
drwxr-xr-x.  5 root root   81 Feb 10 14:37 /etc/selinux/
drwxr-xr-x.  2 root root 4096 Feb 10 14:37 /etc/setuptool.d/
drwxr-xr-x.  2 root root   62 Feb 10 14:35 /etc/skel/
drwxr-xr-x.  3 root root   74 Feb 10 14:39 /etc/smartmontools/
drwxr-xr-x.  2 root root 4096 Feb 10 14:53 /etc/ssh/
drwxr-xr-x.  2 root root   19 Feb 10 14:35 /etc/ssl/
drwxr-xr-x.  2 root root    6 Oct  1  2020 /etc/statetab.d/
drwxr-x---.  2 root root    6 May 24  2020 /etc/sudoers.d/
drwxr-xr-x.  7 root root 4096 Feb 10 14:49 /etc/sysconfig/
drwxr-xr-x.  2 root root   28 Feb 10 14:37 /etc/sysctl.d/
drwxr-xr-x.  4 root root 4096 Feb 10 14:36 /etc/systemd/
drwxr-xr-x.  2 root root    6 Sep  5  2017 /etc/terminfo/
drwxr-xr-x.  2 root root    6 Oct  2  2020 /etc/tmpfiles.d/
drwxr-xr-x.  3 root root 4096 Feb 10 14:37 /etc/tuned/
drwxr-xr-x.  3 root root   54 Feb 10 14:53 /etc/udev/
drwxr-xr-x.  2 root root   33 Feb 10 14:37 /etc/wpa_supplicant/
drwxr-xr-x.  5 root root   57 Feb 10 14:36 /etc/X11/
drwxr-xr-x.  4 root root   38 Feb 10 14:36 /etc/xdg/
drwxr-xr-x.  2 root root    6 Apr 11  2018 /etc/xinetd.d/
drwxr-xr-x.  6 root root  100 Feb 10 14:36 /etc/yum/
drwxr-xr-x.  2 root root  101 Feb 13 22:52 /etc/yum.repos.d/
[root@ep-ol-vm01 vadim]#
```

# Task1.Part2
## 1) Examine the tree command. Master the technique of applying a template, for example, display all files that contain a character c, or files that contain a specific sequence of characters. List subdirectories of the root directory up to and including the second nesting level.

### [root@ep-ol-vm01 vadim]# tree   /home
```
/home
├── vadim
│   └── test_nanofile_1
└── vadim2

2 directories, 1 file
[root@ep-ol-vm01 vadim]#

[root@ep-ol-vm01 vadim]# tree   -a /home
/home
├── vadim
│   ├── .bash_history
│   ├── .bash_logout
│   ├── .bash_profile
│   ├── .bashrc
│   ├── .cache
│   │   └── abrt
│   │       └── lastnotification
│   ├── .config
│   │   └── abrt
│   ├── test_nanofile_1
│   └── .viminfo
└── vadim2
    ├── .bash_history
    ├── .bash_logout
    ├── .bash_profile
    ├── .bashrc
    ├── .cache
    │   └── abrt
    │       └── lastnotification
    └── .config
        └── abrt

10 directories, 12 files
[root@ep-ol-vm01 vadim]#
```
### -- Print only DIR
### [root@ep-ol-vm01 vadim]# tree -d  /home
/home
├── vadim
└── vadim2

2 directories
[root@ep-ol-vm01 vadim]#


### -- tree : display full  path for each files

### [root@ep-ol-vm01 vadim]# tree   -f  /home
/home
├── /home/vadim
│   └── /home/vadim/test_nanofile_1
└── /home/vadim2

2 directories, 1 file
[root@ep-ol-vm01 vadim]#


### --- Display hierarchy level 2 directories  use  –L 2

[root@ep-ol-vm01 vadim]# tree   -L 2 -d   /var
/var
├── account
├── adm
├── cache
│   ├── abrt-di
│   ├── ldconfig
│   ├── man
│   └── yum
├── crash
├── db
│   └── sudo
├── empty
│   └── sshd
├── games
├── gopher
├── kerberos
│   └── krb5
├── lib
│   ├── alternatives
│   ├── authconfig
│   ├── chrony
│   ├── dbus
│   ├── dhclient
│   ├── fprint
│   ├── games
│   ├── initramfs
│   ├── logrotate
│   ├── machines
│   ├── misc
│   ├── mlocate
│   ├── NetworkManager
│   ├── os-prober
│   ├── plymouth
│   ├── polkit-1
│   ├── postfix
│   ├── rpcbind
│   ├── rpm
│   ├── rpm-state
│   ├── rsyslog
│   ├── stateless
│   ├── systemd
│   ├── tuned
│   ├── up2date
│   └── yum
├── local
├── lock -> ../run/lock
├── log
│   ├── anaconda
│   ├── audit
│   ├── chrony
│   ├── qemu-ga
│   ├── sa
│   └── tuned
├── mail -> spool/mail
├── nis
├── opt
├── preserve
├── run -> ../run
├── spool
│   ├── abrt
│   ├── abrt-upload
│   ├── anacron
│   ├── at
│   ├── cron
│   ├── lpd
│   ├── mail
│   ├── plymouth
│   ├── postfix
│   └── up2date
├── tmp
│   └── abrt
└── yp

71 directories
[root@ep-ol-vm01 vadim]#

### --- list directory with name start from cron in /var file system
[root@ep-ol-vm01 var]# tree --prune -P 'cron*' /var/
/var/
├── log
│   ├── cron
│   ├── cron-20220213
│   ├── cron-20220321
│   └── cron-20220401
└── spool
    └── anacron
        ├── cron.daily
        ├── cron.monthly
        └── cron.weekly

3 directories, 7 files
[root@ep-ol-vm01 var]#

## 2) What command can be used to determine the type of file (for example, text or binary)? Give an example.


[root@ep-ol-vm01 vadim]# file /etc/bashrc
/etc/bashrc: ASCII text
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]# file /etc/hosts
/etc/hosts: ASCII text
[root@ep-ol-vm01 vadim]#
 [root@ep-ol-vm01 vadim]# which  df
/bin/df
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 vadim]# file /bin/df
/bin/df: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.32, BuildID[sha1]=cf7a8573245de196253ca1027014846a34e79e0d, stripped
[root@ep-ol-vm01 vadim]#

##  3) Master the skills of navigating the file system using relative and absolute paths. How can you go back to your home directory from anywhere in the filesystem?
### navigate use absolute path
### [root@ep-ol-vm01 vadim]# cd /var/log/sa
[root@ep-ol-vm01 sa]#

[root@ep-ol-vm01 sa]# pwd
/var/log/sa
[root@ep-ol-vm01 sa]#

### navigate use relative path 
### [root@ep-ol-vm01 sa]# cd ../../spool/cron/
[root@ep-ol-vm01 cron]# 

[vadim@ep-ol-vm01 ~]$ cd /etc/
[vadim@ep-ol-vm01 etc]$ cd ssh/
[vadim@ep-ol-vm01 ssh]$
[vadim@ep-ol-vm01 ssh]$ pwd
/etc/ssh
[vadim@ep-ol-vm01 ssh]$ cd ../opt/
[vadim@ep-ol-vm01 opt]$ pwd
/etc/opt
[vadim@ep-ol-vm01 opt]$ 

### go back to home 
[vadim@ep-ol-vm01 opt]$ id
uid=1000(vadim) gid=1000(vadim) groups=1000(vadim),10(wheel) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

### [vadim@ep-ol-vm01 opt]$ cd ~/
[vadim@ep-ol-vm01 ~]$ pwd
/home/vadim
[vadim@ep-ol-vm01 ~]$



## 4) Become familiar with the various options for the ls command. Give examples of listing directories using different keys. Explain the information displayed on the terminal using the -l and -a switches.



### ----long list format 
[root@ep-ol-vm01 ~]# ls -l /etc/
total 1192
drwxr-xr-x.  3 root root      101 Feb 10 14:37 abrt
-rw-r--r--.  1 root root       16 Feb 10 14:47 adjtime
-rw-r--r--.  1 root root     1529 Nov 22  2019 aliases
-rw-r--r--.  1 root root    12288 Feb 10 14:53 aliases.db
drwxr-xr-x.  2 root root     4096 Feb 10 14:39 alternatives
-rw-------.  1 root root      541 Jun  9  2019 anacrontab
-rw-r--r--.  1 root root       55 Jun  9  2019 asound.conf
-rw-r--r--.  1 root root        1 Aug 24  2018 at.deny
drwxr-x---.  3 root root       43 Feb 10 14:39 audisp
drwxr-x---.  3 root root       83 Feb 10 14:53 audit
drwxr-xr-x.  2 root root       99 Feb 10 14:39 bash_completion.d
-rw-r--r--.  1 root root     2853 Nov 22  2019 bashrc
drwxr-xr-x.  2 root root        6 Oct  2  2020 binfmt.d


### ---- long list without group
[root@ep-ol-vm01 ~]# ls -o /etc/
total 1192
drwxr-xr-x.  3 root    101 Feb 10 14:37 abrt
-rw-r--r--.  1 root     16 Feb 10 14:47 adjtime
-rw-r--r--.  1 root   1529 Nov 22  2019 aliases
-rw-r--r--.  1 root  12288 Feb 10 14:53 aliases.db
drwxr-xr-x.  2 root   4096 Feb 10 14:39 alternatives
-rw-------.  1 root    541 Jun  9  2019 anacrontab
-rw-r--r--.  1 root     55 Jun  9  2019 asound.conf
-rw-r--r--.  1 root      1 Aug 24  2018 at.deny
drwxr-x---.  3 root     43 Feb 10 14:39 audisp
drwxr-x---.  3 root     83 Feb 10 14:53 audit
drwxr-xr-x.  2 root     99 Feb 10 14:39 bash_completion.d
-rw-r--r--.  1 root   2853 Nov 22  2019 bashrc
drwxr-xr-x.  2 root      6 Oct  2  2020 binfmt.d

### --- list INODES
[root@ep-ol-vm01 ~]# ls -i /etc/
 9737017 abrt                       296392 iproute2                   8427424 rc4.d
 9589061 adjtime                   8389529 issue                      8427425 rc5.d
 8389537 aliases                   8389530 issue.net                  8427426 rc6.d
 9795501 aliases.db                9701137 kdump.conf                17168134 rc.d
  294629 alternatives              9915223 kernel                     9588581 rc.local
 9588991 anacrontab                8401088 krb5.conf                  8389533 redhat-r


### --- list directories only 
```
[root@ep-ol-vm01 ~]# ls -d /etc/
/etc/
[root@ep-ol-vm01 ~]# ls -d /etc/*/
/etc/abrt/               /etc/firewalld/     /etc/modules-load.d/  /etc/qemu-ga/      /etc/smartmontools/
/etc/alternatives/       /etc/gcrypt/        /etc/my.cnf.d/        /etc/rc0.d/        /etc/ssh/
/etc/audisp/             /etc/gdbinit.d/     /etc/NetworkManager/  /etc/rc1.d/        /etc/ssl/
/etc/audit/              /etc/gnupg/         /etc/ntp/             /etc/rc2.d/        /etc/statetab.d/
/etc/bash_completion.d/  /etc/groff/         /etc/openldap/        /etc/rc3.d/        /etc/sudoers.d/
/etc/binfmt.d/           /etc/grub.d/        /etc/opt/             /etc/rc4.d/        /etc/sysconfig/
/etc/chkconfig.d/        /etc/gss/           /etc/pam.d/           /etc/rc5.d/        /etc/sysctl.d/
/etc/cifs-utils/         /etc/init.d/        /etc/pkcs11/          /etc/rc6.d/        /etc/systemd/
/etc/cron.d/             /etc/iproute2/      /etc/pki/             /etc/rc.d/         /etc/terminfo/
/etc/cron.daily/         /etc/kernel/        /etc/plymouth/        /etc/rpm/          /etc/tmpfiles.d/
/etc/cron.hourly/        /etc/krb5.conf.d/   /etc/pm/              /etc/rsyslog.d/    /etc/tuned/
/etc/cron.monthly/       /etc/ld.so.conf.d/  /etc/polkit-1/        /etc/rwtab.d/      /etc/udev/
/etc/cron.weekly/        /etc/libnl/         /etc/popt.d/          /etc/sasl2/        /etc/wpa_supplicant/
/etc/dbus-1/             /etc/libreport/     /etc/postfix/         /etc/scl/          /etc/X11/
/etc/default/            /etc/logrotate.d/   /etc/ppp/             /etc/security/     /etc/xdg/
/etc/depmod.d/           /etc/lsm/           /etc/prelink.conf.d/  /etc/selinux/      /etc/xinetd.d/
/etc/dhcp/               /etc/lvm/           /etc/profile.d/       /etc/setuptool.d/  /etc/yum/
/etc/dracut.conf.d/      /etc/modp
```

### ----list in colum 
[vadim@ep-ol-vm01 ~]$ ls -1 /etc/
abrt
adjtime
aliases
aliases.db
alternatives
anacrontab
asound.conf
at.deny
audisp
audit
bash_completion.d
bashrc
binfmt.d
chkconfig.d
chrony.conf
chrony.keys
cifs-utils
cron.d
cron.daily
cron.deny
