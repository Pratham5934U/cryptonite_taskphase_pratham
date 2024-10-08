# 1. cat: not the pet, but the command

**Flag:**     
pwn.college{E4LKRg0P1sE3A5BZGyvV4YOMhOJ.dFzN1QDLzcTN0czW}

**Procedure**     
In this challenge the flag was copied in the home directory. On opening the terminal I was already in the home directory this was concluded by the symbool '~' so i had to just type 'cat flag' command and the flag was read out.

**Code** <br>
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag   
pwn.college{E4LKRg0P1sE3A5BZGyvV4YOMhOJ.dFzN1QDLzcTN0czW}

# 2. catting absolute path

**Flag**    
pwn.college{Qdc3mxrwVLgfva4QDUVgK0D4xQT.dlTM5QDLzcTN0czW}

**Procedure**     
In this challenge the flag is in /flag where the flag always lives in pwn.college to get it I had to just type the 'cat' and then the absolute path '/flag'.

**Code:**    
hacker@commands~catting-absolute-paths:~$ cat /flag       
pwn.college{Qdc3mxrwVLgfva4QDUVgK0D4xQT.dlTM5QDLzcTN0czW}


# 3. more catting practice

**Flag**       
pwn.college{IP2KgAOUIRsc6aqw8BEFW_T0cw3.dBjM5QDLzcTN0czW}

**Procedure**          
Here I could not use 'cd' command to enter the directory so to get the flag I had to read out the flag in the provided location, used 'cat' along with the absolute path where the flag was stored  '/usr/share/calendar/flag'.

**Code**    
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/calendar/flag. Go cat it out **without** cding into that 
directory!       
hacker@commands~more-catting-practice:~$ cat /usr/share/calendar/flag       
pwn.college{IP2KgAOUIRsc6aqw8BEFW_T0cw3.dBjM5QDLzcTN0czW}

# 4. grepping for a needle in a haystack

**Flag**     
pwn.college{oypET6Dsr1PJ_oKDPoeZ13dN0a6.ddTM4QDLzcTN0czW}

**Procedure**    
 'grep' command is used to search the file for lines of text containing SEARCH_STRING and print them to the console. Here there were a hundred thousand lines of text into the /challenge/data.txt file so I used grep command to search the line which starts with 'pwn.college' as the flags have the same starting. 

**Code**     
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt      
pwn.college{oypET6Dsr1PJ_oKDPoeZ13dN0a6.ddTM4QDLzcTN0czW}


# 5. listing files

**Flag**     
pwn.college{EzTAXD_xTvnII7SLa_Ec08uhdMM.dhjM4QDLzcTN0czW}

**Procedure**       
I had to use 'ls' command to list the everything in the home directory then used the same command with absolute path '/challenge' and got the renamed flag file.

**Code:**         
hacker@commands~listing-files:~$ ls /    
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~listing-files:~$ ls /challenge      
17034-renamed-run-32665  DESCRIPTION.md        
hacker@commands~listing-files:~$ /challenge/17034-renamed-run-32665        
Yahaha, you found me! Here is your flag:        
pwn.college{EzTAXD_xTvnII7SLa_Ec08uhdMM.dhjM4QDLzcTN0czW}    
hacker@commands~listing-files:~$ /flag         
bash: /flag: Permission denied      

# 6. touching files

**Flag**      
pwn.college{E6klr13UGhsQcQWmNnGXRzmUjNS.dBzM4QDLzcTN0czW}

**Procedure**        
I had to creat two files named 'pwn' and 'college' in '/tmp' then executed 'run' program in 'challenge' directory.

**Code:**         
hacker@commands~touching-files:~$ ls /tmp     
bin  hsperfdata_root  tmp.XvrUsDZh8M  vscode-git-350992565c.sock  vscode-ipc-1f62b92b-07e4-4c0e-b4f4-553e3031b8b2.sock  vscode-ipc-f90f7932-33f5-4582-aba6-0b08ba2d3733.sock      
hacker@commands~touching-files:~$ touch /tmp/pwn        
hacker@commands~touching-files:~$ touch /tmp/college        
hacker@commands~touching-files:~$ /challenge/run      
Success! Here is your flag:       
pwn.college{E6klr13UGhsQcQWmNnGXRzmUjNS.dBzM4QDLzcTN0czW}


# 7. removing files

**Flag**         
pwn.college{M7C7ekGy8wFIyzDWQs9VvPqb2sx.dZTOwUDLzcTN0czW}

**Procedure**   
I had to delete a file named 'delete_me' stored in home directory using 'rm' command and provided the relative path.

**Code:**          
hacker@commands~removing-files:~$ ls
Desktop  a  delete_me
hacker@commands~removing-files:~$ ls
Desktop  a  delete_me
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
Desktop  a
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{M7C7ekGy8wFIyzDWQs9VvPqb2sx.dZTOwUDLzcTN0czW}


# 8. hidden files

**Flag**     
pwn.college{AhEe4zGZvo1Z_HRsWHLTiOd6yZ_.dBTN4QDLzcTN0czW}

**Procedure** 
In this challenge the flag was kept in a hidden file using '.' in the starting to list the hidden files I had to invoke ls with -a, after getting the file name I read it out using 'cat' command.  

**Code:**    
hacker@commands~hidden-files:~$ ls     
Desktop  a   
hacker@commands~hidden-files:~$ cd /    
hacker@commands~hidden-files:/$ ls        
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var      
hacker@commands~hidden-files:/$ ls -a         
.  ..  .dockerenv  .flag-24604320419474  bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var      
hacker@commands~hidden-files:/$ cat .flag-24604320419474            
pwn.college{AhEe4zGZvo1Z_HRsWHLTiOd6yZ_.dBTN4QDLzcTN0czW}


# # 9. AN Epic Filesystem Quest

**Flag**      
pwn.college{gwmoMPtH9ZPhw_sNVYLWjNFIedH.dljM4QDLzcTN0czW}

**Procedure**     
In this challenge the was a huge file system in which I listed different files and directories to find the first clue after that I follow the clues which led to flag.

**Code:**    
hacker@commands~an-epic-filesystem-quest:~$ cd /     
hacker@commands~an-epic-filesystem-quest:/$ ls       
INSIGHT  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var     
hacker@commands~an-epic-filesystem-quest:/$ ls -a    
.  ..  .dockerenv  INSIGHT  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var       
hacker@commands~an-epic-filesystem-quest:/$ /INSIGHT     
bash: /INSIGHT: Permission denied     
hacker@commands~an-epic-filesystem-quest:/$ cd /INSIGHT        
bash: cd: /INSIGHT: Not a directory        
hacker@commands~an-epic-filesystem-quest:/$ cat .dockerenv            
hacker@commands~an-epic-filesystem-quest:/$ cat flag        
cat: flag: Permission denied            
hacker@commands~an-epic-filesystem-quest:/$ cat challenge       
cat: challenge: Is a directory          
hacker@commands~an-epic-filesystem-quest:/$ /challenge         
bash: /challenge: Is a directory               
hacker@commands~an-epic-filesystem-quest:/$ cd /challenge          
hacker@commands~an-epic-filesystem-quest:/challenge$ ls        
DESCRIPTION.md          
hacker@commands~an-epic-filesystem-quest:/challenge$ ls -a       
.  ..  .bashrc  .init  DESCRIPTION.md       
hacker@commands~an-epic-filesystem-quest:/challenge$ cd /     
hacker@commands~an-epic-filesystem-quest:/$ cd      
hacker@commands~an-epic-filesystem-quest:~$ ls          
Desktop  a       
hacker@commands~an-epic-filesystem-quest:~$ cd /          
hacker@commands~an-epic-filesystem-quest:/$ ls        
INSIGHT  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var     
hacker@commands~an-epic-filesystem-quest:/$ ls -a          
.  ..  .dockerenv  INSIGHT  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var       
hacker@commands~an-epic-filesystem-quest:/$ cat INSIGHT        
Lucky listing!         
The next clue is in: /usr/share/matplotlib/mpl-data/stylelib         

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.         
hacker@commands~an-epic-filesystem-quest:/$ cd /usr        
hacker@commands~an-epic-filesystem-quest:/usr$ /share/matplotlib/mpl-data/stylelib           
bash: /share/matplotlib/mpl-data/stylelib: No such file or directory          
hacker@commands~an-epic-filesystem-quest:/usr$ ls               
aarch64-linux-gnu  bin  games  include  lib  lib32  lib64  libexec  libx32  local  sbin  share  src              
hacker@commands~an-epic-filesystem-quest:/usr$ /share          
bash: /share: No such file or directory            
hacker@commands~an-epic-filesystem-quest:/usr$ cd /share         
bash: cd: /share: No such file or directory         
hacker@commands~an-epic-filesystem-quest:/usr$ /usr/share/matplotlib/mpl-data/stylelib          
bash: /usr/share/matplotlib/mpl-data/stylelib: Is a directory            
hacker@commands~an-epic-filesystem-quest:/usr$ cd /usr/share/matplotlib/mpl-data/stylelib          
hacker@commands~an-epic-filesystem-quest:/usr/share/matplotlib/mpl-data/stylelib$ ls            
BLUEPRINT                 classic.mplstyle          ggplot.mplstyle              seaborn-dark-palette.mplstyle  seaborn-muted.mplstyle     seaborn-poster.mplstyle  seaborn-whitegrid.mplstyle
Solarize_Light2.mplstyle  dark_background.mplstyle  grayscale.mplstyle           seaborn-dark.mplstyle          seaborn-notebook.mplstyle  seaborn-talk.mplstyle    seaborn.mplstyle
_classic_test.mplstyle    fast.mplstyle             seaborn-bright.mplstyle      seaborn-darkgrid.mplstyle      seaborn-paper.mplstyle     seaborn-ticks.mplstyle   tableau-colorblind10.mplstyle
bmh.mplstyle              fivethirtyeight.mplstyle  seaborn-colorblind.mplstyle  seaborn-deep.mplstyle          seaborn-pastel.mplstyle    seaborn-white.mplstyle
hacker@commands~an-epic-filesystem-quest:/usr/share/matplotlib/mpl-data/stylelib$ cat BLUEPRINT          
Tubular find!           
The next clue is in: /opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8       

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.         
hacker@commands~an-epic-filesystem-quest:/usr/share/matplotlib/mpl-data/stylelib$ cd /opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8       
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ ls -a       
.  ..  .NOTE  build-script-build-script-build  build-script-build-script-build.json  dep-build-script-build-script-build  invoked.timestamp       
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ cat .NOTE        
Great sleuthing!           
The next clue is in: /usr/share/tcltk/tk8.6/ttk      

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!        
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$  /usr/share/tcltk/tk8.6/ttk          
bash: /usr/share/tcltk/tk8.6/ttk: Is a directory          
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ cat  /usr/share/tcltk/tk8.6/ttk     
cat: /usr/share/tcltk/tk8.6/ttk: Is a directory          
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ cat  /usr/share/tcltk/tk8.6/ttk        
cat: /usr/share/tcltk/tk8.6/ttk: Is a directory         
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ ls  /usr/share/tcltk/tk8.6/ttk        
SPOILER-TRAPPED  aquaTheme.tcl  clamTheme.tcl     combobox.tcl  defaults.tcl  fonts.tcl       notebook.tcl     progress.tcl  scrollbar.tcl  spinbox.tcl   ttk.tcl    vistaTheme.tcl  xpTheme.tcl           
altTheme.tcl     button.tcl     classicTheme.tcl  cursors.tcl   entry.tcl     menubutton.tcl  panedwindow.tcl  scale.tcl     sizegrip.tcl   treeview.tcl  utils.tcl  winTheme.tcl      
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ cat SPOILER-TRAPPED        
cat: SPOILER-TRAPPED: No such file or directory           
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ cat  /usr/share/tcltk/tk8.6/ttk/SPOILER-TRAPPED        
Tubular find!            
The next clue is in: /usr/lib/python3/dist-packages/prompt_toolkit/shortcuts/progress_bar          
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ cd /usr/lib/python3/dist-packages/prompt_toolkit/shortcuts/progress_bar          
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/prompt_toolkit/shortcuts/progress_bar$ ls           
SNIPPET  __init__.py  __pycache__  base.py  formatters.py              
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/prompt_toolkit/shortcuts/progress_bar$ cat SNIPPET             
Great sleuthing!                
The next clue is in: /usr/share/rsync              

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!                 
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/prompt_toolkit/shortcuts/progress_bar$ ls /usr/share/rsync                    
CLUE-TRAPPED  scripts                    
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/prompt_toolkit/shortcuts/progress_bar$ cat /usr/share/rsync/CLUE-TRAPPED                 
Great sleuthing!               
The next clue is in: /usr/local/lib/python3.8/dist-packages/setuptools/_vendor/autocommand              

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.             
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/prompt_toolkit/shortcuts/progress_bar$ cd  /usr/local/lib/python3.8/dist-packages/setuptools/_vendor/autocommand    
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/_vendor/autocommand$ ls -a           
.  ..  .TIP  __init__.py  __pycache__  autoasync.py  autocommand.py  automain.py  autoparse.py  errors.py         
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/_vendor/autocommand$ cat .TIP           
Tubular find!       
The next clue is in: /etc/php/7.4/apache2/conf.d          

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.         
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/_vendor/autocommand$ cd /etc/php/7.4/apache2/conf.d         
hacker@commands~an-epic-filesystem-quest:/etc/php/7.4/apache2/conf.d$ ls               
10-mysqlnd.ini  10-pdo.ini       20-ctype.ini  20-ffi.ini       20-ftp.ini      20-iconv.ini  20-mysqli.ini     20-phar.ini   20-readline.ini  20-sockets.ini  20-sysvsem.ini  20- 
   tokenizer.ini      
10-opcache.ini  20-calendar.ini  20-exif.ini   20-fileinfo.ini  20-gettext.ini  20-json.ini   20-pdo_mysql.ini  20-posix.ini  20-shmop.ini     20-sysvmsg.ini  20-sysvshm.ini  EVIDENCE    
hacker@commands~an-epic-filesystem-quest:/etc/php/7.4/apache2/conf.d$ cat EVIDENCE       
Congratulations, you found the clue!         
The next clue is in: /opt/aflplusplus/nyx_mode/QEMU-Nyx/linux-user/alpha              
hacker@commands~an-epic-filesystem-quest:/etc/php/7.4/apache2/conf.d$ cd /opt/aflplusplus/nyx_mode/QEMU-Nyx/linux-user/alpha          
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/nyx_mode/QEMU-Nyx/linux-user/alpha$ ls            
BRIEF  cpu_loop.c  signal.c  sockbits.h  syscall_nr.h  target_cpu.h  target_elf.h  target_fcntl.h  target_signal.h  target_structs.h  target_syscall.h  termbits.h             
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/nyx_mode/QEMU-Nyx/linux-user/alpha$ cat BRIEF          
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!           
It is: pwn.college{gwmoMPtH9ZPhw_sNVYLWjNFIedH.dljM4QDLzcTN0czW}

# 10. making directories

**Flag**
pwn.college{krLrsjNDLCHYFpHUS96nA9epr63.dFzM4QDLzcTN0czW}

**Procedure**     
I had to make a directory whose absolute path was '/tmp/pwn' and make a file college in it then run '/challlenge/run' which check my solution and gave me the flag.

**Code:**   
hacker@commands~making-directories:~$ mkdir /tmp/pwn.   
hacker@commands~making-directories:~$ ls /tmp.     
bin  hsperfdata_root  pwn  tmp.XvrUsDZh8M  vscode-git-7afde2b337.sock  vscode-ipc-4c74aabe-d87d-4e4e-a39a-f4bd91da2e8e.sock  vscode-ipc-a2914e18-da9e-4775-a57a-8a34b6906e99.sock.    
hacker@commands~making-directories:~$ /tmp/pwn.  
bash: /tmp/pwn: Is a directory.  
hacker@commands~making-directories:~$ cd tmp/pwn.      
bash: cd: tmp/pwn: No such file or directory.  
hacker@commands~making-directories:~$ cd /tmp/pwn.  
hacker@commands~making-directories:/tmp/pwn$ touch college.  
hacker@commands~making- directories:/tmp/pwn$ /challenge/run.   
Success! Here is your flag:    
pwn.college{krLrsjNDLCHYFpHUS96nA9epr63.dFzM4QDLzcTN0czW}

# 11. Finding files

**Flag**        
pwn.college{Y2DotLqEdoUSSlfVBJmuylV9EOz.dJzM4QDLzcTN0czW}

**Procedure**    
Here I learned how to use find command. All the flags start with 'pwn.college' so i had to just find the file that started with this but there were a number of files so I had to read them using cat command and find my flag.

**Code:**    
hacker@commands~finding-files:~$ ls.   
Desktop  a.   
hacker@commands~finding-files:~$ ls /   
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var.   
hacker@commands~finding-files:~$ ls /challenge.  
DESCRIPTION.md  run.  
hacker@commands~finding-files:~$ /challenge/run.  
The flag is hidden (and readable) somewhere on the filesystem. Go find it!   
hacker@commands~finding-files:~$ find -name.   
find: missing argument to `-name'  
hacker@commands~finding-files:~$   
hacker@commands~finding-files:~$ find -name flag.  
hacker@commands~finding-files:~$ find / -name flag.  
find: ‘/root’: Permission denied.  
find: ‘/proc/1/task/1/fd’: Permission denied.  
find: ‘/proc/1/task/1/fdinfo’: Permission denied.  
find: ‘/proc/1/task/1/ns’: Permission denied.   
find: ‘/proc/1/fd’: Permission denied.  
find: ‘/proc/1/map_files’: Permission denied.  
find: ‘/proc/1/fdinfo’: Permission denied.  
find: ‘/proc/1/ns’: Permission denied   
find: ‘/proc/7/task/7/fd’: Permission denied.  
find: ‘/proc/7/task/7/fdinfo’: Permission denied.  
find: ‘/proc/7/task/7/ns’: Permission denied.  
find: ‘/proc/7/fd’: Permission denied  
find: ‘/proc/7/map_files’: Permission denied. 
find: ‘/proc/7/fdinfo’: Permission denied.  
find: ‘/proc/7/ns’: Permission denied. 
find: ‘/var/log/private’: Permission denied.   
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
find: ‘/run/mysqld’: Permission denied          
find: ‘/run/sudo’: Permission denied             
find: ‘/etc/ssl/private’: Permission denied           
/usr/local/lib/python3.8/dist-packages/pwnlib/flag               
/usr/local/share/radare2/5.9.5/flag                     
/usr/share/racket/collects/ffi/unsafe/private/flag              
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag           
/opt/radare2/libr/flag              
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag       
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag         
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag       
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory                 
hacker@commands~finding-files:~$ cd /usr/local/lib/python3.8/dist-packages/pwnlib/flag           
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cat flag         
cat: flag: No such file or directory           
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ /usr/local/lib/python3.8/dist-packages/pwnlib     
bash: /usr/local/lib/python3.8/dist-packages/pwnlib: Is a directory      
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cd /usr/local/lib/python3.8/dist-packages/pwnlib           
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib$ cat flag     
cat: flag: Is a directory   
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib$ cd flag        
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ ls      
__init__.py  __pycache__  flag.py            
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cat flag.py     
"""Describes a way to submit a key to a key server.        
"""            
from __future__ import absolute_import      
from __future__ import division        
          
import os      
                               
from pwnlib.args import args         
from pwnlib.log import getLogger          
from pwnlib.tubes.remote import remote                                   

env_server  = args.get('FLAG_HOST', 'flag-submission-server').strip()              
env_port    = args.get('FLAG_PORT', '31337').strip()             
env_file    = args.get('FLAG_FILE', '/does/not/exist').strip()            
env_exploit_name = args.get('EXPLOIT_NAME', 'unnamed-exploit').strip()          
env_target_host  = args.get('TARGET_HOST', 'unknown-target').strip()             
env_team_name    = args.get('TEAM_NAME', 'unknown-team').strip()       

log = getLogger(__name__)           

def submit_flag(flag,                      
                exploit=env_exploit_name,      
                target=env_target_host,        
                server=env_server,          
                port=env_port,          
                team=env_team_name):     
    """                                  
    Submits a flag to the game server          

    Arguments:                         
        flag(str): The flag to submit.            
        exploit(str): Exploit identifier, optional            
        target(str): Target identifier, optional            
        server(str): Flag server host name, optional         
        port(int): Flag server port, optional           
        team(str): Team identifier, optional               

    Optional arguments are inferred from the environment,           
    or omitted if none is set.           
 
    Returns:                 
        A string indicating the status of the key submission,       
        or an error code.          

    Doctest:           

        >>> l = listen()              
        >>> _ = submit_flag('flag', server='localhost', port=l.lport)        
        >>> c = l.wait_for_connection()         
        >>> c.recvall().split()                    
        [b'flag', b'unnamed-exploit', b'unknown-target', b'unknown-team']         
    """                    
    flag = flag.strip()            

    log.success("Flag: %r" % flag)         

    data = "\n".join([flag,           
                      exploit,         
                      target,          
                      team,                     
                      '']).encode('ascii')          
 
    if os.path.exists(env_file):          
        write(env_file, data)           
        return            

    try:          
        with remote(server, int(port)) as r:          
            r.send(data)                   
            return r.recvall(timeout=1)           
    except Exception:                        
        log.warn("Could not submit flag %r to %s:%s", flag, server, port)           
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cat /usr/local/share/radare2/5.9.5/flag        
cat: /usr/local/share/radare2/5.9.5/flag: Is a directory            
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cat /usr/share/racket/collects/ffi/unsafe/private/flag           
pwn.college{Y2DotLqEdoUSSlfVBJmuylV9EOz.dJzM4QDLzcTN0czW}          

# 12. linking files

**Flag**      
pwn.college{EzDshxIRwlyqmvqYRF6zvVVAZ8W.dlTM1UDLzcTN0czW}

**Procedure**
This challlenge introduced me about linker. Here flag was in /flag but but /challenge/catflag will instead read out /home/hacker/not-the-flag so inorder to fool it I tried linking the not-flag-file to flag file but it showed 'file exists' so I first deleted the not-the-flag file and and created it again and linked it to /flag file so when i use '/challenge/catflag' them it read out not-the-flag which in turn game me the flag.

**Code:**    
hacker@commands~linking-files:~$ cat /challenge/catflag       
#!/opt/pwn.college/bash           

fold -s <<< "About to read out the /home/hacker/not-the-flag file!"        
cat /home/hacker/not-the-flag      
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag file!       
ln: target 'file!': No such file or directory                                  
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag file            
ln: target 'file': No such file or directory                              
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag           
ln: failed to create symbolic link '/home/hacker/not-the-flag': File exists              
hacker@commands~linking-files:~$ ls /            
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var          
hacker@commands~linking-files:~$ cd         
hacker@commands~linking-files:~$ ls               
 Desktop   a   not-the-flag  'not-the-flag!'                               
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag            
ln: failed to create symbolic link '/home/hacker/not-the-flag': File exists             
hacker@commands~linking-files:~$ rm /home/hacker/not-the-flag                 
hacker@commands~linking-files:~$ ls                 
 Desktop   a  'not-the-flag!'                             
hacker@commands~linking-files:~$ cat /challenge/flag             
cat: /challenge/flag: No such file or directory             
hacker@commands~linking-files:~$ ls /challenge               
DESCRIPTION.md  catflag                                  
hacker@commands~linking-files:~$ cat /challenge/catflag                  
#!/opt/pwn.college/bash                                         

fold -s <<< "About to read out the /home/hacker/not-the-flag file!"           
cat /home/hacker/not-the-flag             
hacker@commands~linking-files:~$ cd ~/                
hacker@commands~linking-files:~$ touch not-the-flag                 
hacker@commands~linking-files:~$ ls            
 Desktop   a   not-the-flag  'not-the-flag!'                  
hacker@commands~linking-files:~$ ln -s /flag ~/not-the-flag                    
ln: failed to create symbolic link '/home/hacker/not-the-flag': File exists           
hacker@commands~linking-files:~$ rm /home/hacker/not-the-flag            
hacker@commands~linking-files:~$ ls            
 Desktop   a  'not-the-flag!'                                             
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag             
hacker@commands~linking-files:~$ /challenge/catflag         
About to read out the /home/hacker/not-the-flag file!            
pwn.college{EzDshxIRwlyqmvqYRF6zvVVAZ8W.dlTM1UDLzcTN0czW}                 
