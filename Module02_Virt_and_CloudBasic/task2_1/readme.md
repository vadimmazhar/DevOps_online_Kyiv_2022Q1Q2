#  #####################
#       Task 2.1
# #######################
# PART 2. WORK WITH VIRTUALBOX
## 1. First run VirtualBox and Virtual Machine (VM). 
##   1.1 Get acquainted with the structure of the user manual VirtualBox [1] (see list of references in the end of the document) 
##   1.2 From the official VirtualBox site [2] download the latest stable version of VirtualBox according to the host operating system (OS) installed on the student's workplace. For    ## Windows, the file may be called, for example, VirtualBox-6.1.10-138449-Win.exe. Install VirtualBox. 

![Virtual  Box Install](task2_1_images/image01_task2_1.jpg)

## 1.3 Download the latest stable version of Ubuntu Desktop or Ubuntu Server from the official site [3].  (Oracle Linux Server 7.9)
## 1.4 Create VM1 and install Ubuntu using the instructions [1, chapter 1.8]. Set machine name as "host machine name"_"student last name"

###  Create VM   ep-ol-vm01   and OS  Oracle Linux Server 7.9
![Create VM  ep-ol-vm01](task2_1_images/image02_task2_1.jpg)
![Create VM  ep-ol-vm01 and Install  OS OL 7.9](task2_1_images/image03_task2_1.jpg)
![Running VM  ep-ol-vm01 and  OS OL 7.9](task2_1_images/image04_OSver_task2_1.jpg)

### Create 2 net interfaces 
#### 1st  interfaces type NAT(default) – connect VM to Internet 
![Config 1st interfaces type NAT](task2_1_images/image05_net_task2_1.jpg)
![Configured IF on OS](task2_1_images/image06_net_task2_1.jpg)

## 2nd interface Host-only Adapter  - to connect  Virtualbox Host  with  guest VM
![Configured 2nd interface Host-only](task2_1_images/image07_net_task2_1.jpg)
![Configured 2nd IF on OS](task2_1_images/image08_net_task2_1.jpg)

Ping && ssh connect from Host to VM ep-ol-vm01(192.168.56.101)
![Ping to VM ep-ol-vm01](task2_1_images/image09_net_task2_1.jpg)
![SSH connect VM ep-ol-vm01](task2_1_images/image10_net_task2_1.jpg)

## -- 1.5 Get acquainted with the possibilities of VM1 control - start, stop, reboot, save state, use Host key and keyboard shortcuts, mouse capture, etc. [1, ch.1.9] --
### Create snapshot of VM (https://www.virtualbox.org/manual/ch01.html#snapshots) name “ep-ol-vm01_snapsh_hostname_change_v1”
![Create snapshot of VM ep-ol-vm01 ep-ol-vm01_snapsh_hostname_change_v1](task2_1_images/image11_snapshot_task2_1.jpg)
###  change VM’s hostname 
![change hostname to ep-ol-virtualka01](task2_1_images/image12_snapshot_task2_1.jpg)
###  Restore VM from shapshot ep-ol-vm01_snapsh_hostname_change_v1
![restore from snapshot ](task2_1_images/image13_snapshot_task2_1.jpg)
![restore from snapshot / Host name restore](task2_1_images/image14_snapshot_task2_1.jpg)

##  -- 1.6 Clone an existing VM1 by creating a VM2 [1, ch.1.14] --##
### Clone VM ep-ol-vm01   to  VM ep-ol-vm02
![Clone VM ep-ol-vm01   to  VM ep-ol-vm02 ](task2_1_images/image15_vm_clone_task2_1.jpg)
![Clone VM ep-ol-vm01   to  VM ep-ol-vm02 ](task2_1_images/image16_vm_clone_task2_1.jpg)
![Clone VM ep-ol-vm01   to  VM ep-ol-vm02 ](task2_1_images/image17_vm_clone_task2_1.jpg)

##  1.7 Create a group of two VM: VM1, VM2 and learn the functions related to groups [1, ch.1.10] --(https://www.virtualbox.org/manual/ch01.html#gui-vmgroups)
#### Crete group VM-Group-OL from VM ep-ol-vm01 and VM ep-ol-vm02
![Create a group of two VM: ep-ol-vm01 and VM ep-ol-vm02 ](task2_1_images/image18_vm_group_task2_1.jpg)
### Start VM from group VM-Group-OL
![ Start VM from group VM-Group-OL](task2_1_images/image19_vm_group_task2_1.jpg)
![ Start VM from group VM-Group-OL](task2_1_images/image20_vm_group_task2_1.jpg)

## -- 1.9 Export VM1. Save the .ova file to disk. Import VM from .ova file 
![Export VM1 ](task2_1_images/image21_vmexport_task2_1.jpg)
![Export VM1 ](task2_1_images/image22_vmexport_task2_1.jpg)
![Export VM1 ](task2_1_images/image23_vmexport_task2_1.jpg)
![Export VM1 ](task2_1_images/image24_vmexport_task2_1.jpg)
### --  Import VM from .ova file 
![import VM1](task2_1_images/image25_vm_import_task2_1.jpg)
![import VM1](task2_1_images/image26_vm_import_task2_1.jpg)
![import VM1](task2_1_images/image27_vm_import_task2_1.jpg)

## USB to VM
![USB2VM ](task2_1_images/image28_usb2vm_task2_1.jpg)
![USB2VM ](task2_1_images/image29_usb2vm_task2_1.jpg)

---
```
[root@ep-ol-vm01 vadim]# id
uid=0(root) gid=0(root) groups=0(root) context=unconfined_u:unconfined_r:unconfi                                                                                       ned_t:s0-s0:c0.c1023
[root@ep-ol-vm01 vadim]#
[root@ep-ol-vm01 yum.repos.d]# lsscsi
[1:0:0:0]    cd/dvd  VBOX     CD-ROM           1.0   /dev/sr0
[2:0:0:0]    disk    ATA      VBOX HARDDISK    1.0   /dev/sda   
[3:0:0:0]    disk    JetFlash Transcend 64GB   1100  /dev/sdb  <--!!!
[root@ep-ol-vm01 yum.repos.d]#
[root@ep-ol-vm01 yum.repos.d]# fdisk -l /dev/sdb

Disk /dev/sdb: 60.5 GB, 60472426496 bytes, 118110208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0x49f96372

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       16128   118110207    59047040    7  HPFS/NTFS/exFAT    <--!!!
/dev/sdb4         5539936     6758471      609268    0  Empty
[root@ep-ol-vm01 yum.repos.d]#
]# yum-config-manager --enable oracle-epel-release-el7
[root@ep-ol-vm01 yum.repos.d]# yum install ntfs-3g 

[root@ep-ol-vm01 yum.repos.d]# mount  -t ntfs-3g /dev/sdb1 /mnt/usb01/   <--!!!
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
[root@ep-ol-vm01 yum.repos.d]# df -Th /mnt/usb01/
Filesystem     Type     Size  Used Avail Use% Mounted on   
/dev/sdb1      fuseblk   57G   13G   44G  23% /mnt/usb01    <--!!!
[root@ep-ol-vm01 yum.repos.d]#
[root@ep-ol-vm01 yum.repos.d]# ls -l /mnt/usb01/
total 740
drwxrwxrwx. 1 root root   4096 Aug 28  2019 boot
-rwxrwxrwx. 1 root root 409654 Jul  9  2019 bootmgr
-rwxrwxrwx. 1 root root   2048 Jan 17  2012 default
drwxrwxrwx. 1 root root      0 Aug 28  2019 efi
-rwxrwxrwx. 1 root root 272255 Jul 24  2013 grldr
drwxrwxrwx. 1 root root      0 Aug 28  2019 ISO
-rwxrwxrwx. 1 root root   4252 Sep  3  2019 menu.lst
-rwxrwxrwx. 1 root root  43559 Feb 25  2012 plpbt.bin
-rwxrwxrwx. 1 root root   4365 Aug 22  2013 shifthd.bat
drwxrwxrwx. 1 root root      0 Sep  3  2019 soft
drwxrwxrwx. 1 root root      0 Aug 28  2019 System Volume Information
-rwxrwxrwx. 1 root root      0 Dec 12  2009 usbdrive.tag
drwxrwxrwx. 1 root root      0 Aug 28  2019 WINSETUP
[root@ep-ol-vm01 yum.repos.d]#

[root@ep-ol-vm01 yum.repos.d]# umount /mnt/usb01  <--!!!
[root@ep-ol-vm01 yum.repos.d]#
[root@ep-ol-vm01 yum.repos.d]# df -h
Filesystem           Size  Used Avail Use% Mounted on
devtmpfs             836M     0  836M   0% /dev
tmpfs                850M     0  850M   0% /dev/shm
tmpfs                850M  8.6M  841M   2% /run
tmpfs                850M     0  850M   0% /sys/fs/cgroup
/dev/mapper/ol-root  6.2G  2.2G  4.1G  35% /
/dev/sda1           1014M  192M  823M  19% /boot
tmpfs                170M     0  170M   0% /run/user/1000
[root@ep-ol-vm01 yum.repos.d]#

```
---

##  Work with CLI through VBoxManage. 
---
```
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vboxmanage list vms
"bin_default_1488825039581_84671" {fc542fcd-e6f9-4c7d-8e72-3ebcbebedd6f}
"learning" {2dc3212c-f37a-4929-b97c-aab8ddfd0ca7}
"ep-ol-vm01" {aa20e5de-3175-4a8a-ad6c-282c5e649543}
"ep-ol-vm02" {2790ec5c-2c3a-44c4-9c35-0b434784606b}
"ep-ol-import-vm01" {7df76f9a-208c-4dc9-8ea2-28233fa66c28}
"vvm_vgdata_default_1645113222024_94101" {d9ac2237-a1cc-49d0-85d2-2bc9be17ef75}

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vboxmanage list runningvms
"vvm_vgdata_default_1645113222024_94101" {d9ac2237-a1cc-49d0-85d2-2bc9be17ef75}

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>
```
---
# PART 3. WORK WITH VAGRANT
### Install vagrant and show version
![vagrant version](task2_1_images/image30_vboxmanage_task2_1.jpg)
```
C:\Program Files (x86)\Vagrant\bin>cd C:\Users\Vadim.Mazhar\epam_data\vvm_vgda
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vagrant box list
ubuntu/trusty64 (virtualbox, 20170222.0.1)

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vagrant init hashicorp/precise64    <--!!
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vagrant box list
ubuntu/trusty64 (virtualbox, 20170222.0.1)

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>
```
![vagrant up](task2_1_images/image31_vboxmanage_task2_1.jpg)
![vagrant up](task2_1_images/image32_vboxmanage_task2_1.jpg)

---
## -- 5. Connect to the VM using the program MobaXterm or PuTTY (can be downloaded from [6]), using SSH, IP address and port listed above (127.0.0.1:2222). By default, login - vagrant and password are also vagrant  --##
### Connect use vagrant ssh
```
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vagrant ssh
vagrant@127.0.0.1's password:
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

New release '14.04.6 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Welcome to your Vagrant-built virtual machine.
Last login: Thu Feb 17 16:13:45 2022 from 10.0.2.2
vagrant@precise64:~$
```

### --- Connect from putty 
![vagrant putty](task2_1_images/image33_vboxmanage_task2_1.jpg)

```
login as: vagrant
vagrant@127.0.0.1's password:
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

New release '14.04.6 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Welcome to your Vagrant-built virtual machine.
Last login: Fri Sep 14 06:23:18 2012 from 10.0.2.2
vagrant@precise64:~$
vagrant@precise64:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:27:88:0c:a6
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe88:ca6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:143989 (143.9 KB)  TX bytes:141518 (141.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

## --  6. Record the date and time by executing the date command 

![vagrant datatime](task2_1_images/image34_vboxmanage_datatime_task2_1.jpg)

## -- 7. Stop and delete the created VM. --## 
```
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vagrant halt
==> default: Attempting graceful shutdown of VM...

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>
```

## -- 8. Create your own Vagrant box [7] --## 
## 9. (optional) Create a test environment from a few (ONE)servers. Servers' parameters are chosen independently by the student. (Oracle linux 7.9 OS  for test environment)
### Find Oracle linux box 
### generic/oracle7 Vagrant box   https://app.vagrantup.com/generic/boxes/oracle7
### Init generic/oracle7 Vagrant box 
```
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>mkdir vgbox-ol79

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>cd vgbox-ol79

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>vagrant init generic/oracle7   <-- !!!
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>dir
 Том в устройстве C не имеет метки.
 Серийный номер тома: EE15-49AA

 Содержимое папки C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79

17.02.2022  19:15    <DIR>          .
17.02.2022  19:15    <DIR>          ..
17.02.2022  19:15             3 091 Vagrantfile     !!
               1 файлов          3 091 байт
               2 папок  81 518 989 312 байт свободно

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>
```

![vagrant UP](task2_1_images/image35_vboxmanage_create_new_task2_1.jpg)
```
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>vagrant box list
generic/oracle7     (virtualbox, 3.6.8)
hashicorp/precise64 (virtualbox, 1.1.0)
ubuntu/trusty64     (virtualbox, 20170222.0.1)
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>
```
### Connect with Putty to  127.0.0.1:2222   log:vagrant\pass:vagrant
![vagrant putty](task2_1_images/image36_vboxmanage_create_new_task2_1.jpg)

```
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vagrant halt
==> default: Attempting graceful shutdown of VM...

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>vagrant destroy
    default: Are you sure you want to destroy the 'default' VM? [y/N] y
    default: Are you sure you want to destroy the 'default' VM? [y/N] y
==> default: Destroying VM and associated drives...

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata>cd vgbox-ol79   <---!!!
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>vagrant destroy  <---!
    default: Are you sure you want to destroy the 'default' VM? [y/N] y
==> default: Destroying VM and associated drives...

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>
C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>vboxmanage list vms
"bin_default_1488825039581_84671" {fc542fcd-e6f9-4c7d-8e72-3ebcbebedd6f}
"learning" {2dc3212c-f37a-4929-b97c-aab8ddfd0ca7}
"ep-ol-vm01" {aa20e5de-3175-4a8a-ad6c-282c5e649543}
"ep-ol-vm02" {2790ec5c-2c3a-44c4-9c35-0b434784606b}
"ep-ol-import-vm01" {7df76f9a-208c-4dc9-8ea2-28233fa66c28}

C:\Users\Vadim.Mazhar\epam_data\vvm_vgdata\vgbox-ol79>


```






