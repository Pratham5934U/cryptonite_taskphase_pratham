# 1. Listing Processes

**Flag:**    
pwn.college{sAgPepqi2J4fGyJHClq4N4PmGqD.dhzM4QDLzcTN0czW}

**Procedure:**       
In this challenge /challenge/run was renamed to a random filename and I could not ls /challenge and it was already launched so I had to see running process list, figure out the filename, 
and relaunch it directly for the flag so I got the running process list using ps -ef and found the renamed file and ran it to get the flag.

**Code:**    
```
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 20:28 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 20:28 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 20:28 ?        00:00:00 /challenge/6065-run-5615
root          72      68  0 20:28 ?        00:00:00 sleep 6h
hacker        81       1  2 20:28 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/out/node/entry.js --au
hacker       102      81 17 20:28 ?        00:00:05 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/out/node/entry
hacker       143     102  9 20:28 ?        00:00:02 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       158     102  1 20:28 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/bootstr
hacker       221     158  0 20:28 pts/1    00:00:00 /run/dojo/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/vs/workbench/contrib/terminal/browser/media/
hacker       336     221  0 20:29 pts/1    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/6065-run-5615
Yahaha, you found me! Here is your flag:
pwn.college{sAgPepqi2J4fGyJHClq4N4PmGqD.dhzM4QDLzcTN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```

# 2. killing process

**Flag:**    
pwn.college{UAK-dW6BJpzzrejFggOeHotj5ev.dJDN4QDLzcTN0czW}

**Procedure:**    
First I found out dont_run processs using 'ps -ef | grep /challenge/dont_run' then to terminate it I used 'kill' .

**Code:**   
```
hacker@processes~killing-processes:~$ ps -ef | grep /challenge/dont_run
hacker        73      71  0 21:22 ?        00:00:00 /challenge/dont_run
hacker       384     223  0 21:22 pts/1    00:00:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 71
bash: kill: (71) - Operation not permitted
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{UAK-dW6BJpzzrejFggOeHotj5ev.dJDN4QDLzcTN0czW}
```

# 3. Interrrupting Process 

**Flag:**     
pwn.college{sjyBJ9WI2c2gNwUYWBqfPm5Nply.dNDN4QDLzcTN0czW}

**Procedure:**     
In this challenge i had to interrupt the process run using Ctrl+c .

**Code:**       
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{sjyBJ9WI2c2gNwUYWBqfPm5Nply.dNDN4QDLzcTN0czW}
```

# 4.Suspending Processes

**Flag:**    
pwn.college{s75Z7QOroF20Umfw_4C1GYR15xE.dVDN4QDLzcTN0czW}

**Procedure:**      
I had to first run /challenge/run then suspend it in the background so that when I run it again it can see it's copy running and give the flag.

**Code:**        
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         401     159  0 21:47 pts/0    00:00:00 bash /challenge/run
root         403     401  0 21:47 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         401     159  0 21:47 pts/0    00:00:00 bash /challenge/run
root         531     159  0 21:47 pts/0    00:00:00 bash /challenge/run
root         533     531  0 21:47 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{s75Z7QOroF20Umfw_4C1GYR15xE.dVDN4QDLzcTN0czW}
```

# 5. Resuming Processes

**Flag:**    
pwn.college{8zoVnCroHpEpdp0B-ivVGV0V_wm.dZDN4QDLzcTN0czW}

**Procedure**   
Here I had to first run /challenge/run then suspend it in the background using Ctrl+z and then resume it using fg .

**Code:**
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{8zoVnCroHpEpdp0B-ivVGV0V_wm.dZDN4QDLzcTN0czW}
Don't forget to press Enter to quit me!

Goodbye!
```

# 6. Backgrounding Processes

**Flag:**      
pwn.college{sHMcBvGJDYlYMx_sYz0Bzi7Hmw2.ddDN4QDLzcTN0czW}

**Procedure:**       
Here I first ran /challenge/run then suspended it in the background then resumed it after that ran another run so I could get the flag.

**Code:**     
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         424 S+   bash /challenge/run
root         426 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         424 S    bash /challenge/run
root         509 S    sleep 6h
root         576 S+   bash /challenge/run
root         578 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sHMcBvGJDYlYMx_sYz0Bzi7Hmw2.ddDN4QDLzcTN0czW}
hacker@processes~backgrounding-processes:~$ 
```

# 7. Foregrounding Processes

**Flag:**     
pwn.college{Aao3M4-lJvJZZfZXWdRLB_Ero65.dhDN4QDLzcTN0czW}

**Procedure:**    
This challenge required me to run /challenge/run then suspend it resume it in background using bg and finally foreground it using fg .

**Code:**    
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{Aao3M4-lJvJZZfZXWdRLB_Ero65.dhDN4QDLzcTN0czW}
```

# 8. Starting Background Processes

**Flag:**       
pwn.college{siFR9tTn4opoNJpztCMmvzvMPKl.dlDN4QDLzcTN0czW}

**Procedure:**      
Here I had to just start the function right backgrounded.

**Code:**      
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 399
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{siFR9tTn4opoNJpztCMmvzvMPKl.dlDN4QDLzcTN0czW}
```

# 9. Process exit codes

**Flag:**     
pwn.college{Q0E1YYvqc2zJhbNj_M3bEO2awNC.dljN4UDLzcTN0czW}

**Procedure:**    
Here I had to run /challenge/get-code then use the code which I got from it and use it as instructed to get the flag.

**Code:**   
```
hacker@processes~process-exit-codes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 22:22 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 22:22 ?        00:00:00 /run/dojo/bin/sleep 6h
hacker        75       1  3 22:22 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/out/node/entry.js --auth=none --bind
hacker        96      75 26 22:22 ?        00:00:05 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/out/node/entry
hacker       137      96 11 22:22 ?        00:00:01 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vsc
hacker       152      96  4 22:22 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/bootstrap-fork --type
hacker       215     152  0 22:22 pts/1    00:00:00 /run/dojo/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/vs/workbench/contrib/terminal/browser/media/shellIntegrati
hacker       264     215  0 22:23 pts/1    00:00:00 ps -ef
hacker@processes~process-exit-codes:~$ /challenge/get-code 
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
226
hacker@processes~process-exit-codes:~$ /challenge/submit-code
You must run /challenge/submit-code with the exit code you retrieved from 
/challenge/get-code as the first argument:

Usage: /challenge/submit-code [EXIT_CODE]
hacker@processes~process-exit-codes:~$ /challenge/226
bash: /challenge/226: No such file or directory
hacker@processes~process-exit-codes:~$ /challenge/submit-code 226
CORRECT! Here is your flag:
pwn.college{Q0E1YYvqc2zJhbNj_M3bEO2awNC.dljN4UDLzcTN0czW}
```
