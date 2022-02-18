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
![restore fron snapshot ](task2_1_images/image13_snapshot_task2_1.jpg)
![restore from snapshot / Host name restore](task2_1_images/image14_snapshot_task2_1.jpg)




