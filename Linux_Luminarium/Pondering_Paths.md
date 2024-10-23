# 1. The Root

**Flag:**  
pwn.college{YskNYpLaAzmi1p5BR-CEiHXKBHF.dhzN5QDLzcTN0czW}

**Procedure:**   
In Linux filesystem to refer any files we need to provide exact path i.e. location of the file and the path start with "/" and in order to descend further into the files we 
need to use "/" symbol again after typing the exact and the correct path we press enter. In the challenge 'The Root' a program was already added in / nammed as pwn so I had to just 
type the absolute path of the program pwn in the terminal to get the flag. The absolute path was /pwn .


# 2. Program and absolute paths

**Flag:**
pwn.college{Evb1fhTKrRrV6fZIlmD7ZDBGCqk.dVDN1QDLzcTN0czW}

**Procedure:**
In this challenge the I had to execute the program named 'run' which is in the directory 'challenge' which was in turn in the root directory so my absolute path was /challenge/run .
On typing this absolute path and after pressing enter I got the flag.

# 3. Position thy self

**Flag:**
pwn.college{8BiogCA4DND03vYoxftO8RNiwCD.dZDN1QDLzcTN0czW}

**Procedure:**
```bash
hacker@paths~position-thy-self:~$ cd /challenge
hacker@paths~position-thy-self:/challenge$ cd /run
hacker@paths~position-thy-self:/run$ /
bash: /: Is a directory
hacker@paths~position-thy-self:/run$ cd /
hacker@paths~position-thy-self:/$ ./challenge/run
Incorrect...
You are not currently in the /home directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/$ cd /home directory
bash: cd: too many arguments
hacker@paths~position-thy-self:/$ /home directory
bash: /home: Is a directory
hacker@paths~position-thy-self:/$ cd /home
hacker@paths~position-thy-self:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8BiogCA4DND03vYoxftO8RNiwCD.dZDN1QDLzcTN0czW}
hacker@paths~position-thy-self:/home$ 
```

# 4. Position elsewhere

**Flag**
pwn.college{EaUc5PdvPsY-4EZFy68M7oL0NbJ.ddDN1QDLzcTN0czW}

**Procedure**
```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /home directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /home
hacker@paths~position-elsewhere:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{EaUc5PdvPsY-4EZFy68M7oL0NbJ.ddDN1QDLzcTN0czW}
hacker@paths~position-elsewhere:/home$ 
```

# 5. Position yet elsewhere

**Flag**
pwn.college{QFw6dbIXu-VcTb8eX1pV3hSjW2_.dhDN1QDLzcTN0czW}

**Procedure**
```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia directory.
bash: cd: too many arguments
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia directory
bash: cd: too many arguments
hacker@paths~position-yet-elsewhere:~$ /usr/share/zoneinfo/posix/Aisa
bash: /usr/share/zoneinfo/posix/Aisa: No such file or directory
hacker@paths~position-yet-elsewhere:~$ /usr/share/zoneinfo/posix
bash: /usr/share/zoneinfo/posix: Is a directory
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/zoneinfo/posix
hacker@paths~position-yet-elsewhere:/usr/share/zoneinfo/posix$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-yet-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QFw6dbIXu-VcTb8eX1pV3hSjW2_.dhDN1QDLzcTN0czW}
```



# 6. Implicit relative paths, from /

**Flag**
pwn.college{UcArH4H40TVR4n0tEVbUsptpJaJ.dlDN1QDLzcTN0czW}

**Procedure**
```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ c
bash: c: command not found
hacker@paths~implicit-relative-paths-from-:/$ /c
bash: /c: No such file or directory
hacker@paths~implicit-relative-paths-from-:/$ cd c
bash: cd: c: No such file or directory
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{UcArH4H40TVR4n0tEVbUsptpJaJ.dlDN1QDLzcTN0czW}
hacker@paths~implicit-relative-paths-from-:/$ 
```

# 7. Explicit relative paths, from /

**Flag**
pwn.college{8R_JKEZy5B4oX7Dapsw8_JzfIdi.dBTN1QDLzcTN0czW}

**Procedure**
```bash
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{8R_JKEZy5B4oX7Dapsw8_JzfIdi.dBTN1QDLzcTN0czW}
```

# 8. Implicit relative path

**Flag**
pwn.college{0KVWhfIpbvCE8jGs1-2W301Okrj.dFTN1QDLzcTN0czW}

**Procedure** 
```bash
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
bash: run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0KVWhfIpbvCE8jGs1-2W301Okrj.dFTN1QDLzcTN0czW}
```

# 9. Home sweet home

**Flag**
pwn.college{87ehKGMg_Rinjv-YdEChtrAdkoR.dNzM4QDLzcTN0czW}

**Procedure**
```bash
hacker@paths~home-sweet-home:~$ /challenge/run
You must provide an argument to /challenge/run when you invoke it!
hacker@paths~home-sweet-home:~$ /challenge/run ~/copy
The argument you provided must not have been longer than 3 characters (it's 
currently 6 characters long)!
hacker@paths~home-sweet-home:~$ /challenge/run ~/bre
The argument you provided must not have been longer than 3 characters (it's 
currently 5 characters long)!
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{87ehKGMg_Rinjv-YdEChtrAdkoR.dNzM4QDLzcTN0czW}
```