# BANDIT

## level 0
ssh into level 0 using  ssh bandit0@bandit.labs.overthewire.org -p 2220 with password bandit0.

## level 0 &#8594; level 1
The password was stored in a readme located in home directory. I had to raed it using cat and use that password to SSH into next level and continue the game.

## level 1 &#8594; level 2
The password for going onto next level was located in sos read it using `cat ./-` and SSH into the next level.
Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## level 2 &#8594; level 3
The file name contained spaces so it's name had to quoted thus command `cat ./"spaces in this filename"`
Password:  MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
## level 3 &#8594; level 4
Changed the directory to 'inhere' and then listed the hidden files using `ls -a` and found the file "...Hiding-From-You" read it using `cat ./...Hiding-From-You`
Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## level 4 &#8594; level 5
Changed the directory to 'inhere' then listed all the files and read each one of then one by one using `cat` and found that "-file07" was the only human readible file and had the password.
Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## level 5 &#8594; level 6
First entered into the directory using `cd` then used `find ./ -size 1033c` to get the file of 
size 1033 bytes and found only one file used `cat` to get the password.
Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## level 6 &#8594; level 7


## level 7 &#8594; level 8



## level 8 &#8594; level 9


## level 9 &#8594; level 10
