#Writeup

##Level 0
Using ssh command to connect to the host on port 2220 with username bandit0 and password is bandit0 for this level
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0
```

##Level 1
used ```ls``` command to find the file "readme" then used ```cat readme```. password is ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

##Level 2
used ```cat ./-``` , password is 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

##Level 3
used '\' after every word to compensate for spaces as otherwise it wouldn't work.
used ```cat spaces\ in\ this\ filename``` . password is MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

##Level 4
for hidden files used ```ls -a```. then used ```cd inhere``` to change directory. using ```ls -a``` again then found the hidden file '...Hiding -From-You'. password is 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

##Level 5

```
ls
cd inhere
file ./-file01
file ./-file02
file ./-file03
file ./-file04
file ./-file05
file ./-file06
file ./-file07
```
we found data of file07 to be ASCII ext.
```cat ./-file07```
password is 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

##Level 6
there are many files present. we can find the suitable file using ```find . -type f -size 1033c -readable ! -executable```. which gives "./maybehere07/.file2" which gives us the password- HWasnPhtq9AVKe0dmk45nxy20cvUa6EG 

##Level 7
finding the specific file of the specific size,given owner and group using ```find / -type f -size 33c -user bandit7 -group bandit6``` we get a lot of files and inbetween them "/var/lib/dpkg/info/bandit7.password"
opening it by ```cat /var/lib/dpkg/info/bandit7.password``` gives the password morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj


##Level 8
To find a particular word we use "grep" command.
using ```grep -r millionth "data.txt" ``` we get the password - dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

##Level 9

first sorted the passwords then used uniq command because it only works when repeating phrases are adjacent 
```sort data.txt | uniq -u```
password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

##Level 10
used ```strings data.txt | grep "==="```
password : FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

##Level 11
used the cmd line ```base64 -d data.txt``` to get the password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

##Level 12
used "tr" command to rotate the letters back
```cat data.txt | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'```
The password is : 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

##Level 13 
creating a dir inside tmp
```mkdir /tmp/joe```
copying data and reversing hex dump
```
cp data.txt /tmp/joe
cd /tmp/joe
file data.txt
xxd -r data.txt dataa
file dataa
```
changing datatype,decompressing and repeating
```
mv dataa data1.gz
gzip -d data1.gz
file data1.gz
mv data1 data2.bz2
bzip2 -d data2.bz2
file data2
mv data2 data3.gz
gzip -d data3.gz
file data3
```
data3 is POSIX tar archive, so to decompress it
```tar -xf data3```
checking file type of extrated file
```
ls
file data5.bin
```
it is again POSIX tar archive, so repeating steps-
```
tar -xf data5.bin
file data6.bin
mv data6.bin data7.bz2
bzip2 -d data7.bz2
tar -xf data7
file data8.bin
mv data8.bin data9.gz
gzip -d data9.gz
file data9
```
file type of data9 is ASCII text. opening it gives the password:FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

##Level 14
 to connect using local host used
```ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220```
we reach next level

##Level 15
to get password used ```cat /etc/bandit_pass/bandit14```
password: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

to get password for next level used ```nc localhost 30000```
password: nc localhost 30000






