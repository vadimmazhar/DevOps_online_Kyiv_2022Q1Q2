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
$ cat flower_style1.css
H1 {
  color: #000080;
  font-size: 100%;
  font-family: Arial, Verdana, sans-serif;
  text-align: center;
}
P {
  padding-left: 20px;
}

$ ls
flower_style1.css  flower_style2.css  flower_style3.css  flower_style4.css
$ git status
$ git add *
$ git status
On branch styles
Changes to be committed:
  (use "git restore --staged \<file\>..." to unstage)
        new file:   styles/flower_style1.css
        new file:   styles/flower_style2.css
        new file:   styles/flower_style3.css
        new file:   styles/flower_style4.css


Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (styles)
  
### $ git commit -a -m "-c5- create stiles dir with styles files"
[styles 6c6791a] -c5- create stiles dir with styles files
 4 files changed, 36 insertions(+)
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style1.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style2.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style3.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style4.css
 
 ## -- 18. Change your index.html. Commit. --
 $ vi  index.html
 $ cat index.html
<html>

  <head>
    <title>Flowers pictures</title>
    <meta charset="utf-8">
  </head>

  <body align=center>


    <h1>Flowers Wiki</h1>
    <h1>------------------------</h1>


    <link rel="stylesheet" href="styles/flower_style1.css">

    <h2>Flower-1</h2>
    <img src="flower_images/flower_photo1.jpg">


    <link rel="stylesheet" href="styles/flower_style2.css">

    <h2>Flower-2</h2>
    <img src="flower_images/flower_photo2.jpg">


    <link rel="stylesheet" href="styles/flower_style3.css">

    <h2>Flower-3</h2>
    <img src="flower_images/flower_photo3.jpg">


   <link rel="stylesheet" href="styles/flower_style4.css">

    <h2>Flower-4</h2>
    <img src="flower_images/flower_photo4.jpg">


  </body>
</html>


$ git add *
warning: LF will be replaced by CRLF in Module01_DevOps-Intro/task_1.1/index.html.
The file will have its original line endings in your working directory

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (styles)

$ git commit -a -m "-c6- change index.html with style"  !!!
[styles 2676f2d] -c6- change index.html with style
 5 files changed, 41 insertions(+)
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo1.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo2.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo3.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo4.jpg
 
 ## -- 19. Go to develop branch. 20. Merge two new branches into develop using git merge command. Resolve conflict if it appear. 
 ## Do it in next sequence:  •merge “images” into “develop”  •merge “styles” into “develop” --##
$ git branch --show-current
styles

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (styles)
$ git checkout develop
Switched to branch 'develop'

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (develop)
$ git branch --show-current
develop
 
$ git branch -a
* develop
  images
  main
  styles
  remotes/origin/HEAD -> origin/main
  remotes/origin/main

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (develop)
$
## $ git merge images !!
Updating 52ab259..bd55628
Fast-forward
 .../task_1.1/flower_images/flower_photo1.jpg       | Bin 0 -> 25786 bytes
 .../task_1.1/flower_images/flower_photo2.jpg       | Bin 0 -> 111591 bytes
 .../task_1.1/flower_images/flower_photo3.jpg       | Bin 0 -> 74014 bytes
 .../task_1.1/flower_images/flower_photo4.jpg       | Bin 0 -> 87561 bytes
 Module01_DevOps-Intro/task_1.1/index.html          |  29 +++++++++++++++++++++
 5 files changed, 29 insertions(+)
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo1.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo2.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo3.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo4.jpg


## $ git merge styles  !!
Auto-merging Module01_DevOps-Intro/task_1.1/index.html
CONFLICT (content): Merge conflict in Module01_DevOps-Intro/task_1.1/index.html  !!
Automatic merge failed; fix conflicts and then commit the result.


$ ls -l
total 13
drwxr-xr-x 1 Vadim.Mazhar 1049089    0 Feb  9 17:53 flower_images/
-rw-r--r-- 1 Vadim.Mazhar 1049089 1039 Feb  9 17:54 index.html
-rw-r--r-- 1 Vadim.Mazhar 1049089    0 Feb  8 20:32 readme.txt
drwxr-xr-x 1 Vadim.Mazhar 1049089    0 Feb  9 17:54 styles/
-rw-r--r-- 1 Vadim.Mazhar 1049089   33 Feb  8 20:28 task_1_1_description.txt

$ git merge styles
`error: Merging is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.
`


## $ vi index.html  !!!

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (develop|MERGING)
$ cat index.html  !!
<html>

  <head>
    <title>Flowers pictures</title>
    <meta charset="utf-8">
  </head>

  <body align=center>


    <h1>Flowers Wiki</h1>
    <h1>------------------------</h1>


    <link rel="stylesheet" href="styles/flower_style1.css">

    <h2>Flower-1</h2>
    <img src="flower_images/flower_photo1.jpg">


    <link rel="stylesheet" href="styles/flower_style2.css">

    <h2>Flower-2</h2>
    <img src="flower_images/flower_photo2.jpg">


    <link rel="stylesheet" href="styles/flower_style3.css">

    <h2>Flower-3</h2>
    <img src="flower_images/flower_photo3.jpg">


   <link rel="stylesheet" href="styles/flower_style4.css">

    <h2>Flower-4</h2>
    <img src="flower_images/flower_photo4.jpg">


  </body>
</html>

### $ git add index.html
warning: LF will be replaced by CRLF in Module01_DevOps-Intro/task_1.1/index.html.
The file will have its original line endings in your working directory

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (develop|MERGING)
### $ git commit -m "merged and resolved the conflict in index.html"
[develop 76b5466] merged and resolved the conflict in index.html

## --21. Do not delete any branches!  22. Merge develop into master --## 
$ git branch -a
* develop
  images
  main
  styles
  remotes/origin/HEAD -> origin/main
  remotes/origin/main

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (develop)
## $ git checkout main 
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
## $ git merge develop  !!
Updating 88e910b..76b5466
Fast-forward
 .../task_1.1/flower_images/flower_photo1.jpg       | Bin 0 -> 25786 bytes
 .../task_1.1/flower_images/flower_photo2.jpg       | Bin 0 -> 111591 bytes
 .../task_1.1/flower_images/flower_photo3.jpg       | Bin 0 -> 74014 bytes
 .../task_1.1/flower_images/flower_photo4.jpg       | Bin 0 -> 87561 bytes
 Module01_DevOps-Intro/task_1.1/index.html          |  41 +++++++++++++++++++++
 .../task_1.1/styles/flower_style1.css              |   9 +++++
 .../task_1.1/styles/flower_style2.css              |   9 +++++
 .../task_1.1/styles/flower_style3.css              |   9 +++++
 .../task_1.1/styles/flower_style4.css              |   9 +++++
 9 files changed, 77 insertions(+)
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo1.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo2.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo3.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/flower_images/flower_photo4.jpg
 create mode 100644 Module01_DevOps-Intro/task_1.1/index.html
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style1.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style2.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style3.css
 create mode 100644 Module01_DevOps-Intro/task_1.1/styles/flower_style4.css

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
$ ls
flower_images/  index.html  readme.txt  styles/  task_1_1_description.txt

## --- 23. Try to inspect your repository with git log command. Use different options with this command (git log --help) --##
$ git log  !!
commit 76b5466a96d1d46e053b0a968f26b6bfe0bbf3a2 (HEAD -> main, develop)
Merge: bd55628 2676f2d
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Wed Feb 9 18:05:11 2022 +0200

    merged and resolved the conflict in index.html

commit 2676f2d4495af022ef5881a9d4db2cdfb96569ff (styles)
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Wed Feb 9 17:46:20 2022 +0200

    -c6- change index.html with style

commit 6c6791a4f95fb7a1997ed856664485ab1c1fe710
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 21:13:41 2022 +0200

    -c5- create stiles dir with styles files

commit bd556289db76634238f930e009ecae16126dc1f0 (images)
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 20:54:02 2022 +0200

    -c4- modify index.html, insert images

commit ca8889870916a7445eb14d3d8e49f10bc83a3fd4
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 20:50:49 2022 +0200

    -c3- create images brahch and directory

commit 52ab2590f1eb478a72da51b93f3b3e4958b2945c
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 20:42:09 2022 +0200

    -c2- create empty index.html

commit 88e910b72f1052094acece8c55306ad286108de1
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 20:37:12 2022 +0200

    -c1- create readme.txt file

commit 52d2740e1884b6adfa24ed69ad02bb517e44ae3d (origin/main, origin/HEAD)
Author: vadimmazhar <99098762+vadimmazhar@users.noreply.github.com>
Date:   Sun Feb 6 22:52:52 2022 +0200

    Create task_1_1_description.txt

commit 32073bc838bd8074591844f294c986f9538bbf9b
Author: vadimmazhar <99098762+vadimmazhar@users.noreply.github.com>
Date:   Sat Feb 5 23:15:39 2022 +0200

    Initial commit

### $ git log -1 HEAD    !!
commit 76b5466a96d1d46e053b0a968f26b6bfe0bbf3a2 (HEAD -> main, develop)
Merge: bd55628 2676f2d
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Wed Feb 9 18:05:11 2022 +0200

    merged and resolved the conflict in index.html

 
 ### Get commit files from log – (--name-only) 
$ git log --name-only
commit 76b5466a96d1d46e053b0a968f26b6bfe0bbf3a2 (HEAD -> main, develop)
Merge: bd55628 2676f2d
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Wed Feb 9 18:05:11 2022 +0200

    merged and resolved the conflict in index.html

commit 2676f2d4495af022ef5881a9d4db2cdfb96569ff (styles)
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Wed Feb 9 17:46:20 2022 +0200

    -c6- change index.html with style

Module01_DevOps-Intro/task_1.1/flower_images/flower_photo1.jpg
Module01_DevOps-Intro/task_1.1/flower_images/flower_photo2.jpg
Module01_DevOps-Intro/task_1.1/flower_images/flower_photo3.jpg
Module01_DevOps-Intro/task_1.1/flower_images/flower_photo4.jpg
Module01_DevOps-Intro/task_1.1/index.html

commit 6c6791a4f95fb7a1997ed856664485ab1c1fe710
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 21:13:41 2022 +0200

    -c5- create stiles dir with styles files

Module01_DevOps-Intro/task_1.1/styles/flower_style1.css
Module01_DevOps-Intro/task_1.1/styles/flower_style2.css
Module01_DevOps-Intro/task_1.1/styles/flower_style3.css
Module01_DevOps-Intro/task_1.1/styles/flower_style4.css

commit bd556289db76634238f930e009ecae16126dc1f0 (images)
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 20:54:02 2022 +0200

    -c4- modify index.html, insert images

Module01_DevOps-Intro/task_1.1/index.html

commit ca8889870916a7445eb14d3d8e49f10bc83a3fd4
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 20:50:49 2022 +0200

    -c3- create images brahch and directory

Module01_DevOps-Intro/task_1.1/flower_images/flower_photo1.jpg
Module01_DevOps-Intro/task_1.1/flower_images/flower_photo2.jpg
Module01_DevOps-Intro/task_1.1/flower_images/flower_photo3.jpg
Module01_DevOps-Intro/task_1.1/flower_images/flower_photo4.jpg

commit 52ab2590f1eb478a72da51b93f3b3e4958b2945c
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 20:42:09 2022 +0200

    -c2- create empty index.html

Module01_DevOps-Intro/task_1.1/index.html

commit 88e910b72f1052094acece8c55306ad286108de1
Author: vadimmazhar <vadimmazhar@ukr.net>
Date:   Tue Feb 8 20:37:12 2022 +0200

    -c1- create readme.txt file

Module01_DevOps-Intro/task_1.1/readme.txt

commit 52d2740e1884b6adfa24ed69ad02bb517e44ae3d (origin/main, origin/HEAD)
Author: vadimmazhar <99098762+vadimmazhar@users.noreply.github.com>
Date:   Sun Feb 6 22:52:52 2022 +0200

    Create task_1_1_description.txt

Module01_DevOps-Intro/task_1.1/task_1_1_description.txt

commit 32073bc838bd8074591844f294c986f9538bbf9b
Author: vadimmazhar <99098762+vadimmazhar@users.noreply.github.com>
Date:   Sat Feb 5 23:15:39 2022 +0200

    Initial commit

README.md

## -- 24. Push all your changes with all your branches to origin (git push origin --all). --
## $ git push origin --all !!
Enumerating objects: 41, done.
Counting objects: 100% (41/41), done.
Delta compression using up to 4 threads
Compressing objects: 100% (31/31), done.
Writing objects: 100% (38/38), 293.09 KiB | 2.62 MiB/s, done.
Total 38 (delta 6), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (6/6), done.
To github.com:vadimmazhar/DevOps_online_Kyiv_2022Q1Q2.git
   52d2740..76b5466  main -> main
 * [new branch]      develop -> develop
 * [new branch]      images -> images
 * [new branch]      styles -> styles

## -- 25. Execute command “git reflog“ and save it content somewhere (not in repository) with filename “task1.1_GIT.txt”. --## 

### $ git reflog > ~/epam_data/tmp/task1.1_GIT_REFLOG_v1.txt

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
$ vi ~/epam_data/tmp/task1.1_GIT_REFLOG_v1.txt

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
$ cat ~/epam_data/tmp/task1.1_GIT_REFLOG_v1.txt !!
76b5466 HEAD@{0}: merge develop: Fast-forward
88e910b HEAD@{1}: checkout: moving from develop to main
76b5466 HEAD@{2}: commit (merge): merged and resolved the conflict in index.html
bd55628 HEAD@{3}: merge images: Fast-forward
52ab259 HEAD@{4}: checkout: moving from styles to develop
2676f2d HEAD@{5}: commit: -c6- change index.html with style
6c6791a HEAD@{6}: checkout: moving from develop to styles
52ab259 HEAD@{7}: checkout: moving from styles to develop
6c6791a HEAD@{8}: commit: -c5- create stiles dir with styles files
52ab259 HEAD@{9}: checkout: moving from develop to styles
52ab259 HEAD@{10}: checkout: moving from images to develop
bd55628 HEAD@{11}: commit: -c4- modify index.html, insert images
ca88898 HEAD@{12}: commit: -c3- create images brahch and directory
52ab259 HEAD@{13}: checkout: moving from develop to images
52ab259 HEAD@{14}: commit: -c2- create empty index.html
88e910b HEAD@{15}: checkout: moving from main to develop
88e910b HEAD@{16}: commit: -c1- create readme.txt file
52d2740 HEAD@{17}: clone: from github.com:vadimmazhar/DevOps_online_Kyiv_2022Q1Q2.git

## -- 26. Add task1.1_GIT.txt to your local repo in then Push it in GitHub repo. --## 
cp ~/epam_data/tmp/task1.1_GIT_REFLOG_v1.txt ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 !!

$ ls -l task1.1_GIT_REFLOG_v1.txt
-rw-r--r-- 1 Vadim.Mazhar 1049089 1091 Feb  9 18:39 task1.1_GIT_REFLOG_v1.txt

$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
`  (use "git add <file>..." to include in what will be committed)
        task1.1_GIT_REFLOG_v1.txt
`
nothing added to commit but untracked files present (use "git add" to track)

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
## $ git add task1.1_GIT_REFLOG_v1.txt !!
warning: LF will be replaced by CRLF in Module01_DevOps-Intro/task_1.1/task1.1_GIT_REFLOG_v1.txt.
The file will have its original line endings in your working directory

Vadim.Mazhar@KIE-2969448-NB MINGW64 ~/epam_data/github_data/DevOps_online_Kyiv_2022Q1Q2/Module01_DevOps-Intro/task_1.1 (main)
$ git status
`On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   task1.1_GIT_REFLOG_v1.txt
`
## $ git commit -m "-c8- add task1_1 git reflog file"
[main 08d6fbd] -c8- add task1_1 git reflog file
 1 file changed, 18 insertions(+)
 create mode 100644 Module01_DevOps-Intro/task_1.1/task1.1_GIT_REFLOG_v1.txt

## $ git push origin !!
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 843 bytes | 281.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:vadimmazhar/DevOps_online_Kyiv_2022Q1Q2.git
   76b5466..08d6fbd  main -> main


