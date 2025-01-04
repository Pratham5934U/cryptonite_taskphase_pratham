## **1. HideToSee**

### **Flag-**     
picoCTF{atbash_crack_1f84d779}

### **Thought Process-**        
> It was clear from the challenge name that some data was hidden in the image so I tried finding it using binwalk,exiftool,zsteg finally found it using `steghide`. The data was `krxlXGU{zgyzhs_xizxp_1u84w779}`, the image made it clear that it was an encrypted text using `atbash cipher` itself so I deccoded it manually and got the flag.>

## **2. Vigenere**

### **Flag-**     
picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_ae82272q}

### **Thought Process-**         
> It was clear from the hint that it was a `Vigenere Cipher` so I had to just decode it.

### **Decoded text-**         
![decoded using dcode.fr]()
