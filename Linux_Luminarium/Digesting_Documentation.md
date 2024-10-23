# 1. Learning from documentation

**Flag:**    
pwn.college{MyfvzKKb6HCumPGW9fyj9R-m9s2.dRjM5QDLzcTN0czW}   

**Procedure:**     
I just had to pass a argument '--giveflag'.

**Code:** 
```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag        
Correct argument! Here is your flag:         
pwn.college{MyfvzKKb6HCumPGW9fyj9R-m9s2.dRjM5QDLzcTN0czW}
```

# 2. Learning Complex Usage

 **Flag:**          
pwn.college{EZUEWoxgeUqjOAsIidiFk9UD_cS.dVjM5QDLzcTN0czW}

 **Procedure:**           
Here i had to pass two arguments to /challenge/challenge that were '--printfile' and '/flag' this was to specify the particular file.

 **Code:**     
```bash
hacker@man~learning-complex-usage:~$ /challenge/challenge  --printfile /flag        
Correct argument! Here is the /flag file:       
pwn.college{EZUEWoxgeUqjOAsIidiFk9UD_cS.dVjM5QDLzcTN0czW}
```

# 3. Reading Manuals5

**Flag:**
pwn.college{EEh87YDlJgMvz3DFdvbYhf10b-X.dRTM4QDLzcTN0czW}

**Procedure:**    
I had to just read through the manual and found the argument to pass to '/challenge/challenge' in order to get the flag.

**Code:**
```bash
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                                                                     Challenge Commands                                                                                     CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --hlgvzd NUM
              print the flag if NUM is 873

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                                                           May 2024                                                                                          CHALLENGE(1)
hacker@man~reading-manuals:~$ 
hacker@man~reading-manuals:~$ /challenge/challenge --hlgvzd 873
Correct usage! Your flag: pwn.college{EEh87YDlJgMvz3DFdvbYhf10b-X.dRTM4QDLzcTN0czW}
```

# 4. Searching Manuals 

**Flag**   
Correct usage! Your flag: pwn.college{AaekJ0fAbOk_-mJ7Ptv53WrVLsE.dVTM4QDLzcTN0czW}

**Procedure**   
We can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, hit n to go to the next result and N to go to the previous result. Instead of /, 
we can use ? to search backwards. Afetr opening the manual i searched for word flag using '/flag' command and found the required argument then pressed 'q' to exit from the manual and type 
passed the required comman to '/challenge/challenge'.

**Code:**
```bash
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ 
hacker@man~searching-manuals:~$ 
hacker@man~searching-manuals:~$ /challenge/challenge  --sybce
Initializing...
Correct usage! Your flag: pwn.college{AaekJ0fAbOk_-mJ7Ptv53WrVLsE.dVTM4QDLzcTN0czW}
```

# 5. Searching for Manuals 

**Flag:**   
pwn.college{IKJvYWL91K_yKRiE5I-20fmIciy.dZTM4QDLzcTN0czW}

**Procedure:**      
First I used 'man man' command to figure out which manpage to search but then I saw a bunch of commands when I search for them I got to know that command 'man -k "reqeexp" ' is used to 
search a particular keyword in the description of manuals. I used this to search for the keyword 'challenge' and got the required manual name where I got the argument which I passed to
'/challenge/challenge' to get the flag.

Source : https://docs.oracle.com/cd/E23824_01/html/821-1451/gkyre.html#:~:text=To%20search%20a%20specific%20man,%2Dk%20or%20%2DK%20option.&text=Note%20%2D%20Keywords%20are%20contained%20within%20double%20quotation%20marks.

**Code:**
```bash
acker@man~searching-for-manuals:~$ man man
MAN(1)                                                                                           Manual pager utils                                                                                           MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man  is  the  system's manual pager.  Each page argument given to man is normally the name of a program, utility or function.  The manual page associated with each of these arguments is then found and dis‐
       played.  A section, if provided, will direct man to look only in that section of the manual.  The default action is to search in all of the available sections following a pre-defined order (see  DEFAULTS),
       and to show only the first page found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
hacker@man~searching-for-manuals:~$ 
hacker@man~searching-for-manuals:~$ man -k challenge
vyifmciydz (1)       - print the flag!
hacker@man~searching-for-manuals:~$  man vyifmciydz (1)
bash: syntax error near unexpected token `('
hacker@man~searching-for-manuals:~$ man vyifmciydz

CHALLENGE(1)                                                                                     Challenge Commands                                                                                     CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --vyifmc NUM
              print the flag if NUM is 915

AUTHOR
       Written by Zardus.
hacker@man~searching-for-manuals:~$ 
hacker@man~searching-for-manuals:~$ /challenge/challenge --vyifmc 915
Correct usage! Your flag: pwn.college{IKJvYWL91K_yKRiE5I-20fmIciy.dZTM4QDLzcTN0czW}
```

# 6. Helpful Programs

**Flag:**   
pwn.college{AUb--AvfOIce79BYvTG3ALy7_1T.ddjM4QDLzcTN0czW}

**Procedure:**    
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. So in this challenge I use '--help' argument to read the program's documentation
so I was able to get knowledge about more argumnets which helped my way to flag.

**Code:**     
```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 793
hacker@man~helpful-programs:~$ /challenge/challenge -g 793
Correct usage! Your flag: pwn.college{AUb--AvfOIce79BYvTG3ALy7_1T.ddjM4QDLzcTN0czW}
```

# 7. Help for Builtins

**Flag:**    
pwn.college{0KDsSRR2D79ap-fwfiXS68bkKh6.dRTM5QDLzcTN0czW}

**Procedure:**    
Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, 
but the shell handles them internally instead of launching other programs. We can get a list of shell builtins using help and a specific one by passing it to builtin help.
In this challenge, I had to practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, I had 
to lookup its help to figure out the secret value to pass to it! So first I passed 'challenge' to help to get to know it's use then I passed the secret value to builtin challenge 
to get the flag.

**Code:**  
```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "0KDsSRR2".
hacker@man~help-for-builtins:~$ challenge --secret 0KDsSRR2
Correct! Here is your flag!
pwn.college{0KDsSRR2D79ap-fwfiXS68bkKh6.dRTM5QDLzcTN0czW}
```
