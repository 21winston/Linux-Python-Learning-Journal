## Going into student2's home directory

**Command**

```cd /home/student2```

**Output**

```-bash: cd: /home/student2: No such file or directory```

## Becoming student2 and finding out I still don't see the home directory

**command**

``` su - student2```

**Output**

```Password: 
su: warning: cannot change directory to /home/student2: No such file or directory```

## Giving student2 a home directoru

```@skodi:~$ sudo mkdir /home/student2
[sudo] password for skodi: 
skodi@skodi:~$ cp -r /etc/skel/. /home/student2```

##Realized that I needed to do all this as root user and made the correction
 
```cp: cannot create regular file '/home/student2/./.bash_logout': Permission denied
cp: cannot create regular file '/home/student2/./.bashrc': Permission denied
cp: cannot create regular file '/home/student2/./.profile': Permission denied```

```skodi@skodi:~$ sudo cp -r /etc/skel/. /home/student2```
## Fixed the ownership

```skodi@skodi:~$ sudo chown student2:student2 /home/student2
skodi@skodi:~$ su -s student2 
Password: 
This is the Z Shell configuration function for new users,
zsh-newuser-install.
You are seeing this message because you have no zsh startup files
(the files .zshenv, .zprofile, .zshrc, .zlogin in the directory
~).  This function can help you with a few settings that should
make your use of the shell easier.

You can:

(q)  Quit and do nothing.  The function will be run again next time.

(0)  Exit, creating the file ~/.zshrc containing just a comment.
     That will prevent this function being run again.

(1)  Continue to the main menu.

(2)  Populate your ~/.zshrc with the configuration recommended
     by the system administrator and exit (you will need to edit
     the file by hand, if so desired).

--- Type one of the keys in parentheses --- E
Aborting.
The function will be run again next time.  To prevent this, execute:
  touch ~/.zshrc
/home/student2```

## Changed the shell to bash

skodi@skodi:~$ sudo usermod -s /bin/bash student2
[sudo] password for skodi: 
student2:x:1001:1001::/home/student2:/bin/bash
skodi@skodi:~$ sudo grep student2 /etc/passwd[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[Cusermod -s /bin/bash student2[C[C[C[C[C[C[C[C[C[C[C[C[C[C[Cexit[Ksu - student2
[?2004lPassword: 
[?2004hstudent2@skodi:~$ pwd
[?2004l/home/student2
[?2004hstudent2@skodi:~$ k[Kls
[?2004l[?2004hstudent2@skodi:~$ ls -a
[?2004l[0m[01;34m.[0m  [01;34m..[0m  .bash_logout  .bashrc  .profile  .zcompdump
[?2004hstudent2@skodi:~$ ls -l
[?2004ltotal 0
[?2004hstudent2@skodi:~$ ls[K[Kls -la -l
[?2004ltotal 72
drwxr-xr-x 2 student2 student2  4096 Jun 11 12:11 [0m[01;34m.[0m
drwxr-xr-x 4 root     root      4096 Jun 11 12:07 [01;34m..[0m
-rw-r--r-- 1 student2 student2   220 Jun 11 12:08 .bash_logout
-rw-r--r-- 1 student2 student2  3771 Jun 11 12:08 .bashrc
-rw-r--r-- 1 student2 student2   807 Jun 11 12:08 .profile
-rw-rw-r-- 1 student2 student2 50426 Jun 11 12:11 .zcompdump
[?2004hstudent2@skodi:~$ ch[Kd /etc/pam.d
[?2004l[?2004hstudent2@skodi:/etc/pam.d$ pwd
[?2004l/etc/pam.d
[?2004hstudent2@skodi:/etc/pam.d$ cd ..
[?2004l[?2004hstudent2@skodi:/etc$ pd[Kwd
[?2004l/etc
[?2004hstudent2@skodi:/etc$ cd
[?2004l[?2004hstudent2@skodi:~$ pwd
[?2004l/home/student2
[?2004hstudent2@skodi:~$ exit
[?2004llogout
[?2004hskodi@skodi:~$ eit[K[Kxit
[?2004lexit

Script done on 2026-06-11 12:24:24+03:00 [COMMAND_EXIT_CODE="0"]
