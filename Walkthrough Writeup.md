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
With this command we get the password for bandit level Six: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
