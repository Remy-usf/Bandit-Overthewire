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
