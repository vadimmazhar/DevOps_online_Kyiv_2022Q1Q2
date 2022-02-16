# ##############################################
# Task 1.1 Report
# ##############################################
## -- 4. Create account on GitHub. 
## -- 5. Create new private repo on GitHub. Repo name: DevOps_online_City_year_quarter 
## -- 6. You can see example repository structure. --
  https://github.com/vadimmazhar
  https://github.com/vadimmazhar/DevOps_online_Kyiv_2022Q1Q2/new/main/Module01_DevOps-Intro/task_1.1
  DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1/

## -- 7. Clone repositories (Repo) --
Go to github my repo vadimmazhar/DevOps_online_Kyiv_2022Q1Q2
“Code”/Clone->ssh and Copy GitHub link

git@github.com:vadimmazhar/DevOps_online_Kyiv_2022Q1Q2.git

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data
## $ git clone git@github.com:vadimmazhar/DevOps_online_Kyiv_2022Q1Q2.git    !!!
Cloning into 'DevOps_online_Kyiv_2022Q1Q2'...
The authenticity of host 'github.com (140.82.121.3)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 8 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (8/8), done.

$ ls -a
./  ../  DevOps_online_Kyiv_2022Q1Q2/

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data
$ cd DevOps_online_Kyiv_2022Q1Q2/

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2 (main)  !!!
$ ls -la
total 5
drwxr-xr-x 1 Vadim.Mazhar 1049089  0 Feb  7 15:24 ./
drwxr-xr-x 1 Vadim.Mazhar 1049089  0 Feb  7 15:24 ../
drwxr-xr-x 1 Vadim.Mazhar 1049089  0 Feb  7 15:24 .git/
drwxr-xr-x 1 Vadim.Mazhar 1049089  0 Feb  7 15:24 Module01_DevOps-Intro/  !!!
-rw-r--r-- 1 Vadim.Mazhar 1049089 78 Feb  7 15:24 README.md

## -- 10. Create empty readme.txt file. &&  11. Make init commit. --
$ touch readme.txt  !!!

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
$ ls
readme.txt  task_1_1_description.txt

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add \<file\>..." to include in what will be committed)
        readme.txt

nothing added to commit but untracked files present (use "git add" to track)

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
## $ git add *   !!!
  
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged \<file\>..." to unstage)
        new file:   readme.txt


Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)

## $ git commit -a -m "create readme.txt file commit"   !!!
[main 5660a40] create readme.txt file commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 Module01_DevOps-Intro/task_1.1/readme.txt
  
  $ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

## -- (12. Create develop branch and checkout on it.)  && (13. Create index.html empty file. Commit.) --

$ git branch  --show-current
main
$ git checkout -b "develop"
Switched to a new branch 'develop'

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (develop)
$ git branch  --show-current
develop

$ echo "" \> index.html  !!!

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (develop)
$ ls -l
total 2
-rw-r--r-- 1 Vadim.Mazhar 1049089  1 Feb  7 16:43 index.html  !!
-rw-r--r-- 1 Vadim.Mazhar 1049089  0 Feb  7 15:47 readme.txt
-rw-r--r-- 1 Vadim.Mazhar 1049089 33 Feb  7 15:24 task_1_1_description.txt

$ git status
On branch develop
Untracked files:
  (use "git add \<file\>..." to include in what will be committed)
        index.html
$ git add *     !!!
$ git commit -m "-c2- create empty index.html"  !!!
[develop 227ab9b] -c2- create empty index.html
 1 file changed, 1 insertion(+)
 create mode 100644 Module01_DevOps-Intro/task_1.1/index.html
  
## -- 14. Create branch with name “images”. Checkout on it. Add images folder with some images inside it. Commit. --##
$ git checkout -b "images"
Switched to a new branch 'images'

$ git branch  --show-current
images

## $ mkdir flower_images     !!!
$ ls -l
total 2
drwxr-xr-x 1 Vadim.Mazhar 1049089  0 Feb  7 17:04 flower_images/  !!
-rw-r--r-- 1 Vadim.Mazhar 1049089  1 Feb  7 16:43 index.html
-rw-r--r-- 1 Vadim.Mazhar 1049089  0 Feb  7 15:47 readme.txt
-rw-r--r-- 1 Vadim.Mazhar 1049089 33 Feb  7 15:24 task_1_1_description.txt

$ ls flower_images/    !!!
flower_photo1.jpg  flower_photo2.jpg  flower_photo3.jpg  flower_photo4.jpg
$ git status
On branch images
Untracked files:
  (use "git add \<file\>..." to include in what will be committed)
        flower_images/

nothing added to commit but untracked files present (use "git add" to track)

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (images)
$ git add * !!!

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (images)
$ git status
On branch images
Changes to be committed:
  (use "git restore --staged \<file\>..." to unstage)
        new file:   flower_images/flower_photo1.jpg
        new file:   flower_images/flower_photo2.jpg
        new file:   flower_images/flower_photo3.jpg
        new file:   flower_images/flower_photo4.jpg
        
## $ git commit -a -m "-c3- create images brahch and directory"  !!!
[images 0066e36] -c3- create images brahch and directory
 4 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo1.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo2.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo3.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo4.jpg
 
 ## -- 15. Change your index.html. Add images source inside it. Commit.  --##
 $ vi index.html
$ cat index.html
<html>

  <head>
    <title>Flowers pictures</title>
    <meta charset="utf-8">
  </head>

  <body align=center>


    <h1>Flowers Wiki</h1>
    <h1>------------------------</h1>

    <h2>Flower-1</h2>
    <img src="flower_images/flower_photo1.jpg">

    <h2>Flower-2</h2>
    <img src="flower_images/flower_photo2.jpg">

    <h2>Flower-3</h2>
    <img src="flower_images/flower_photo3.jpg">

    <h2>Flower-4</h2>
    <img src="flower_images/flower_photo4.jpg">


  </body>
</html>

$ git status
On branch images
Changes not staged for commit:
  (use "git add \<file\>..." to update what will be committed)
  (use "git restore \<file\>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")

$ git add *
## $ git commit -a -m "-c4- modify index.html, insert images"  !!
[images 1edec20] -c4- modify index.html, insert images
 1 file changed, 27 insertions(+)

$ git status
On branch images
nothing to commit, working tree clean

## -- 16. Go back to develop branch.  &&  17. Create branch with name “styles”. Checkout on it. Add styles folder with styles source inside it. Commit. --
$ git branch -a
  develop
* images
  main
  remotes/origin/HEAD -> origin/main
  remotes/origin/main
## $ git checkout develop  !!
Switched to branch 'develop'

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (develop)

$ git branch  --show-current
develop

## $ git checkout -b "styles"  !!
Switched to a new branch 'styles'

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (styles)
$ git branch --show-current
styles

$ mkdir styles !!

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (styles)
$ ls
index.html  readme.txt  styles/  task_1_1_description.txt

$ cd styles/

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1/styles (styles)
$ vi flower_style1.css

$ ls
flower_style1.css  flower_style2.css  flower_style3.css  flower_style4.css
$ git status
$ git add *
$ git status
On branch styles
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   styles/flower_style1.css
        new file:   styles/flower_style2.css
        new file:   styles/flower_style3.css
        new file:   styles/flower_style4.css


Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (styles)
  
$ git commit -a -m "-c5- create stiles dir with styles files"
[styles 6c6791a] -c5- create stiles dir with styles files
 4 files changed, 36 insertions(+)
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style1.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style2.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style3.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style4.css

  








