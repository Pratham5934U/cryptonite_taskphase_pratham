# 1. Becoming root with su

**Flag:**      
pwn.college{ErPjiMrHesjXWkhKJLX2-D4Wdwt.dVTN0UDLzcTN0czW}

**Procedure:**     
In this challenge I had to switch to root using su command and password in order to read out /flag .

**Code:**        
```bash
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{ErPjiMrHesjXWkhKJLX2-D4Wdwt.dVTN0UDLzcTN0czW}
```

# 2.  Other users with su

**Flag:**      
pwn.college{wvhX4zYMsKEU8-Wgyhb-LwHNgUs.dZTN0UDLzcTN0czW}

**Procedure:**     
I had to provide user name to su and provide password to switch to zardus and then run /challenge/run .

**Code:**        
```bash
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wvhX4zYMsKEU8-Wgyhb-LwHNgUs.dZTN0UDLzcTN0czW}
```

# 3. Cracking passwords

**Flag:**      
pwn.college{YvfwBZJPdXIOL1a2vuEWaD808ZY.ddTN0UDLzcTN0czW}

**Procedure:**     
Here I first cracked the password using John the Ripper from the leak of /etc/shadow (in /challenge/shadow-leak) after cracking the password I switch to zardus and then ran /challenge/run
to get the flag.

**Code:**        
```bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04861g/s 283.0p/s 283.0c/s 283.0C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{YvfwBZJPdXIOL1a2vuEWaD808ZY.ddTN0UDLzcTN0czW}
```

# 4. Using sudo

**Flag:**      
pwn.college{wk7j7rmo1kSiBCh0QH9TS8e-thS.dhTN0UDLzcTN0czW}

**Procedure:**     
Here I used sudo command which allowed me to read /flag in root.

**Code:**        
```bash
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{wk7j7rmo1kSiBCh0QH9TS8e-thS.dhTN0UDLzcTN0czW}
```