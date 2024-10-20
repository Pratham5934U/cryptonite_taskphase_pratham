# BANDIT

## level 0
ssh into level 0 using  **`ssh bandit0@bandit.labs.overthewire.org -p 2220`** with password **`bandit0`**.

## level 0 &#8594; level 1
The password was stored in a `readme` located in home directory. I had to read it using cat and use that password to SSH into next level and continue the game.
<br>**Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If**

## level 1 &#8594; level 2
The password for going onto next level was located in sos read it using `cat ./-` and SSH into the next level.
<br>**Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx**

## level 2 &#8594; level 3
The file name contained spaces so it's name had to quoted thus command `cat ./"spaces in this filename"`
<br>**Password:  MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx**

## level 3 &#8594; level 4
Changed the directory to 'inhere' and then listed the hidden files using `ls -a` and found the file "...Hiding-From-You" read it using `cat ./...Hiding-From-You`
<br>**Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ**

## level 4 &#8594; level 5
Changed the directory to 'inhere' then listed all the files and read each one of then one by one using `cat` and found that "-file07" was the only human readible file and had the password.
<br>**Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw**

## level 5 &#8594; level 6
First entered into the directory using `cd` then used `find ./ -size 1033c` to get the file of 
size 1033 bytes and found only one file used `cat` to get the password.
<br>**Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG**

## level 6 &#8594; level 7
Used `find ~ -user bandit7 -group bandit6 -size 33c` to search then file with exact same properties and in the whole list of files which I got there was only one file whose permission was not denied and this was the file which contain the password.
<br>**Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj**

## level 7 &#8594; level 8
First I founnd out the location of file using `find` then I tried to `cat` it and it was too long to find that specific word so to find out that specific word I used `grep` command and Got the password.
```bash
bandit7@bandit:~$ grep "millionth" data.txt
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
<br>**Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc**

## level 8 &#8594; level 9
Here first I tried to overwrite the sorted output to data.txt using `sort data.txt -o data.txt` but it was not permitted so then I piped the sorted output to the command which displayed only the line which occured only once, and the command for this was ``sort data.txt | uniq -u`
<br>**Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM**

## level 9 &#8594; level 10
Here I made use of `strings` and piped the out used grep to get all the human readable strings which starts with "=". I got the following output - 
```bash
bandit9@bandit:~$ strings data.txt | grep "="
}========== the
p\l=
;c<Q=.dEXU!
3JprD========== passwordi
qC(=
~fDV3========== is
7=oc
zP=
~de=
3k=fQ
~o=0
69}=
%"=Y
=tZ~07
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
N=~[!N
zA=?0j
```
From here it was clear that what was the password.
<br>**Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey**
