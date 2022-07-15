# ##################################
# Final task of Epam devops cource #
# ##################################
----
## ----- Targets of final task ----
  ### - Create WEB infrastructure for test and production 
  ### - Delivery website into WEB infrastructure 
  
## ---- Tools and Environment  used in Final tasks
   ### VirtualBox VM, AWS, Docker, Ansible, Jenkins, Terraform, Git
  
##  ----------  Infrastructure description  -------#
### ep-ol-vmain01  (192.168.56.110) – Main host using for deploy  infrastructure and control CI/CD
### ep-ol-vmtst01  (192.168.56.121) – test  environment to check changes on website 
### websrv-prod (ip_after_create)   - Productive environment VM in AWS cloud  to  run website

----
## --- 1 Create WEB infrastructure for test and production  ---##
###  -- 1.1 Create Main VM in VirtualBox from   OFV  image  CPU -2  Memory 4096MB
````
C:\Windows\System32>vboxmanage import C:\DATA\VMs\template-vm\vbox\ep-ol-mainvm-template\ep-ol-vm02_mainvm-template.ovf --vsys 0 --vmname "ep-ol-mainvm01" --cpus 2 --memory 4096
C:\Windows\System32>vboxmanage list vms
"bin_default_1488825039581_84671" {fc542fcd-e6f9-4c7d-8e72-3ebcbebedd6f}
"learning" {2dc3212c-f37a-4929-b97c-aab8ddfd0ca7}
"ep-ol-vm01" {aa20e5de-3175-4a8a-ad6c-282c5e649543}
"ep-ol-vm02" {2790ec5c-2c3a-44c4-9c35-0b434784606b}
"ep-ol-vm03" {174b1d4f-cfbc-46c0-a34d-5410b449ae31}
"ep-ol-mainvm01" {17e4792d-12e9-4ac5-90fb-759e4c6a82a8}   <- !!!

````
#### -- Start VM "ep-ol-mainvm01" ------
````
C:\Windows\System32>vboxmanage startvm "ep-ol-mainvm01"
C:\Windows\System32>vboxmanage list runningvms
"ep-ol-vmain01" {e6c53ec8-f267-4230-a6a2-d4cced941915}
C:\Windows\System32>
````
#### --- Change IP  and Hostname  for ep-ol-mainvm01 --- 
````
  [root@ep-ol-vm02 vadim]# cat /etc/sysconfig/network-scripts/ifcfg-enp0s8
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static
IPV4_FAILURE_FATAL=no
NAME=enp0s8
DEVICE=enp0s8
ONBOOT=yes
IPADDR=192.168.56.110  
PREFIX=24
[root@ep-ol-vm02 vadim]#

 [root@ep-ol-vm02 vadim]# hostnamectl set-hostname ep-ol-vmain01
[root@ep-ol-vm02 vadim]#
[root@ep-ol-vm02 vadim]# hostname
ep-ol-vmain01
[root@ep-ol-vm02 vadim]#
[root@ep-ol-vm02 network-scripts]# systemctl restart network

[root@ep-ol-vmain01 vadim]# cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

192.168.56.110    ep-ol-vmain01   
[root@ep-ol-vmain01 vadim]#
````

### 1.2 -- Create  VirtualBox VM for TEST ENV ep-ol-vmtst01  from OVF OS image CPUS-1 MEM-2048MB --
````
 C:\Windows\System32>vboxmanage import C:\DATA\VMs\template-vm\vbox\ep-ol-vm01.ova --vsys 0  --vmname "ep-ol-vmtst01" --cpus 1 --memory 2048
 
 :\Windows\System32>vboxmanage list vms
"bin_default_1488825039581_84671" {fc542fcd-e6f9-4c7d-8e72-3ebcbebedd6f}
"learning" {2dc3212c-f37a-4929-b97c-aab8ddfd0ca7}
"ep-ol-vm01" {aa20e5de-3175-4a8a-ad6c-282c5e649543}
"ep-ol-vm02" {2790ec5c-2c3a-44c4-9c35-0b434784606b}
"ep-ol-vm03" {174b1d4f-cfbc-46c0-a34d-5410b449ae31}
"ep-ol-vmain01" {e6c53ec8-f267-4230-a6a2-d4cced941915}
"ep-ol-vmtst01" {7963a0e7-86b9-4b8b-87be-c3ca3492d1de}
C:\Windows\System32>

C:\Windows\System32>vboxmanage startvm  "ep-ol-vmtst01"
Waiting for VM "ep-ol-vmtst01" to power on...
VM "ep-ol-vmtst01" has been successfully started.
C:\Windows\System32>

C:\Windows\System32>vboxmanage list runningvms
"ep-ol-vmain01" {e6c53ec8-f267-4230-a6a2-d4cced941915}
"ep-ol-vmtst01" {7963a0e7-86b9-4b8b-87be-c3ca3492d1de}
C:\Windows\System32>
````
#### --- change IP and hostname for ep-ol-vmtst01 ---#
````
[root@ep-ol-vm01 network-scripts]# cat  /etc/sysconfig/network-scripts/ifcfg-enp0s8
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
NAME=enp0s8
DEVICE=enp0s8
ONBOOT=yes
IPADDR=192.168.56.121
PREFIX=24
[root@ep-ol-vm01 network-scripts]#
[root@ep-ol-vm01 network-scripts]# hostnamectl set-hostname ep-ol-vmtst01
[root@ep-ol-vm01 network-scripts]# cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
192.168.56.121  ep-ol-vmtst01
[root@ep-ol-vm01 network-scripts]#

[root@ep-ol-vm01 network-scripts]# systemctl restart network.service
````

###  -- 1.3 Create  Productive environment VM in AWS cloud  through Terraform --### 
/home/vadim/epam-data/terraform-resources/aws-webapp-prod
````
[vadim@ep-ol-vmain01 aws-webapp-prod]$ tree ./
./
├── modules
│   └── webprod_mod
│       ├── vmwebapp-prod_instance.tf
│       ├── vmwebapp-prod_output.tf
│       └── vmwebapp-prod_vars.tf
├── vmwebapp-prod_main.tf
├── vmwebapp-prod_security-group.tf
└── vmwebapp-prod_webserver.tf

2 directories, 6 files
[vadim@ep-ol-vmain01 aws-webapp-prod]$
````
#### ----------------  vmwebapp-prod_main.tf  ---------------------------
````
[vadim@ep-ol-vmain01 aws-webapp-prod]$ cat vmwebapp-prod_main.tf
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.16"
    }
  }

  required_version = ">= 1.2.0"
}

provider "aws" {
  region = "eu-central-1"
}

[vadim@ep-ol-vmain01 aws-webapp-prod]$
````

#### #------- vmwebapp-prod_security-group.tf  ----
````
[vadim@ep-ol-vmain01 aws-webapp-prod]$ cat  vmwebapp-prod_security-group.tf
resource "aws_security_group" "webserver_fw" {
  name        = "web_firewall_access"
  description = "Allow Web TCP & Ssh traffic"
}

resource "aws_security_group_rule" "http_access" {
  type        = "ingress"
  from_port   = 0
  to_port     = 80
  protocol    = "tcp"
  cidr_blocks = ["0.0.0.0/0"]
  //   ipv6_cidr_blocks  = []
  security_group_id = aws_security_group.webserver_fw.id
}

resource "aws_security_group_rule" "https_access" {
  type        = "ingress"
  from_port   = 0
  to_port     = 443
  protocol    = "tcp"
  cidr_blocks = ["0.0.0.0/0"]
  //   ipv6_cidr_blocks  = []
  security_group_id = aws_security_group.webserver_fw.id
}

resource "aws_security_group_rule" "ssh_access" {
  type              = "ingress"
  from_port         = 0
  to_port           = 22
  protocol          = "tcp"
  cidr_blocks       = ["0.0.0.0/0"]
  security_group_id = aws_security_group.webserver_fw.id
}

[vadim@ep-ol-vmain01 aws-webapp-prod]$
````

#### #-------  vmwebapp-prod_webserver.tf  ----------
````
[vadim@ep-ol-vmain01 aws-webapp-prod]$ cat vmwebapp-prod_webserver.tf
module "webserver-production" {
   source = "./modules/webprod_mod"

   security_group_id_var = aws_security_group.webserver_fw.id
   instance_tag_name_var = "websrv-prod"
}
[vadim@ep-ol-vmain01 aws-webapp-prod]$

````

#### #----------   modules/webprod_mod/vmwebapp-prod_vars.tf ------
````
[vadim@ep-ol-vmain01 aws-webapp-prod]$ cat modules/webprod_mod/vmwebapp-prod_vars.tf
//---- Define variables ----------//
variable "security_group_id_var" {
  description = "Define security group ID defenition"
}
variable "instance_tag_name_var" {
  description = "Define Tag Name of instance"
  type = string
}
[vadim@ep-ol-vmain01 aws-webapp-prod]$

````

#### --------   modules/webprod_mod/vmwebapp-prod_instance.tf  -------
````
   [vadim@ep-ol-vmain01 aws-webapp-prod]$ cat modules/webprod_mod/vmwebapp-prod_instance.tf
resource "aws_instance" "webapp-prod" {
  ami           = "ami-06ec8443c2a35b0ba"
  instance_type = "t2.micro"
  key_name = "jks-websrv-rsa-key"
  //--- define security group  for instance
  vpc_security_group_ids = [var.security_group_id_var]
//  vpc_security_group_ids = [aws_security_group.webserver_fw.id]

  tags = {
//    Name    = "websrv-prod"
    Name    = var.instance_tag_name_var
    Service = "Web"
    Owner   = "VVM Student"
    Project = "terraform intro"
  }
}
[vadim@ep-ol-vmain01 aws-webapp-prod]$

````

[vadim@ep-ol-vmain01 aws-webapp-prod]$ terraform validate
[vadim@ep-ol-vmain01 aws-webapp-prod]$ terraform plan
[vadim@ep-ol-vmain01 aws-webapp-prod]$ terraform apply

#### ---Check  connect to aws  ec2  instance  websrv-prod () from ep-ol-vmain01 () and MobaXterm--- 
````
[vadim@ep-ol-vmain01 epam-data]$ ssh -i  /home/vadim/keystst/aws-jks-websrv-rsa-key/jks-websrv-rsa-key   ec2-user@18.156.171.227                                     
Last login: Thu Jul 14 13:01:34 2022 from 188.163.72.59
[ec2-user@ip-172-31-37-89 ~]$

````
----
### 1.4  Configure  Test env ep-ol-vmtst01    and Production env   websrv-prod (aws)  with Ansible ###
####- create  directory /home/vadim/epam-data/ansible-playbooks

````
ansible-playbooks/
├── ansible.cfg
├── inventory-dir
│   ├── aws-webapp_inventory
│   │   └── aws-webapp_hosts
│   └── test-env_inventory
│       └── test-env_hosts
├── log
│   └── ansible.log
├── prepare-test-env.yml
└── roles

5 directories, 5 files
[vadim@ep-ol-vmain01 epam-data]$

````

####  --- Create inventory  files  ---###
For Test env:
````
[vadim@ep-ol-vmain01 epam-data]$ cat ansible-playbooks/inventory-dir/test-env_inventory/test-env_hosts
[test-env]
ep-ol-vmtst01  #192.168.56.121
[vadim@ep-ol-vmain01 epam-data]$
````
For Prod ENV:
````
[vadim@ep-ol-vmain01 epam-data]$ cat ansible-playbooks/inventory-dir/aws-webapp_inventory/aws-webapp_hosts
[aws-webapp]
websrv-prod   ansible_host=18.156.171.227

[aws-webapp:vars]
ansible_ssh_user=ec2-user
ansible_ssh_private_key_file=/home/vadim/keystst/aws-jks-websrv-rsa-key/jks-websrv-rsa-key
[vadim@ep-ol-vmain01 epam-data]$
````

##### Check connect ansible  to aws Prod env
````
[vadim@ep-ol-vmain01 ansible-playbooks]$ ansible  aws-webapp  -m ping
SSH password:
BECOME password[defaults to SSH password]:
[WARNING]: Invalid characters were found in group names but not replaced, use -vvvv to see details
websrv-prod | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "ping": "pong"
}
[vadim@ep-ol-vmain01 ansible-playbooks]$

````

####  ----  Playbook to prepare Test env: 
````
[vadim@ep-ol-vmain01 ansible-playbooks]$ cat prepare-test-env.yml
---
- name: Preparation Test ENvironment Script
  hosts: test-env

  vars:
     user_name: 'jksagent'
     user_pwd: '_Jks_Qwerty_123'
     user_pubkey: '/home/vadim/keystst/jenkins/jksagent-key/jksagent01key_rsa.pub'
     jksagent_workspace_dir: "/home/{{ user_name }}/jksagent-workspace"
     java_pkg: "java-11-openjdk"
     debug_flag: 1
     docker_flag: 1
     docker_pkgs:
        - docker-ce
        - docker-ce-cli
        - containerd.io
        - docker-compose-plugin


  tasks:
     - name: <--- Create user for jenkins agent connection --->
       user:
          name: '{{ user_name }}'
          comment: "Jenkins Agent user for connection"
          password: "{{ user_pwd | password_hash('sha256') }}"
          state: present

     - name: <--- Set authorized key taken from file --->
       authorized_key:
          user: '{{ user_name }}'
          state: present
          key: "{{ lookup('file', '/home/vadim/keystst/jenkins/jksagent-key/jksagent01key_rsa.pub') }}"

     - name: "<--- Create  Jenkins agent workspace directory --->"
       file:
          path: '{{ jksagent_workspace_dir }}'
          state: directory
          owner: "{{ user_name }}"
          group: "{{ user_name }}"
          mode: '0775'

     - name: <--- Install Java package --->
       yum:
          name: "{{ java_pkg }}"
          state: present

     - name: <--- Istall Git packages --->
       yum:
          name: git
          state: present

##------------   Install docker block ----------------------##
     - name: Install docker on Oracle Linux
       block:
          - name: Install package oraclelinux-developer-release-el7
            yum:
               name: oraclelinux-developer-release-el7
               state: present

          - name: Add Docker Repository
            shell: yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

          - name: Install docker pakages
            yum:
               name: "{{ docker_pkgs }}"
               state: present

          - name: Check Installed Docker pakages
            shell:
               cmd: "yum list installed docker-ce docker-ce-cli containerd.io docker-compose-plugin"
               warn: no


          - name: "<--- Start Docker --->"
            service:
               name: docker
               state: started

          - name: "< --- Add user {{ user_name }} to sudo  --->"
            lineinfile:
               path: "/etc/sudoers.d/{{ user_name }}"
               line: '{{ user_name }} ALL=(ALL) NOPASSWD: /usr/bin/docker'
               state: present
               mode: 0440
               create: yes
               validate: 'visudo -cf %s'


       when: docker_flag == 1
##-------------------------------------------------------##

...

````

####  ----  Playbook to prepare Prod ENV ------ : 
````
[vadim@ep-ol-vmain01 ansible-playbooks]$ cat prepare-prod-env.yml
---
- name: Preparation Prod ENVironment playbook
  hosts: aws-webapp

  vars:
     user_name: "vadim"
     user_pwd: "_Qwerty_123"
     user_comment: "admin user"
     user_pubkey: '/home/vadim/keystst/aws-vm-access/aws-vm-key_rsa.pub'
     java_pkg: "java-11-openjdk"

  tasks:
     - name: <--- Create admin User -->
       user:
          name: '{{ user_name }}'
          comment: "{{ user_comment }}"
          password: "{{ user_pwd | password_hash('sha256') }}"
          state: present

     - name: "<--- Set authorized key taken from file --->"
       authorized_key:
          user: '{{ user_name }}'
          state: present
##          key: "{{ lookup('file', '/home/vadim/keystst/aws-vm-access/aws-vm-key_rsa.pub') }}"
          key: "{{ lookup('file', '{{ user_pubkey }}') }}"


     - name: "< --- Add user {{ user_name }} to sudo  --->"
       lineinfile:
          path: "/etc/sudoers.d/{{ user_name }}"
          line: '{{ user_name }} ALL=(ALL) NOPASSWD: ALL'
          state: present
          mode: 0440
          create: yes
          validate: 'visudo -cf %s'

     - name: "<--- Install httpd  server --->"
       yum:
          name: httpd
          state: present

     - name: "<--- Start Httpd service --->"
       service:
          name: httpd
          state: started

...
[vadim@ep-ol-vmain01 ansible-playbooks]$

````

----
## 2.- Delivery website from GitHub into WEB test and production  infrastructure -
### 2.1 #-- Create repo “epam_final-task01” on GitHub –#

#### ----- Create index.html file  (epam_final-task01/index.html)---- 
````
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!-- Add the navbar here -->
    <h2>About me</h2>
    <p>I am learning DevOps course in EPAM </p>
</body>
</html>

````

### 2.2 --- Start and configre Jenkins on MainHost  ep-ol-vmain01 ---
````
[root@ep-ol-vmain01 vadim]# systemctl stop mysqld
[root@ep-ol-vmain01 vadim]# systemctl stop firewalld
[root@ep-ol-vmain01 vadim]#
[root@ep-ol-vmain01 vadim]# systemctl start jenkins
[root@ep-ol-vmain01 vadim]#
[root@ep-ol-vmain01 vadim]# systemctl status jenkins
● jenkins.service - Jenkins Continuous Integration Server
   Loaded: loaded (/usr/lib/systemd/system/jenkins.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2022-07-12 12:38:13 EEST; 9s ago

````


### 2.3 --- Create Freestyle job --- 
-- Add script to  Build -> Execute shell-> Command
````
echo "##------ Start script ------##"
echo "Hello my Jenkins agent  <$NODE_NAME> !!!"
echo "Build number BUILD_NUMBER: $BUILD_NUMBER"
echo "JOB_NAME: $JOB_NAME"
echo "WORKSPACE: $WORKSPACE"
sleep 10
echo "#--- Create Dockerfile ---#"
mkdir -p alpine-apache2
cp index.html alpine-apache2/
cat << EOF > alpine-apache2/Dockerfile
FROM alpine:3.14
MAINTAINER  VVM <vadimmazhar@ukr.net>

ENV  TZ=Europe/Kiev
RUN  apk  update && apk  upgrade && \
     apk add --no-cache apache2 libxml2-dev apache2-utils

COPY  index.html /var/www/localhost/htdocs/

CMD   ["/usr/sbin/httpd", "-D", "FOREGROUND"]

EXPOSE 80 443

EOF
echo "----------------------------"
ls -la
sleep 10
echo "#--- Build docker image ussing alpine-apache2/Dockerfile ---#"
sudo /usr/bin/docker build -t alpine-apache2:v1 alpine-apache2/
sleep 10
echo "#-------------------------------------------------------#"
echo "#------- stop all docker containers ---#"
sudo /usr/bin/docker ps -q | xargs -r sudo /usr/bin/docker stop
#sudo /usr/bin/docker stop $(sudo /usr/bin/docker ps -q)
sleep 10
echo "#-------  start containet --------#"
sudo /usr/bin/docker run -d --name websrv-tst -p 8080:80 --rm alpine-apache2:v1
sleep 10
sudo /usr/bin/docker ps 
echo "##------ End scripts ------##"

````
