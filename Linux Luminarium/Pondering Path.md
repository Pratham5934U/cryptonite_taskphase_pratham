# 1. The PATH Variable

**Flag:**   
pwn.college{k323Uia1QoHJqUHim2OGCJqTAEv.dZzNwUDLzcTN0czW}

**Proceedure:**      
In this challenge after printing the variable I tried figuring out the statements which I could remove so that I can get the flag after some time figured out that PATH="" and I got the flag.

**Code:**        
```
hacker@path~the-path-variable:~$ echo $PATH
/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{k323Uia1QoHJqUHim2OGCJqTAEv.dZzNwUDLzcTN0czW}
```

# 2. Setting PATH

**Flag:**   
pwn.college{E75b31C41bvQ90hhBuETtYBrVa1.dVzNyUDLzcTN0czW}

**Proceedure:**      
In this challenge I had to overwrite PATH with /challenge/more_commands/ so that on running /challenge/run the win command can be invoked using it's bare name.

**Code:**        
```
hacker@path~setting-path:~$ echo $PATH
/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{E75b31C41bvQ90hhBuETtYBrVa1.dVzNyUDLzcTN0czW}
```

# 3. Adding Commands 

**Flag:**   
pwn.college{Ib2vNryw0PA2tn-NfFgYJnWQDQ0.dZzNyUDLzcTN0czW}

**Proceedure:**      
Here first I found the location of cat then made the win command and wrote the location of cat in it then made it executable and then ran /challenge/run.

**Code:**        
```
hacker@path~adding-commands:~$ find / -name cat
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.XvrUsDZh8M’: Permission denied
/run/workspace/bin/cat
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/bin/cat
/usr/share/doc/zsh-common/examples/Functions/cat
/opt/busybox/busybox-1.33.2/_install/bin/cat
/opt/busybox/busybox-1.33.2/testsuite/cat
/opt/aflplusplus/nyx_mode/packer/linux_initramfs/rootTemplate/bin/cat
/nix/store/hgcmc7ps7wr0sxnbc87g4ba970km2vy4-dojo-workspace-full/bin/cat
/nix/store/mjnsl8dps0vn3aaf9wpgk4n830x320a7-dojo-workspace-full/bin/cat
/nix/store/nlxcqrgiszbjqkq86qhnflrbrs4adaac-dojo-workspace-full/bin/cat
/nix/store/6sin45s97yp4cfdn3q74drsjd7f4cq1f-dojo-workspace-full/bin/cat
/nix/store/cakzg9vppcbxwq046nlbi6xmib3xx4ka-dojo-workspace-full/bin/cat
/nix/store/vapa6rnwfvbm3srldx33nyy2ybz9iqpy-dojo-workspace-full/bin/cat
/nix/store/a18ji16bi5ws1zksk1jwrx8dir6rdbhi-dojo-workspace-full/bin/cat
/nix/store/h8k7v1w69b9fs60jkx59vkhpy6scwgap-dojo-workspace-full/bin/cat
/nix/store/nsh8bjqlami5grymm2mv63plmncga7wk-dojo-workspace-full/bin/cat
/nix/store/k71apxkm38m3g34k01sb6zhysi0y7gph-coreutils-9.5/bin/cat
hacker@path~adding-commands:~$ /usr/bin/cat b
/usr/bin/cat: b: No such file or directory
hacker@path~adding-commands:~$ nano win.sh
hacker@path~adding-commands:~$ ld
/nix/store/adakqsdbifx7d688z4874ap17clarhfn-binutils-2.41/bin/ld: no input files
hacker@path~adding-commands:~$ ls
 COLLEGE   Desktop   PATH   PWN   a   error   instruction   instructions   myflag   not-the-flag  'not-the-flag!'   output   p.sh   pwn   pwn_output   rm.sh   the-flag   win.sh   x.sh
hacker@path~adding-commands:~$ bash win.sh
/usr/bin/cat: /flag: Permission denied
hacker@path~adding-commands:~$ mv win win.sh
mv: cannot stat 'win': No such file or directory
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ mv win win.sh
hacker@path~adding-commands:~$ ls
 COLLEGE   Desktop   PATH   PWN   a   error   instruction   instructions   myflag   not-the-flag  'not-the-flag!'   output   p.sh   pwn   pwn_output   rm.sh   the-flag   win.sh   x.sh
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ ls
 COLLEGE   Desktop   PATH   PWN   a   error   instruction   instructions   myflag   not-the-flag  'not-the-flag!'   output   p.sh   pwn   pwn_output   rm.sh   the-flag   win   win.sh   x.sh
hacker@path~adding-commands:~$ pwd
/home/hacker
hacker@path~adding-commands:~$ mkdir scripts
hacker@path~adding-commands:~$ mv scripts/ win
mv: cannot overwrite non-directory 'win' with directory 'scripts/'
hacker@path~adding-commands:~$ mv scripts/win win
mv: cannot stat 'scripts/win': No such file or directory
hacker@path~adding-commands:~$ cd scripts/
hacker@path~adding-commands:~/scripts$ touch win
hacker@path~adding-commands:~/scripts$ nano win
hacker@path~adding-commands:~/scripts$ cat win
/usr/bin/cat /flag
hacker@path~adding-commands:~/scripts$ PATH=~/scripts
hacker@path~adding-commands:~/scripts$ chmod u+x win
bash: chmod: command not found
hacker@path~adding-commands:~/scripts$ /usr/bin/chmod u+x win
hacker@path~adding-commands:~/scripts$ /challege/run
bash: /challege/run: No such file or directory
hacker@path~adding-commands:~/scripts$ /challenge/run
Invoking 'win'....
pwn.college{Ib2vNryw0PA2tn-NfFgYJnWQDQ0.dZzNyUDLzcTN0czW}
```

# 4. Hijacking Commands

**Flag:**   
pwn.college{0dYbYC6pnvuE0dM7OH5XDjge7fl.ddzNyUDLzcTN0czW}

**Proceedure:**      
First I had to find the location of cat then created rm command and added in it the location of cat file to read flag then make it executable then change PATH as 
required then execute /challenge/run.

**Code:**        
```
hacker@path~hijacking-commands:~$ find / -name cat
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.XvrUsDZh8M’: Permission denied
/run/workspace/bin/cat
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/bin/cat
/usr/share/doc/zsh-common/examples/Functions/cat
/opt/busybox/busybox-1.33.2/_install/bin/cat
/opt/busybox/busybox-1.33.2/testsuite/cat
/opt/aflplusplus/nyx_mode/packer/linux_initramfs/rootTemplate/bin/cat
/nix/store/hgcmc7ps7wr0sxnbc87g4ba970km2vy4-dojo-workspace-full/bin/cat
/nix/store/mjnsl8dps0vn3aaf9wpgk4n830x320a7-dojo-workspace-full/bin/cat
/nix/store/nlxcqrgiszbjqkq86qhnflrbrs4adaac-dojo-workspace-full/bin/cat
/nix/store/6sin45s97yp4cfdn3q74drsjd7f4cq1f-dojo-workspace-full/bin/cat
/nix/store/cakzg9vppcbxwq046nlbi6xmib3xx4ka-dojo-workspace-full/bin/cat
/nix/store/vapa6rnwfvbm3srldx33nyy2ybz9iqpy-dojo-workspace-full/bin/cat
/nix/store/a18ji16bi5ws1zksk1jwrx8dir6rdbhi-dojo-workspace-full/bin/cat
/nix/store/h8k7v1w69b9fs60jkx59vkhpy6scwgap-dojo-workspace-full/bin/cat
/nix/store/nsh8bjqlami5grymm2mv63plmncga7wk-dojo-workspace-full/bin/cat
/nix/store/k71apxkm38m3g34k01sb6zhysi0y7gph-coreutils-9.5/bin/cat
hacker@path~hijacking-commands:~$ /scripts
bash: /scripts: No such file or directory
hacker@path~hijacking-commands:~$ ls
 COLLEGE   Desktop   PATH   PWN   a   error   instruction   instructions   myflag   not-the-flag  'not-the-flag!'   output   p.sh   pwn   pwn_output   rm.sh   scripts   the-flag   win   win.sh   x.sh
hacker@path~hijacking-commands:~$ ~/scripts
bash: /home/hacker/scripts: Is a directory
hacker@path~hijacking-commands:~$ cd ~/scripts
hacker@path~hijacking-commands:~/scripts$ nano rm
hacker@path~hijacking-commands:~/scripts$ PATH=/home/hacker
hacker@path~hijacking-commands:~/scripts$ chmod +x rm
bash: chmod: command not found
hacker@path~hijacking-commands:~/scripts$ /usr/bin/chmod +x rm
hacker@path~hijacking-commands:~/scripts$ /challenge/run
Trying to remove /flag...
/challenge/run: line 7: rm: command not found
hacker@path~hijacking-commands:~/scripts$ cat /flag
bash: cat: command not found
hacker@path~hijacking-commands:~/scripts$ echo $PATH
/home/hacker
hacker@path~hijacking-commands:~/scripts$ PATH=~/scripts
hacker@path~hijacking-commands:~/scripts$ /challenge/run
Trying to remove /flag...
pwn.college{0dYbYC6pnvuE0dM7OH5XDjge7fl.ddzNyUDLzcTN0czW}
```
