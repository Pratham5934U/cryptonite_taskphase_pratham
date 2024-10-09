# OASIS CFT

# Stairway To Heaven -    
The ground beneath you trembles as Tetris blocks rain from the shadows, cascading down like a storm. At first, panic sets in, but then you realize: these blocks aren't meant to crush 
youâ€”they're your escape. Each piece, carefully arranged, could form a staircase to the control room floating above in the void. It's time to use them strategically and rise to safety. 
Stack the blocks and find your way out!     
Attachment: https://drive.proton.me/urls/NMT01V9DBW#zn1evKwtdD4y
* On opening the link I found out that the file preview was not supported so I had no other option than to download the file. After searching about it on google, can across 
  ELF i.e. Executable and Linkable Format.     
  Source: https://www.baeldung.com/linux/executable-and-linkable-format-file#:~:text=ELF%20is%20short%20for%20Executable,executed%20on%20various%20processor%20types.    
* Then I copied the file to WSL and tried running it but I got this -    
   ```
   pratham@LAPTOP-SDGL4LEJ:~$ ./game
   -bash: ./game: Permission denied
   ```
* Again on searching about this issue on net I came across a new command "chmod +x [filename]"     
   Source: https://stackoverflow.com/questions/40458246/how-do-i-run-an-extensionless-maybe-elf-file-on-ubuntu    
* Gathered some information about this new command from the page link given below.
  Source: https://www.geeksforgeeks.org/chmod-command-linux/
* Ater using the command as required I got the following output -
  ![OUTPUT](https://github.com/Pratham5934U/cryptonite_taskphase_pratham/blob/main/Linux%20Luminarium/crypt.png)
