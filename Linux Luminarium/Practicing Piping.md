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


**Procedure:**   


**Code:**  
```

```


# 5.  

**Flag:**   


**Procedure:**   


**Code:**  
```

```


# 6. 

**Flag:**   


**Procedure:**   


**Code:**  
```

```


# 7.  

**Flag:**   


**Procedure:**   


**Code:**  
```

```


# 8.  

**Flag:**   


**Procedure:**   


**Code:**  
```

```


# 9.  

**Flag:**   


**Procedure:**   


**Code:**  
```

```
