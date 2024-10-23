# 1. Redirecting Output

**Flag:**    
pwn.college{0spdNvHg94S3tc_p85cJmgn-o9_.dRjN1QDLzcTN0czW}

**Procedure:**   
In this challenge I just had to redirect the output 'PWN' to file named 'COLLEGE' .

**Code:**    
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{0spdNvHg94S3tc_p85cJmgn-o9_.dRjN1QDLzcTN0czW}
```
# 2. Redirecting more Output 

**Flag:**   
pwn.college{ojMPUinmJ2ibQ5x-mTuMwnKP86S.dVjN1QDLzcTN0czW}

**Procedure:**   
In this challenge I had to redirect the output of '/challenge/run' to file name 'myflag' . 

**Code:**  
```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{ojMPUinmJ2ibQ5x-mTuMwnKP86S.dVjN1QDLzcTN0czW}
```

# 3. Appending Output 

**Flag:**   
pwn.college{cVOiFqCUGM9aW3uUWPtgUMXSuOO.ddDM5QDLzcTN0czW}

**Procedure:**   
In this challenge according to the instruction redirection in truncation mode (>) resulted in the later half of the flag and redirection in append mode (>>) resulted in the whole flag.

**Code:**  
```
hacker@piping~appending-output:~$ /challenge/run > ~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat the-flag
FqCUGM9aW3uUWPtgUMXSuOO.ddDM5QDLzcTN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
hacker@piping~appending-output:~$ /challenge/run >> ~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{cVOiFqCUGM9aW3uUWPtgUMXSuOO.ddDM5QDLzcTN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```


# 4.  Redirecting errors

**Flag:**   
 pwn.college{wylSSEz2TctHuPQdP28TcIkvmmi.ddjN1QDLzcTN0czW}

**Procedure:**   
I had to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions and then use the cat command to get the flag.

**Code:**  
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{wylSSEz2TctHuPQdP28TcIkvmmi.ddjN1QDLzcTN0czW}
```


# 5.  Redirecting Input

**Flag:**   
pwn.college{oxr3DTgHvwpbjisuhASHdf6uEmN.dBzN1QDLzcTN0czW}

**Procedure:**   
In this challenge I was to required to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!_

**Code:**  
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run <PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{oxr3DTgHvwpbjisuhASHdf6uEmN.dBzN1QDLzcTN0czW}
```


# 6. Grepping stored results 

**Flag:**   
pwn.college{QZ8XVHMOPtLthpg1zLgFQRH33jk.dhTM4QDLzcTN0czW}

**Procedure:**   
In this thing challenge I had to do a number of things-
(1) Redirect the output of /challenge/run to /tmp/data.txt.
(2)This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
(3)Grep that for the flag!

**Code:**  
```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$  grep -i "pwn.college" /tmp/data.txt
pwn.college{QZ8XVHMOPtLthpg1zLgFQRH33jk.dhTM4QDLzcTN0czW}
```


# 7.  Grepping Live output

**Flag:**   
pwn.college{YnQRyCGBWUkhweG0iRwCrlXV2RK.dlTM4QDLzcTN0czW}

**Procedure:**   
Here I had to grep flag from '/challenge/run' which resulted in a thosand lines on executing it.

**Code:**  
```
hacker@piping~grepping-live-output:~$  /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{YnQRyCGBWUkhweG0iRwCrlXV2RK.dlTM4QDLzcTN0czW}
```


# 8.  Grepping Errors

**Flag:**   
pwn.college{Mr00H0Oc42t2eKw2ZRAi0Ajgelg.dVDM5QDLzcTN0czW}

**Procedure:**   
This time I had to use >& operator, which redirects a file descriptor to another file descriptor. This means that there is a two-step process to grep through errors: first, redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|). I had to grep through standard error to find the flag.

**Code:**  
```
hacker@piping~grepping-errors:~$  /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Mr00H0Oc42t2eKw2ZRAi0Ajgelg.dVDM5QDLzcTN0czW}
```


# 9.  Duplicating piped data with tee

**Flag:**   
pwn.college{A_KkXe0PPI-guGNs4e7UdYPWaWh.dFjM5QDLzcTN0czW}

**Procedure:**    
Here the data in /challenge/pwn had to be piped into /challenge/college and I aslo had to intercept the dat in order to see what pwn needed from me.

**Code:**  
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee output | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "A_KkXe0P"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret A_KkXe0P | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{A_KkXe0PPI-guGNs4e7UdYPWaWh.dFjM5QDLzcTN0czW}
```

# 10.  

**Flag:**   
pwn.college{UR1U6ZgkXxRukcbFWIjSmE_C-_3.dBDO0UDLzcTN0czW}

**Procedure:**   
tee designed to write to files and to standard output it is used to duplicate data to a file and a command or duplicate data to two files.In this challenge, I had /challenge/hack, /challenge/the, and /challenge/planet. I had to run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands.

**Code:**  
```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{UR1U6ZgkXxRukcbFWIjSmE_C-_3.dBDO0UDLzcTN0czW}
```

# 11.  Split-piping stderr and stdout

**Flag:**   
pwn.college{YkqWq_DzKxHgVyRaBqXGhtQH2QN.dFDNwYDLzcTN0czW}

**Procedure:**   
In this challenge I had to      
1. /challenge/hack: this produces data on stdout and stderr      
2. /challenge/the: you must redirect hack's stderr to this program       
3. /challenge/planet: you must redirect hack's stdout to this program     
I I tried to redirect hack's stderr and stdout individually but it did not work so I wrote the whole command I one line and got the flag. 

**Code:**  
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the)
You must redirect my standard output into '/challenge/planet'!
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 1> >(/challenge/planet)
You must redirect my standard error into '/challenge/the'!
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{YkqWq_DzKxHgVyRaBqXGhtQH2QN.dFDNwYDLzcTN0czW}
```
