# 1. Printing Variables

**Flag:**         
pwn.college{0s4VsuvbJB45omlwk-poriFOtq6.ddTN1QDLzcTN0czW}

**Procedure:**        
In this challenge the flag was put into the variable called "FLAG"  I had to read it out using 'echo' .

**Code:**   
```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{0s4VsuvbJB45omlwk-poriFOtq6.ddTN1QDLzcTN0czW}
```

# 2. Setting Variables

**Flag:**    
pwn.college{cNpseWN4tTPfVAOJd3RlaEbwLrn.dlTN1QDLzcTN0czW}

**Procedure:**      
In this challenge I had to set the PWN variable to the value COLLEGE keeping in mind that, in shell terms, prepending of $ triggers what is called variable expansion so I had to basically
use 'PWN=COLLEGE' .

**Code:**      
```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{cNpseWN4tTPfVAOJd3RlaEbwLrn.dlTN1QDLzcTN0czW}
```

# 3. Multi-word Variables

**Flag:**     
pwn.college{Agu8AWxGntFjOvCp9dMBf7oxCih.dBjN1QDLzcTN0czW}

**Procedure:**         
In this challenge I had to set the variable PWN to COLLEGE YEAH, since there was space in between COLLEGE and YEAh so I had to quote them.

**Code:**       
```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{Agu8AWxGntFjOvCp9dMBf7oxCih.dBjN1QDLzcTN0czW}
```

# 4. Exporting Variables 

**Flag:**   
pwn.college{wEhfwbN9FLR_0w8olV-lvOC5XfV.dJjN1QDLzcTN0czW}

**Procedure:** 
Here I first set the value of PWN to COLLEGE and then exported it after that I set the value of COLLEGE to PWN and then run then command /challenge/run .

**Code:**   
```bash
hacker@variables~exporting-variables:~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{wEhfwbN9FLR_0w8olV-lvOC5XfV.dJjN1QDLzcTN0czW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

# 5. Printing Exported Variables

***Flag:**    
pwn.college{g8tMjtyNtnfC7EickZ0n1rAR5qm.dhTN1QDLzcTN0czW}

**Procedure**    
I had to just use 'env' commmand which printed all the exported variables and I found out the flag from it.

**Code:** 
```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
COLORTERM=truecolor
TERM_PROGRAM_VERSION=1.89.1
HOSTNAME=variables~printing-exported-variables
VSCODE_PROXY_URI=https://pwn.college/workspace/code/proxy/{{port}}/
PWD=/home/hacker
DOJO_AUTH_TOKEN=d285622f21e727c5bcbe8699922315a29a513d8373c37e56be12d019ccd20bee
VSCODE_GIT_ASKPASS_NODE=/nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:
GIT_ASKPASS=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/extensions/git/dist/askpass.sh
FLAG=pwn.college{g8tMjtyNtnfC7EickZ0n1rAR5qm.dhTN1QDLzcTN0czW}
VSCODE_GIT_ASKPASS_EXTRA_ARGS=
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm-256color
LESSOPEN=| /usr/bin/lesspipe %s
VSCODE_GIT_IPC_HANDLE=/tmp/vscode-git-de7246c8df.sock
SHLVL=2
LC_CTYPE=C.UTF-8
VSCODE_GIT_ASKPASS_MAIN=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/extensions/git/dist/askpass-main.js
BROWSER=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/helpers/browser.sh
PATH=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
NODE_EXEC_PATH=/nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node
TERM_PROGRAM=vscode
VSCODE_IPC_HOOK_CLI=/tmp/vscode-ipc-d11d3220-14e4-4556-830e-e3afe156aa45.sock
_=/run/workspace/bin/env
```

# 6. Storing Command Output

**Flag:**     
pwn.college{IYnJmBoOkMi7lCc9JRhX8uSijwL.dVzN0UDLzcTN0czW}

**Procedure:**  
In this challenge read the output of the /challenge/run command directly into a variable called PWN and then read it out using 'echo' .

**Code:** 
```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{IYnJmBoOkMi7lCc9JRhX8uSijwL.dVzN0UDLzcTN0czW}
```

# 7. Reading Input 

**Flag:**    
pwn.college{A4Zm3Fu88q5PKuXy4UTTLEVjeku.dhzN1QDLzcTN0czW}

**Procedure:**     
This challenge required me to set the value of variable PWN to COLLEGE from user using read command.

**Code:**   
```bash
hacker@variables~reading-input:~$ read -p "PWN=" PWN
PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{A4Zm3Fu88q5PKuXy4UTTLEVjeku.dhzN1QDLzcTN0czW}
```

# 8. Reading Files 

**Flag:**    
pwn.college{cZT3oP15qGxkZ1bXyqp7j-qa91R.dBjM4QDLzcTN0czW}

**Procedure:**     
Here I just redirected the contents in /challenge/read_me to PWN variable using read and I got the flag.

**Code:**     
```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{cZT3oP15qGxkZ1bXyqp7j-qa91R.dBjM4QDLzcTN0czW}
```