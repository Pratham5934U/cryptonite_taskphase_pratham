## 1. trivial flag transfer protocol

### **Flag-**      
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

### **Thought Process-**       
> Here first of all I exported the `TFTP packages` with which I got some files, 3 pictures, 2 test files and 1 deb file. The 2 text files(instructions.txt,plan.txt)
  had cipher text in `ROT-13 cipher` from which I got the password and then I inspected deb file where I found a `steghide` file which gave me the hint to use this tool
  and I was able to extract the flag from the picture.


## 2. tunn3l v1s10n

### **Flag-**     
picoCTF{qu1t3_a_v13w_2020}

### **Thought Process-**    
> With the help of Hex editor I came to know that it was a `bmp` file, it started with `BM`, which was corrupted so I had to figure out the right changes to be done
 to fix,after doing the necessary changes I was able to get the flag in the picture.

### **Changes done in Hex Editor-**
![Modifications in hex editor]()

### **Picture after modification-**   
![Flag pic]()


## 3. m00nwalk

### **Flag-**    
picoCTF{beep_boop_im_in_space}

### **Thought Process-**        
> Here with help of first clue I found out it was an image encoded in the form of audio and second clue gave me the hint that something named as `Scottie` was related to
  to it so I started searching for `audio to image decoder` first I found `noaa-apt image decoder` I downloaded it but it did not give any output, then I went across
  `sstv_decoder` I tried to understand the Github `readme.md` file but I was not able to understand it then I came across a mobile app `Robot36` which gave an image
  output which had the flag.

### **Output-**
![Output]()

### **Sources that I went across-**  
1. noaa-apt: https://noaa-apt.mbernardi.com.ar/
2. sstv_decoder: https://github.com/davidhoness/sstv_decoder/blob/master/README.md
3. Robot36: https://play.google.com/store/apps/details?id=xdsopl.robot36&hl=en_IN
