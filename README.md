# Bandit-Overthewire
Bandit Overthewire Solutions

This is my walkthrough of the Bandit Overthewire challanges.

<h1> Level One ---> Level Two </h1>
Level Goal: The password for the next level is stored in a file called - located in the home directory
<br></br>
By reading the level description we can tell that the next level's password is stored in a text file that we're going to have to read thus the only command we will need is <STRONG>cat</STRONG>. The only tricky thing about this level is that the file is named "-" so a simple <STRONG>cat -</STRONG> will not work. We're going to have to specify the file location by using command line prompt: <pre> cat ./- </pre>
<br><br>
With this command we get the password for bandit level two: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
