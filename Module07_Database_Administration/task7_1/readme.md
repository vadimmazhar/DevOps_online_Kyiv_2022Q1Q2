#  #########################
#  Module 7 Database Administration TASK 7.1
# ############################
## #--------------------------#
## ---  TASK 7.1 PART 1    ---
## #--------------------------#

### 1. Download MySQL server for your OS on VM.
#### get  OS version 
```
[root@ep-ol-vm02 vadim]# hostnamectl | egrep 'Operating System|Architecture|Kernel'
  Operating System: Oracle Linux Server 7.9
            Kernel: Linux 5.4.17-2102.201.3.el7uek.x86_64
      Architecture: x86-64
[root@ep-ol-vm02 vadim]#
```
#### - download  MySql –
Go to  Oracle Linux 7x repo  https://public-yum.oracle.com/oracle-linux-7.html
Select  MySql 8.0 for OS  OL7  Architecture: x86-64  

MySQL 8.0 Community Server: x86_64, Source(x86_64), aarch64, Source(aarch64)
Latest MySQL 8.0 Community Server packages for Oracle Linux 7.

Go to  https://public-yum.oracle.com/repo/OracleLinux/OL7/MySQL80_community/x86_64/index.html

#### Create repo file  /etc/yum.repos.d/OL7_x86_64_MySQL80.repo and check repository
```
[root@ep-ol-vm02 yum.repos.d]# cat   /etc/yum.repos.d/OL7_x86_64_MySQL80.repo
[OL7_x86-64_MySQL80]
name=MySQL 8.0 for Oracle Linux $releasever  ($basearch)
baseurl=http://yum.oracle.com/repo/OracleLinux/OL7/MySQL80_community/$basearch/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
gpgcheck=1
enabled=1

[root@ep-ol-vm02 yum.repos.d]#
[root@ep-ol-vm02 yum.repos.d]# yum repolist
Loaded plugins: langpacks, ulninfo
OL7_x86-64_MySQL80                                                                                           | 3.0 kB  00:00:00   <-!!!
ol7_UEKR6                                                                                                    | 3.0 kB  00:00:00
ol7_latest                                                                                                   | 3.6 kB  00:00:00
(1/2): OL7_x86-64_MySQL80/x86_64/updateinfo                                                                  |   71 B  00:00:00
(2/2): OL7_x86-64_MySQL80/x86_64/primary_db                                                                  | 204 kB  00:00:00
repo id                            repo name                                                                                  status
OL7_x86-64_MySQL80/x86_64          MySQL 8.0 for Oracle Linux 7Server  (x86_64)                                                  320
ol7_UEKR6/x86_64                   Latest Unbreakable Enterprise Kernel Release 6 for Oracle Linux 7Server (x86_64)              680
ol7_latest/x86_64                  Oracle Linux 7Server Latest (x86_64)                                                       24,340
repolist: 25,340
[root@ep-ol-vm02 yum.repos.d]#
```
### 2. Install MySQL server on VM.

##### check available mysql* packages from repositories
```
[root@ep-ol-vm02 yum.repos.d]#
[root@ep-ol-vm02 yum.repos.d]# yum list mysql-community*
Loaded plugins: langpacks, ulninfo
Available Packages
mysql-community-client.i686                                           8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-client.x86_64                                         8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-client-plugins.i686                                   8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-client-plugins.x86_64                                 8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-common.i686                                           8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-common.x86_64                                         8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-devel.i686                                            8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-devel.x86_64                                          8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-embedded-compat.i686                                  8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-embedded-compat.x86_64                                8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-icu-data-files.i686                                   8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-icu-data-files.x86_64                                 8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-libs.i686                                             8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-libs.x86_64                                           8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-libs-compat.i686                                      8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-libs-compat.x86_64                                    8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-server.x86_64                                         8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-server-debug.x86_64                                   8.0.29-1.el7                                OL7_x86-64_MySQL80
mysql-community-test.x86_64                                           8.0.29-1.el7                                OL7_x86-64_MySQL80
[root@ep-ol-vm02 yum.repos.d]#
```
####   Install mysql-community-server  with dependencies
```
[root@ep-ol-vm02 yum.repos.d]# yum install mysql-community-server
Loaded plugins: langpacks, ulninfo
Resolving Dependencies
--> Running transaction check
---> Package mysql-community-server.x86_64 0:8.0.29-1.el7 will be installed
--> Processing Dependency: mysql-community-common(x86-64) = 8.0.29-1.el7 for package: mysql-community-server-8.0.29-1.el7.x86_64
--> Processing Dependency: mysql-community-icu-data-files = 8.0.29-1.el7 for package: mysql-community-server-8.0.29-1.el7.x86_64
--> Processing Dependency: mysql-community-client(x86-64) >= 8.0.11 for package: mysql-community-server-8.0.29-1.el7.x86_64
--> Running transaction check
---> Package mysql-community-client.x86_64 0:8.0.29-1.el7 will be installed
--> Processing Dependency: mysql-community-client-plugins = 8.0.29-1.el7 for package: mysql-community-client-8.0.29-1.el7.x86_64
--> Processing Dependency: mysql-community-libs(x86-64) >= 8.0.11 for package: mysql-community-client-8.0.29-1.el7.x86_64
---> Package mysql-community-common.x86_64 0:8.0.29-1.el7 will be installed
---> Package mysql-community-icu-data-files.x86_64 0:8.0.29-1.el7 will be installed
--> Running transaction check
---> Package mariadb-libs.x86_64 1:5.5.68-1.el7 will be obsoleted
--> Processing Dependency: libmysqlclient.so.18()(64bit) for package: 2:postfix-2.10.1-9.el7.x86_64
--> Processing Dependency: libmysqlclient.so.18(libmysqlclient_18)(64bit) for package: 2:postfix-2.10.1-9.el7.x86_64
---> Package mysql-community-client-plugins.x86_64 0:8.0.29-1.el7 will be installed
---> Package mysql-community-libs.x86_64 0:8.0.29-1.el7 will be obsoleting
--> Running transaction check
---> Package mysql-community-libs-compat.x86_64 0:8.0.29-1.el7 will be obsoleting
--> Finished Dependency Resolution

Dependencies Resolved

====================================================================================================================================
 Package                                     Arch                Version                      Repository                       Size
====================================================================================================================================
Installing:
 mysql-community-libs                        x86_64              8.0.29-1.el7                 OL7_x86-64_MySQL80              1.5 M
     replacing  mariadb-libs.x86_64 1:5.5.68-1.el7
 mysql-community-libs-compat                 x86_64              8.0.29-1.el7                 OL7_x86-64_MySQL80              667 k
     replacing  mariadb-libs.x86_64 1:5.5.68-1.el7
 mysql-community-server                      x86_64              8.0.29-1.el7                 OL7_x86-64_MySQL80               53 M
Installing for dependencies:
 mysql-community-client                      x86_64              8.0.29-1.el7                 OL7_x86-64_MySQL80               14 M
 mysql-community-client-plugins              x86_64              8.0.29-1.el7                 OL7_x86-64_MySQL80              2.5 M
 mysql-community-common                      x86_64              8.0.29-1.el7                 OL7_x86-64_MySQL80              633 k
 mysql-community-icu-data-files              x86_64              8.0.29-1.el7                 OL7_x86-64_MySQL80              2.1 M

Transaction Summary
====================================================================================================================================
Install  3 Packages (+4 Dependent packages)

Total download size: 75 M
Is this ok [y/d/N]: y
Downloading packages:
warning: /var/cache/yum/x86_64/7Server/OL7_x86-64_MySQL80/packages/mysql-community-client-plugins-8.0.29-1.el7.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID ec551f03: NOKEY
Public key for mysql-community-client-plugins-8.0.29-1.el7.x86_64.rpm is not installed
(1/7): mysql-community-client-plugins-8.0.29-1.el7.x86_64.rpm                                                | 2.5 MB  00:00:08
(2/7): mysql-community-client-8.0.29-1.el7.x86_64.rpm                                                        |  14 MB  00:00:10
(3/7): mysql-community-common-8.0.29-1.el7.x86_64.rpm                                                        | 633 kB  00:00:02
(4/7): mysql-community-icu-data-files-8.0.29-1.el7.x86_64.rpm                                                | 2.1 MB  00:00:01
(5/7): mysql-community-libs-8.0.29-1.el7.x86_64.rpm                                                          | 1.5 MB  00:00:03
(6/7): mysql-community-libs-compat-8.0.29-1.el7.x86_64.rpm                                                   | 667 kB  00:00:01
(7/7): mysql-community-server-8.0.29-1.el7.x86_64.rpm                                                        |  53 MB  00:00:09
------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                               3.1 MB/s |  75 MB  00:00:23
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
Importing GPG key 0xEC551F03:
 Userid     : "Oracle OSS group (Open Source Software group) <build@oss.oracle.com>"
 Fingerprint: 4214 4123 fecf c55b 9086 313d 72f9 7b74 ec55 1f03
 Package    : 7:oraclelinux-release-7.9-1.0.9.el7.x86_64 (@anaconda/7.9)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : mysql-community-common-8.0.29-1.el7.x86_64                                                                       1/8
  Installing : mysql-community-client-plugins-8.0.29-1.el7.x86_64                                                               2/8
  Installing : mysql-community-libs-8.0.29-1.el7.x86_64                                                                         3/8
  Installing : mysql-community-client-8.0.29-1.el7.x86_64                                                                       4/8
  Installing : mysql-community-icu-data-files-8.0.29-1.el7.x86_64                                                               5/8
  Installing : mysql-community-server-8.0.29-1.el7.x86_64                                                                       6/8
  Installing : mysql-community-libs-compat-8.0.29-1.el7.x86_64                                                                  7/8
  Erasing    : 1:mariadb-libs-5.5.68-1.el7.x86_64                                                                               8/8
  Verifying  : mysql-community-icu-data-files-8.0.29-1.el7.x86_64                                                               1/8
  Verifying  : mysql-community-libs-compat-8.0.29-1.el7.x86_64                                                                  2/8
  Verifying  : mysql-community-client-8.0.29-1.el7.x86_64                                                                       3/8
  Verifying  : mysql-community-client-plugins-8.0.29-1.el7.x86_64                                                               4/8
  Verifying  : mysql-community-server-8.0.29-1.el7.x86_64                                                                       5/8
  Verifying  : mysql-community-common-8.0.29-1.el7.x86_64                                                                       6/8
  Verifying  : mysql-community-libs-8.0.29-1.el7.x86_64                                                                         7/8
  Verifying  : 1:mariadb-libs-5.5.68-1.el7.x86_64                                                                               8/8

Installed:
  mysql-community-libs.x86_64 0:8.0.29-1.el7                     mysql-community-libs-compat.x86_64 0:8.0.29-1.el7
  mysql-community-server.x86_64 0:8.0.29-1.el7

Dependency Installed:
  mysql-community-client.x86_64 0:8.0.29-1.el7                 mysql-community-client-plugins.x86_64 0:8.0.29-1.el7
  mysql-community-common.x86_64 0:8.0.29-1.el7                 mysql-community-icu-data-files.x86_64 0:8.0.29-1.el7

Replaced:
  mariadb-libs.x86_64 1:5.5.68-1.el7

Complete!
[root@ep-ol-vm02 yum.repos.d]#
```

#### ---check installed MySQL packages 
```
[root@ep-ol-vm02 yum.repos.d]# yum list installed mysql*
Loaded plugins: langpacks, ulninfo
Installed Packages
mysql-community-client.x86_64                                        8.0.29-1.el7                                @OL7_x86-64_MySQL80
mysql-community-client-plugins.x86_64                                8.0.29-1.el7                                @OL7_x86-64_MySQL80
mysql-community-common.x86_64                                        8.0.29-1.el7                                @OL7_x86-64_MySQL80
mysql-community-icu-data-files.x86_64                                8.0.29-1.el7                                @OL7_x86-64_MySQL80
mysql-community-libs.x86_64                                          8.0.29-1.el7                                @OL7_x86-64_MySQL80
mysql-community-libs-compat.x86_64                                   8.0.29-1.el7                                @OL7_x86-64_MySQL80
mysql-community-server.x86_64                                        8.0.29-1.el7                                @OL7_x86-64_MySQL80
[root@ep-ol-vm02 yum.repos.d]#
```

#### ---   Start the mysqld service
```
[root@ep-ol-vm02 yum.repos.d]# systemctl start mysqld
[root@ep-ol-vm02 yum.repos.d]#
[root@ep-ol-vm02 yum.repos.d]# systemctl status  mysqld
- mysqld.service - MySQL Server
   Loaded: loaded (/usr/lib/systemd/system/mysqld.service; enabled; vendor preset: disabled)
   Active: active (running) since Sun 2022-05-22 15:25:51 EEST; 9s ago                       <- !!!
     Docs: man:mysqld(8)
           http://dev.mysql.com/doc/refman/en/using-systemd.html
  Process: 4286 ExecStartPre=/usr/bin/mysqld_pre_systemd (code=exited, status=0/SUCCESS)
 Main PID: 4357 (mysqld)
   Status: "Server is operational"
   CGroup: /system.slice/mysqld.service
           └─4357 /usr/sbin/mysqld

May 22 15:25:39 ep-ol-vm02 systemd[1]: Starting MySQL Server...
May 22 15:25:51 ep-ol-vm02 systemd[1]: Started MySQL Server.
[root@ep-ol-vm02 yum.repos.d]#
````
####  ---  run  /usr/bin/mysql_secure_installation   scripts
```
[root@ep-ol-vm02 yum.repos.d]# /usr/bin/mysql_secure_installation

Securing the MySQL server deployment.

Enter password for user root:
Error: Access denied for user 'root'@'localhost' (using password: YES)
````

#### --- Get temporary mysql root user password 
#### A superuser account 'root'@'localhost is created. A password for the superuser is set and stored in the error log file. To reveal it, use the following command:
#### $> sudo grep 'temporary password' /var/log/mysqld.log
 ````
[root@ep-ol-vm02 yum.repos.d]# sudo grep 'temporary password' /var/log/mysqld.log
2022-05-22T12:25:44.091857Z 6 [Note] [MY-010454] [Server] A temporary password is generated for root@localhost: TUtBrMpk6g;i
[root@ep-ol-vm02 yum.repos.d]#

[root@ep-ol-vm02 yum.repos.d]# mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 13
Server version: 8.0.29

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
````
#### --  Change  root password 
````
mysql>
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'NewPassword_for_root_user!';
Query OK, 0 rows affected (0.04 sec)

mysql>
mysql> exit
Bye
[root@ep-ol-vm02 yum.repos.d]#
````
---- 
### 3. Select a subject area and describe the database schema, (minimum 3 tables)

#### Subject area (DATABASE name): Medical card [medcard]

````
------------------------
|Table#01:Patient      |
------------------------
|p_id           | number|
| fio           | string|
| insuarence_num| number|
-------------------------

----------------------------
|Table#02:Diagnoz-Lib|
---------------- -----------
|d-code          |  number |
|dname           | String |
|ddiscription     | string|
----------------------------

-------------------------
|Table#03: Diagnoz|
-------------------------
|dnum       | number |
|p_id       | number |
|d-code     | number |
|d_date    | datetime|
|doc_id     | number |
------------------ -------

----------+--------------
|Table#04: Doctor |
------------+-----------
|doc_id      | number |
|doc_fio     |  string|
|doc_special | string |
-------------------------

````

### 4. Create a database on the server through the console.
#### -- create database medcard
````
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.00 sec)

mysql>
mysql> CREATE DATABASE medcard;      <- !!!
Query OK, 1 row affected (0.16 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| medcard            |     <- !!!
| mybooks            |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
6 rows in set (0.00 sec)

mysql>
mysql> use medcard;      <- !!!
Database changed
mysql>

mysql> select database();
+------------+
| database() |
+------------+
| medcard    |
+------------+
1 row in set (0.00 sec)
````

#### -- Create 4 tables  patient, diagnoz_lib, diagnoz, doctors
````
mysql> CREATE TABLE patient (p_id INT NOT NULL, fio VARCHAR(50) NOT NULL, insuarence_num INT, PRIMARY KEY (p_id) );
Query OK, 0 rows affected (0.07 sec)

mysql> show tables ;
+-------------------+
| Tables_in_medcard |
+-------------------+
| patient           |
+-------------------+
1 row in set (0.00 sec)

mysql>
mysql> CREATE TABLE diagnoz_lib (dcode INT NOT NULL, dname VARCHAR(50) NOT NULL, ddescrip VARCHAR(250) NOT NULL, PRIMARY KEY (dcode)
 );
Query OK, 0 rows affected (0.13 sec)
mysql>

 mysql> show tables;
+-------------------+
| Tables_in_medcard |
+-------------------+
| diagnoz_lib       |
| patient           |
+-------------------+
2 rows in set (0.00 sec)

mysql>
mysql> CREATE TABLE diagnoz (dnum INT NOT NULL, p_id INT NOT NULL, dcode INT NOT NULL, ddate DATETIME NOT NULL, doc_id INT NOT NULL );
Query OK, 0 rows affected (0.06 sec)

mysql>
mysql> CREATE TABLE doctors (doc_id INT NOT NULL, doc_fio VARCHAR(50) NOT NULL, doc_special VARCHAR(50) NOT NULL );
Query OK, 0 rows affected (0.10 sec)

mysql>
mysql> show tables;
+-------------------+
| Tables_in_medcard |
+-------------------+
| diagnoz           |
| diagnoz_lib       |
| doctors           |
| patient           |
+-------------------+
4 rows in set (0.01 sec)

mysql>
````
----
### 5. Fill in tables
## --- Fill  tables of “medcard” database

````
mysql> use medcard;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql>
mysql> select database();
+------------+
| database() |
+------------+
| medcard    |
+------------+
1 row in set (0.01 sec)

mysql>
mysql> show tables;
+-------------------+
| Tables_in_medcard |
+-------------------+
| diagnoz           |
| diagnoz_lib       |
| doctors           |
| patient           |
+-------------------+
4 rows in set (0.00 sec)

mysql>
````
#### fill table patient 
````
mysql> DESCRIBE patient;
+----------------+-------------+------+-----+---------+-------+
| Field          | Type        | Null | Key | Default | Extra |
+----------------+-------------+------+-----+---------+-------+
| p_id           | int         | NO   | PRI | NULL    |       |
| fio            | varchar(50) | NO   |     | NULL    |       |
| insuarence_num | int         | YES  |     | NULL    |       |
+----------------+-------------+------+-----+---------+-------+
3 rows in set (0.01 sec)

mysql>
mysql> INSERT INTO patient (p_id,fio,insuarence_num) VALUES (100101,"Smit N",90100101);
Query OK, 1 row affected (0.25 sec)

mysql> INSERT INTO patient (p_id,fio,insuarence_num) VALUES (100102,"Brown S",90100102);
Query OK, 1 row affected (0.03 sec)

mysql> INSERT INTO patient (p_id,fio,insuarence_num) VALUES (100201,"Wilson M",90100201);
Query OK, 1 row affected (0.05 sec)

mysql> INSERT INTO patient (p_id,fio,insuarence_num) VALUES (100209,"Johnson J",90100209);
Query OK, 1 row affected (0.03 sec)

mysql>
mysql> select * from patient;
+--------+-----------+----------------+
| p_id   | fio       | insuarence_num |
+--------+-----------+----------------+
| 100101 | Smit N    |       90100101 |
| 100102 | Brown S   |       90100102 |
| 100201 | Wilson M  |       90100201 |
| 100209 | Johnson J |       90100209 |
+--------+-----------+----------------+
4 rows in set (0.00 sec)

mysql>
````


#### ---- modify table structure 
````
mysql> DESCRIBE diagnoz_lib;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| dcode    | int          | NO   | PRI | NULL    |       |
| dname    | varchar(50)  | NO   |     | NULL    |       |
| ddescrip | varchar(250) | NO   |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> ALTER TABLE diagnoz_lib MODIFY dcode VARCHAR(6);
Query OK, 0 rows affected (0.21 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql>
mysql> DESCRIBE diagnoz_lib;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| dcode    | varchar(6)   | NO   | PRI | NULL    |       |
| dname    | varchar(50)  | NO   |     | NULL    |       |
| ddescrip | varchar(250) | NO   |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql>
mysql> ALTER TABLE diagnoz_lib ADD COLUMN  d_id INT NOT NULL FIRST;
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql>
mysql> DESCRIBE diagnoz_lib;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| d_id     | int          | NO   |     | NULL    |       |
| dcode    | varchar(6)   | NO   | PRI | NULL    |       |
| dname    | varchar(50)  | NO   |     | NULL    |       |
| ddescrip | varchar(250) | NO   |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql>
````

####  --  Fill table diagnoz_lib 
````
mysql> DESCRIBE diagnoz_lib;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| d_id     | int          | NO   |     | NULL    |       |
| dcode    | varchar(6)   | NO   | PRI | NULL    |       |
| dname    | varchar(50)  | NO   |     | NULL    |       |
| ddescrip | varchar(250) | NO   |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql>
mysql> INSERT INTO diagnoz_lib (d_id,dcode,dname,ddescrip) VALUES (1,"A00B99","Infection","caused by microorganisms")
    -> ;
Query OK, 1 row affected (0.07 sec)

mysql> INSERT INTO diagnoz_lib (d_id,dcode,dname,ddescrip) VALUES (2,"C00D48","Novoutvorennya","klitynni rozrostannya");
Query OK, 1 row affected (0.03 sec)

mysql>
mysql> INSERT INTO diagnoz_lib (d_id,dcode,dname,ddescrip) VALUES (3,"F00F99","Psyxiky","Rozlad psyxiky");
Query OK, 1 row affected (0.01 sec)

mysql>
mysql> INSERT INTO diagnoz_lib (d_id,dcode,dname,ddescrip) VALUES (4,"G00G99","Nervy","Nervova systema");
Query OK, 1 row affected (0.03 sec)

mysql>
mysql> select * from diagnoz_lib;
+------+--------+----------------+--------------------------+
| d_id | dcode  | dname          | ddescrip                 |
+------+--------+----------------+--------------------------+
|    1 | A00B99 | Infection      | caused by microorganisms |
|    2 | C00D48 | Novoutvorennya | klitynni rozrostannya    |
|    3 | F00F99 | Psyxiky        | Rozlad psyxiky           |
|    4 | G00G99 | Nervy          | Nervova systema          |
+------+--------+----------------+--------------------------+
4 rows in set (0.01 sec)

mysql>
````





