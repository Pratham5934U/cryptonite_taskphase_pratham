# 1. Chaining with Semicolons

**Flag:**    
pwn.college{osNB4N9lWjFGtuXpBJZcbpTLRfJ.dVTN4QDLzcTN0czW}

**Procedure:**    
I used ' ; ' to chain the execution statement of pwn and college in challenge.

**Code:**           
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{osNB4N9lWjFGtuXpBJZcbpTLRfJ.dVTN4QDLzcTN0czW}
```

# 2. Your First Shell Script

**Flag:**    
pwn.college{wd-RSiCT6jCcHQ6AN2eM8v99fge.dFzN4QDLzcTN0czW}

**Procedure:**    
Here I struggled a little in getting it that I had to use to write the execution statements in shell script x.sh and then I used bash x.sh to run it and get the flag.

**Code:**           
```
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{wd-RSiCT6jCcHQ6AN2eM8v99fge.dFzN4QDLzcTN0czW}
```

# 3. Redirecting Script Output

**Flag:**    
pwn.college{YgAddJzJwz1RfLil4v9Nrx2inU8.dhTM5QDLzcTN0czW}

**Procedure:**    
Here first I created and edited the shell script p.sh and wrote the commands '/challenge/pwn' and '/challenge/college' and then piped the output to /challenge/solve.

**Code:**           
```
hacker@chaining~redirecting-script-output:~$ nano p.sh
hacker@chaining~redirecting-script-output:~$ bash p.sh | /challenge/solve 
Correct! Here is your flag:
pwn.college{YgAddJzJwz1RfLil4v9Nrx2inU8.dhTM5QDLzcTN0czW}
```

# 4. Executable Shell Scripts

**Flag:**    
pwn.college{Am7DzFA7GPKu4WL0VpIaQW8Mkxl.dRzNyUDLzcTN0czW}

**Procedure:**    
This challenge required me to creat a shell script with /challenge/solve in it so that I can invoke it while execution that script but this time I could not use bash so I had to make 
the script executable using chmod command and then executed it using it's relative path.

**Code:**           
```
hacker@chaining~executable-shell-scripts:~$ nano p.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x p.sh
hacker@chaining~executable-shell-scripts:~$ ./p.sh
Congratulations on your shell script execution! Your flag:
pwn.college{Am7DzFA7GPKu4WL0VpIaQW8Mkxl.dRzNyUDLzcTN0czW}
```
