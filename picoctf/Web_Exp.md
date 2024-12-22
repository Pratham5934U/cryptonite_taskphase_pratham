## 1. SOAP

### **Flag-**     
picoCTF{XML_3xtern@l_3nt1t1ty_e79a75d4}

### **Thought Process-**         
> Here I used the help of `PayloadsAllTheThings` to find out the flag everthing was clearly written in the readme file.

### **Working-**    
![Use of Burp suite](/Images/Web_exp_SOAP.png)

## 2. Forbidden Paths

### **Flag-**       
picoCTF{7h3_p47h_70_5ucc355_e5fe3d4d}

### **Thought Process-**        
 > Here I first observed that it was just reading the file name so I tried `flag.txt` but it showed `not authorized`, then I tried `/flag.txt` it again showed me
  `not authorised` then I understood the meaning of `the website is filtering absolute file paths` and that I was in `/usr/share/nginx/html/` so I thought maybe
  if I cannot provide the adsolute path then I can try relative path so I tried `../../../../flag.txt` and it worked and I got my flag. But before all this I tried
 `Burp suit` to see if I can observe anything but I could not find anything.
