# Bandit-Overthewire
Bandit Overthewire Solutions

This is my walkthrough of the Bandit Overthewire challanges.

<h1> Level One ---> Level Two </h1>
Level Goal: The password for the next level is stored in a file called - located in the home directory
<br></br>
By reading the level description we can tell that the next level's password is stored in a text file that we're going to have to read thus the only command we will need is <STRONG>cat</STRONG>. The only tricky thing about this level is that the file is named "-" so a simple <STRONG>cat -</STRONG> will not work. We're going to have to specify the file location by using command line prompt: <pre> cat ./- </pre>
<br><br>
With this command we get the password for bandit level two: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

<br></br>
<h1> Level Two ---> Level Three </h1>
Level Goal: The password for the next level is stored in a file called spaces in this filename located in the home directory
<br></br>
So by the level description we can tell that there is a file called "spaces in this filename" so lets run a cat command. Naturally, I type in spaces and then hit tab so I don't have to type the entire file name but we get the surprise below.
<pre> cat spaces\ in\ this\ filename </pre>
So obviously the command wasn't as simple at cat spaces in this filename, but the tab key made it alot easier to circumvent. And with that we now have the password for the next level.
<br><br>
With this command we get the password for bandit level three: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

<br></br>
<h1> Level Three ---> Level Four </h1>
Level Goal: The password for the next level is stored in a hidden file in the inhere directory.
<br></br>
This level is pretty self-explanatory. Requires that you know basic command-line prompts and how to list hidden files. ls -a in this case.
<pre> cd inhere 
 ls -al
 cat .hidden
</pre>
<br><br>
With this command we get the password for bandit level four: 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

<br></br>
<h1> Level Four ---> Level Five </h1>
Level Goal: The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
<br></br>
So we know we're looking for a human readable file which means we're going to have run a file command in the inhere directory and look for whatever file that is ASCII. 
<pre>
cd inhere
ls -al
file ./*
cat ./-file07
</pre>
<br><br>
With this command we get the password for bandit level Five: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

<br></br>
<h1> Level Five ---> Level Six </h1>
Level Goal: The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
human-readable
1033 bytes in size
not executable
<br></br>
So we know we're looking for a file that is 1033 bytes in size so we're going to use the find command along with the -size parameter. 
<pre>
cd inhere
find -size 1033c
cat ./maybehere07/.file2
</pre>
<br><br>
With this command we get the password for bandit level Six: P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

<br></br>
<h1> Level Six ---> Level Seven </h1>
Level Goal: The password for the next level is stored somewhere on the server and has all of the following properties:
owned by user bandit7
owned by group bandit6
33 bytes in size
<br></br>
So we know we're looking for a file that is 33 bytes in size and owned by user bandit7 so we're going to use the find command along with the -size parameter and -user parameter. Also, we know that the file can be anywhere in the server and we weren't given a specific directory so we can start by running cd / and search the root directory.
<pre>
cd /
find -user bandit7 -size 33c (permission denied)
find -user bandit7 -size 33c 2>/dev/null
cat ./var/lib/dpkg/info/bandit7.password
</pre>
There was a roadblock on this level with permissions being denied when searching for the file but due to previous experience, I was able to bypass this with 2>/dev/null
<br><br>
With this command we get the password for bandit level Seven: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

<br></br>
<h1> Level Seven ---> Level Eight </h1>
The password for the next level is stored in the file data.txt next to the word millionth
<br></br>
So based on the level description we know we have to search for the password within the text file and to do this we're going to use grep and search for 'millionth'
<pre>
grep 'millionth' data.txt
</pre>
<br><br>
With this command we get the password for bandit level Eight: TESKZC0XvTetK0S9xNwm25STk5iWrBvP

<br></br>
<h1> Level Eight ---> Level Nine </h1>
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
<br></br>
This level is similar to the previous level in that we must search for the password within the text file but this time we must first sort it and then use the uniq command.
<pre>
sort data.txt | uniq -u
</pre>
<br><br>
With this command we get the password for bandit level Nine: EN632PlfYiZbn3PhVK3XOGSlNInNE00t

<br></br>
<h1> Level Nine ---> Level Ten </h1>
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
<br></br>
Again, we have to search within the file but because the file is a data file, a grep command alone will not be enough. We must extract whatever strings we can from the data.txt file and then pipe it and grep for "======".
<pre>
strings data.txt | grep '======'
</pre>
<br><br>
With this command we get the password for bandit level Ten: G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

<br></br>
<h1> Level Ten ---> Level Eleven </h1>
The password for the next level is stored in the file data.txt, which contains base64 encoded data.
<br></br>
Based on the level description the file is base64 encoded so to find the password we will use the base64 command but with the -d argument to decode the file.
<pre>
base64 -d data.txt
</pre>
<br><br>
With this command we get the password for bandit level Eleven: 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

<br></br>
<h1> Level Eleven ---> Level Twelve </h1>
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
<br></br>
To complete this level as simply as possible, we're going to utilze the resource link which links us to a wiki page on ROT13. We're going to copy and paste the tr command for rot13 and use this command on the file to rotate the letters again that way we get the original text.
<pre>
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
</pre>
<br><br>
With this command we get the password for bandit level Twelve: JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

<br></br>
<h1> Level Twelve ---> Level Thirteen </h1>
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)
<br></br>
Completing this level is going to require us to first make our own directory and copy the data.txt file to this directory. Once that is finished, we will start decompressing this file which will require alot of renaming and various decodings of multiple types of encoding. First we start with a hex dump and name it data1.txt. We then see what kind of file it is by using file and based on what it says we rename it according to the compression method and then decode it with the corresponding command. For instance if a file is said to be gzip then we name it to data1.gz and then run gzip -d data1.gz. Then we get the next file we have to decompress and we keep repeating the process untill we eventually get the file: data8 and can read it to get the password.
<pre>
mkdir /tmp/jurami
cp data.txt /tmp/jurami
xxd -r data.txt data1.txt
mv data1.txt data1.gz
gzip -d data1.gz
mv data1 data2.bz2
bzip2 -d data2.bz2
mv data2 data3.gz
gzip -d data3.gz
mv data3 data3.tar
tar -xvf data3.tar
mv data5.bin data5.tar
tar -xvf data5.tar
mv data6.bin data6.bz2
bzip2 -d data6.bz2
mv data6 data6.tar
tar -xvf data6.tar
mv data8.bin data8.gz
gzip -d data8.gz
cat data8
</pre>
<br><br>
With this command we get the password for bandit level Thirteen: wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

<br></br>
<h1> Level Thirteen ---> Level Fourteen </h1>
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on
<br></br>
We can tell by the level description that we need to figure out a way to ssh into the next level to find the password via the private key. So first we read the man pages to figure out that we need the -i argument to specfiy the key and then we can simply ssh into the user: bandit 14 on the local host.
<pre>
man ssh
ssh bandit14@localhost -i sshkey.private (didn't work)
ssh bandit14@localhost -i sshkey.private -p 2220 (needed to specify the correct port number)
cat /etc/bandit_pass/bandit14
</pre>
<br><br>
With this command we get the password for bandit level Fourteen: fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

<br></br>
<h1> Level 14 ---> 15  </h1>
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
<br></br>
Seeing as we're already logged in as bandit14 we can go ahead and submit the password we just got to the localhost on port 30000 by utilizing nc.
<pre>
nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
</pre>
<br><br>
With this command we get the password for bandit level 15: jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

<br></br>
<h1> Level 15 ---> 16  </h1>
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…
<br></br>
This level is pretty self explanatory like the last level but because I'm unsure on how I have to format the command I will run openssl s_client -help.
<pre>
openssl s_client localhost:30001
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
</pre>
<br><br>
With this command we get the password for bandit level 16: JQttfApK4SeyHwDlI9SXGR50qclOAil1

<br></br>
<h1> Level 16 ---> 17  </h1>
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.
<br></br>
<pre>
nmap localhost -sV -p31000-32000 (first tried without -sV and wanted more detail on which services these ports are running)
openssl s_client localhost:31518 (input password - didn't work)
openssl s_client localhost:31960 (did work)
JQttfApK4SeyHwDlI9SXGR50qclOAil1
</pre>
<br><br>
With this command we get the password for bandit level 17: 

-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

To connect to level 17 use this rsa key by creating a file with this key in it, changing permissions so that it is protectecd (chmod 500), then using the file to ssh. Ex. ssh bandit17@bandit.labs.overthewire.org -i bandit17.key -p 2220

<br></br>
<h1> Level 17 ---> 18  </h1>
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19
<br></br>
This level is pretty easy. based on the description we must use the diff command and with that we get the password for the next level.
<pre>
diff passwords.old passwords.new
</pre>
<br><br>
With this command we get the password for bandit level 18: hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

<br></br>
<h1> Level 18 ---> 19  </h1>
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
<br></br>
This level is pretty tricky. However we can bypass the logoff by putting cat readme in the same line as the ssh command. This will allow me to read the file and get the password for the next level despite being automatically logged off.
<pre>
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
</pre>
<br><br>
With this command we get the password for bandit level 19: awhqfNnAbc1naukrpqDYcF95h7HoMTrC

<br></br>
<h1> Level 19 ---> 20  </h1>
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
<br></br>
This level can be tricky if you forget to run the command with ./  Once you run bandit20-do it becomes clear that it will allow you to act as user: bandit20 which lets us read the password for the next level in bandit_pass/bandit20.
<pre>
ls -al
./bandit20-do
./bandit20-do cat /etc/bandit_pass/bandit20
</pre>
<br><br>
With this command we get the password for bandit level 20: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
