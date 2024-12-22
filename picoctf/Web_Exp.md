## 1. SOAP

### **Flag-**     
picoCTF{XML_3xtern@l_3nt1t1ty_e79a75d4}

### **Thought Process-**         
> Here I used the help of `PayloadsAllTheThings` to find out the flag everthing was clearly written in the readme file.

### **Working-**    
![Use of Burp suite](/Images/Web_exp_SOAP.png)


---
## 2. Forbidden Paths

### **Flag-**       
picoCTF{7h3_p47h_70_5ucc355_e5fe3d4d}

### **Thought Process-**        
 > Here I first observed that it was just reading the file name so I tried `flag.txt` but it showed `not authorized`, then I tried `/flag.txt` it again showed me
  `not authorised` then I understood the meaning of `the website is filtering absolute file paths` and that I was in `/usr/share/nginx/html/` so I thought maybe
  if I cannot provide the adsolute path then I can try relative path so I tried `../../../../flag.txt` and it worked and I got my flag. But before all this I tried
 `Burp suit` to see if I can observe anything but I could not find anything.


---
## 3. cookies 

### **Flag-**        
picoCTF{3v3ry1_l0v3s_c00k135_88acab36}

### **Thought Process-**         
> Here the  hint was `cookies` so just when on inspect and tried to locate cookies there was a only one tab which had two things suspicious `name` and `value` so I just tried entering the name `flag` and reload but did work as I thought so then I changed the value to `5` and reloaded again so I got a new cookie then I understood that if I get the correct value I can get the flag maybe so I tried to automate this using `Burp suite` but I was unable to get to how to do it so I tried manual way.
It was obvious that I such a situation first I had to find till what numbers were the cookies so I tried to find it by entering random values and got to know that there were different cookies till 28 and after that it showed `invalid` so since it could be done manually so I got the flag by inputing all the values. 
