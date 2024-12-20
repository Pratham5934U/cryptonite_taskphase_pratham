## 1. C3

### **Flag-**      
picoCTF{adlibs}

 ### **Thought Process-**
 > In this challenge I was given a ciphered text and an encoder program. In order to decode the ciphered text i just reversed the program given then I got a new python
  program, now the problem was what input I had to given so according to the commnets it had i.e. self input I tried to input the whole program itself and it worked I 
  got the flag.

**Ciphered Text-**    
`DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl`

**Encoder-**      
```bash
import sys
chars = ""
from fileinput import input
for line in input():
  chars += line

lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""

prev = 0
for char in chars:
  cur = lookup1.index(char)
  out += lookup2[(cur - prev) % 40]
  prev = cur

sys.stdout.write(out)
```

**Decoder made-**       
```bash
import sys
chars = "DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl"


lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""
temp = ""

prev = 0
for char in chars:
  cur = lookup2.index(char)
  temp = lookup1[(cur + prev) % 40]
  out += temp
  prev = lookup1.index(temp)

sys.stdout.write(out)
```

**New Python Program obtained-** 
```bash
#asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print (chars[i]) #prints
        b += 1 / 1
```

## 2. Custom encryption

### **Flag-**       
picoCTF{custom_d2cr0pt6d_751a22dc}

### **Thought Process-**     
> Here I went through the the given custom encryption program, understood it and then made a decryption program for that custom encryption and got the flag.

**Ciphered Text-**          
`260307, 491691, 491691, 2487378, 2516301, 0, 1966764, 1879995, 1995687, 1214766, 0, 2400609, 607383, 144615, 1966764, 0, 636306, 2487378, 28923, 1793226, 694152, 780921, 173538, 173538, 491691, 173538, 751998, 1475073, 925536, 1417227, 751998, 202461, 347076, 491691`

**Encryption Program(with some changes that I did for my convenience)**    
```bash
from random import randint
import sys


def generator(g, x, p):
    return pow(g, x) % p


def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(((ord(char) * key*311)))
    return cipher


def is_prime(p):
    v = 0
    for i in range(2, p + 1):
        if p % i == 0:
            v = v + 1
    if v > 1:
        return False
    else:
        return True


def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def test(plain_text, text_key):
    p = 97
    g = 31
    if not is_prime(p) and not is_prime(g):
        print("Enter prime numbers")
        return
    a = 94 #randint(p-10, p)
    b = 29 #randint(g-10, g)
    print(f"a = {a}")
    print(f"b = {b}")
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    else:
        print("Invalid key")
        return
    semi_cipher = dynamic_xor_encrypt(plain_text, text_key)
    cipher = encrypt(semi_cipher, shared_key)
    print(f'cipher is: {cipher}')
    print(f'shared key {shared_key}')


if __name__ == "__main__":
    message = sys.argv[1]
    test(message, "trudeau")

## a = 87
#b = 24
#cipher is: [806112, 895680, 746400, 29856, 388128]
#shared key 96
```

**Decryption Program**      
```bash
def dynamic_xor_decrypt(ciphertext, text_key):
    plain_text = ""
    key_length = len(text_key)
    for i, char in enumerate(ciphertext):
        key_char = text_key[i % key_length]
        decrypted_char = chr(char ^ ord(key_char))  
        plain_text += decrypted_char
    return plain_text

def decrypt(cipher, text_key, shared_key):
    semi_cipher = [char // (shared_key * 311) for char in cipher]
    plain_text = dynamic_xor_decrypt(semi_cipher, text_key)
    return plain_text

def decrypt_ciphertext():
    # Input ciphertext (as a list of integers)
    cipher = input("Enter the ciphertext (comma-separated integers): ")
    cipher = [int(x.strip()) for x in cipher.split(",")]

    text_key = input("Enter the text key: ")
    shared_key = int(input("Enter the shared key: "))

    decrypted_text= decrypt(cipher, text_key, shared_key)
    reverse_decrypted_text = decrypted_text[::-1]
    print(f"Decrypted Text: {reverse_decrypted_text}")

if __name__ == "__main__":
    decrypt_ciphertext()

```

## 3. miniRSA

### **Flag-**    
picoCTF{n33d_a_lArg3r_e_ccaa7776}

### **Thought Process-**    
> In this challenge, it was the value of `n` which was creating a problem it was so big that it was too difficult to find out `p` and `q`, I tried many programs from the simple RSA decryption program to advavance algorithms such as `Elliptic Curve Method (ECM)`, `Quadratic Sieve` utilising `RsaCtfTool`, `factordb` to find out values of `p`, `q` or the required flag. I then started again and found out a rsa cipher tool `dcode.fr` with the help of which I got my flag.

### **Sources-**
1. RsaCtfTool: https://github.com/RsaCtfTool/RsaCtfTool/blob/master/RsaCtfTool.py
2. Factordb: https://factordb.com
3. dcode.fr: https://www.dcode.fr/rsa-cipher

   
