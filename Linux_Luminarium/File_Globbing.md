# 1.Matching with *

**Flag:**   
pwn.college{kyhqfBOX6N1ydbOK2N3jyTNX8Q2.dFjM4QDLzcTN0czW}

**Procedure:**    
First I used 'cd' command and passed '/ch*' to change the directory and then use '/challenge/run'. 

**Code:**    
```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kyhqfBOX6N1ydbOK2N3jyTNX8Q2.dFjM4QDLzcTN0czW}
```

# 2. Matching with ?

**Flag:**     
pwn.college{gcLJPHOavuhaHbYaE9QZNuC0Q_W.dJjM4QDLzcTN0czW}

**Procedure:**   
Here I had to use '?' inplace of 'c' and 'h' and use 'cd' command first then '/challenge/run'

**Code:**
```bash    
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{gcLJPHOavuhaHbYaE9QZNuC0Q_W.dJjM4QDLzcTN0czW}
```

# 3. Matching with []

**Flag:**    
pwn.college{s1VbfUOCX5wFEGupzrI2EDv8u1L.dNjM4QDLzcTN0czW}

**Procedure:**             
In this challenge I had toh change directory to '/challenge/files' then run '/challenge/run [bash]' so the characters b, a, s and h get matched which were in the name of files file_b, 
file_a, file_s, and file_h

**Code:**     
```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{s1VbfUOCX5wFEGupzrI2EDv8u1L.dNjM4QDLzcTN0czW}
```

# 4. Matching Paths with []

**Flag:**       
pwn.college{opcPK_SXh70BpcaMiGbGQb-Aci0.dRjM4QDLzcTN0czW}

**Procedure:**        
Here I had to run a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files

**Code:**         
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{opcPK_SXh70BpcaMiGbGQb-Aci0.dRjM4QDLzcTN0czW}
```

# 5. Mixing Globs

**Flag:**     
pwn.college{k_9rOqHkA2OG-wp_puzbx6RHxij.dVjM4QDLzcTN0czW}

**Procedure:**       
In this challenge after changing the directory I first tried to get the files using [n] but the expansion was not successful, I also tried using [in] but again failed after that I 
tried [pec]* and I got the flag, what this argument did was that it match the files with the first character p, e or c.

**Code:**       
```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [n]
Your expansion did not expand to the requested files (challenging, educational, 
pwning). Instead, it expanded to:
[n]
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [in]
Your expansion did not expand to the requested files (challenging, educational, 
pwning). Instead, it expanded to:
[in]
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [pec]*
You got it! Here is your flag!
pwn.college{k_9rOqHkA2OG-wp_puzbx6RHxij.dVjM4QDLzcTN0czW}
```

# 6. Exclusionary globbing

**Flag:**     
pwn.college{8mxZWJycwfo5josfYqi_TrRcLv1.dZjM4QDLzcTN0czW}

**Procedure:**      
Here I had to just do not match the files which start with character p, w and n using [^pwn]* .

**Code:**       
```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{8mxZWJycwfo5josfYqi_TrRcLv1.dZjM4QDLzcTN0czW}
```