# OS-Linux-commands-Shell-scripting
Operating systems Lab exercise
# Linux commands-Shell scripting
Linux commands-Shell scripting

# AIM:
To practice Linux Commands and Shell Scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Execute the following commands

### Step 3:

Testing the commands for the desired output. 

# COMMANDS:
### Create the following files file1, file2 as follows:
cat > file1
```
chanchal singhvi
c.k. shukla
s.n. dasgupta
sumit chakrobarty
^d
```
cat > file2
```
anil aggarwal
barun sengupta
c.k. shukla
lalit chowdury
s.n. dasgupta
^d
```
### Display the content of the files
cat < file1
## OUTPUT
```
chanchal singhvi
c.k. shukla
s.n. dasgupta
sumit chakrobarty
^d

```


cat < file2
## OUTPUT
```
anil aggarwal
barun sengupta
c.k. shukla
lalit chowdury
s.n. dasgupta
^d

```

# Comparing Files
cmp file1 file2
## OUTPUT
 ```
file1 file2 differ: byte 1, line 1

```
comm file1 file2
 ## OUTPUT
```
	anil aggarwal
	barun sengupta
chanchal singhvi
		c.k. shukla
	lalit chowdury
		s.n. dasgupta
comm: file 2 is not in sorted order
	^d
sumit chakrobarty
comm: file 1 is not in sorted order
^d
comm: input is not in sorted order

```
 
diff file1 file2
## OUTPUT
```
1c1,2
< chanchal singhvi
---
> anil aggarwal
> barun sengupta
2a4
> lalit chowdury
4d5
< sumit chakrobarty

```

#Filters

### Create the following files file11, file22 as follows:

cat > file11
```
Hello world
This is my world
^d
```
cat > file22
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
^d
```


cut -c1-3 file11
## OUTPUT
```
Hel
Thi

```



cut -d "|" -f 1 file22
## OUTPUT

```
1001 
1002 
1003 
```

cut -d "|" -f 2 file22
## OUTPUT
```
Ram 
 tom 
 Joe 


```

cat > newfile 
```
Hello world
hello world
^d
````
cat < newfile 
```
Hello world
hello world
 ```

grep Hello newfile 
## OUTPUT

```
Hello world

```

grep hello newfile 
## OUTPUT

```
hello world

```


grep -v hello newfile 
## OUTPUT
```
Hello world

```


cat newfile | grep -i "hello"
## OUTPUT

```
Hello world
hello world

```


cat newfile | grep -i -c "hello"
## OUTPUT

```
2
```


grep -R ubuntu /etc
## OUTPUT

```
grep: unrecognized option: R
BusyBox v1.31.1 () multi-call binary.
 
Usage: grep [-HhnlLoqvsriwFE] [-m N] [-A/B/C N] PATTERN/-e PATTERN.../-f FILE [F
ILE]...
 
Search for PATTERN in FILEs (or stdin)
 
        -H      Add 'filename:' prefix
        -h      Do not add 'filename:' prefix
        -n      Add 'line_no:' prefix
        -l      Show only names of files that match
        -L      Show only names of files that don't match
        -c      Show only count of matching lines
        -o      Show only the matching part of line
        -q      Quiet. Return 0 if PATTERN is found, 1 otherwise
        -v      Select non-matching lines
        -s      Suppress open and read errors
        -r      Recurse
        -i      Ignore case
        -w      Match whole words only
        -x      Match whole lines only
        -F      PATTERN is a literal (not regexp)
        -E      PATTERN is an extended regexp
        -m N    Match up to N times per file
        -A N    Print N lines of trailing context
        -B N    Print N lines of leading context
        -C N    Same as '-A N -B N'
        -e PTRN Pattern to match
        -f FILE Read pattern from file		
```

grep -w -n world newfile   
## OUTPUT
```
1:Hello world
2:hello world

```

cat > newfile 
```
Hello world
hello world
Linux is world number 1
Unix is predecessor
Linux is best in this World
^d
```

cat < newfile
```
Hello world
hello world
Linux is world number 1
Unix is predecessor
Linux is best in this World
^d
 ```
egrep -w 'Hello|hello' newfile 
## OUTPUT
```
Hello world
hello world
```


egrep -w '(H|h)ello' newfile 
## OUTPUT

```
Hello world
hello world

```

egrep -w '(H|h)ell[a-z]' newfile 
## OUTPUT

```
Hello world
hello world
```


egrep '(^hello)' newfile 
## OUTPUT

```
hello world

```

egrep '(world$)' newfile 
## OUTPUT

![image](https://github.com/user-attachments/assets/2ed48502-246f-4cef-b7d8-4eccb3c98905)


egrep '(World$)' newfile 
## OUTPUT
![image](https://github.com/user-attachments/assets/a3c2af31-75ae-4477-8b27-5c6bb703a6b8)


egrep '((W|w)orld$)' newfile 
## OUTPUT
![image](https://github.com/user-attachments/assets/64f9fb9b-445d-4913-a2d4-7e761e3f6f47)



egrep '[1-9]' newfile 
## OUTPUT

![image](https://github.com/user-attachments/assets/4905b2d5-5d99-4596-b917-72bfd88ca8bd)


egrep 'Linux.*world' newfile 
## OUTPUT
![image](https://github.com/user-attachments/assets/3aebb884-6a87-4332-8529-ef021af5dfba)


egrep 'Linux.*World' newfile 
## OUTPUT

![image](https://github.com/user-attachments/assets/48e21033-66de-4f51-a5f7-5d9da96c9627)

egrep l{2} newfile
## OUTPUT

![image](https://github.com/user-attachments/assets/89b164ca-3076-4f6d-8a0e-894dc4ffb95a)


egrep 's{1,2}' newfile
## OUTPUT 
![image](https://github.com/user-attachments/assets/9a185a48-ff73-409c-a906-1de0ba459b94)


cat > file23
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Ram | 10000 | HR
^d
```


sed -n -e '3p' file23
## OUTPUT
```
1002 | tom |  5000 | Admin

```

sed -n -e '$p' file23
## OUTPUT

```
1001 | Ram | 10000 | HR

```

sed  -e 's/Ram/Sita/' file23
## OUTPUT

```
1001 | Sita | 10000 | HR
1001 | Sita | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Sita | 10000 | HR

```
sed  -e '2s/Ram/Sita/' file23
## OUTPUT

```
1001 | Ram | 10000 | HR
1001 | Sita | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Ram | 10000 | HR

```

sed  '/tom/s/5000/6000/' file23
## OUTPUT

```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  6000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Ram | 10000 | HR

```

sed -n -e '1,5p' file23
## OUTPUT

```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR

```

sed -n -e '2,/Joe/p' file23
## OUTPUT

```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer

```


sed -n -e '/tom/,/Joe/p' file23
## OUTPUT

```
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
```
seq 10 
## OUTPUT

```
1
2
3
4
5
6
7
8
9
10

```

seq 10 | sed -n '4,6p'
## OUTPUT
```
4
5
6

```


seq 10 | sed -n '2,~4p'
## OUTPUT
```
2
3
4

```


seq 3 | sed '2a hello'
## OUTPUT
```
1
2
hello
3

```


seq 2 | sed '2i hello'
## OUTPUT
```
1
hello
2

```

seq 10 | sed '2,9c hello'
## OUTPUT
```
1
hello
10

```

sed -n '2,4{s/^/$/;p}' file23
## OUTPUT

```
$1001 | Ram | 10000 | HR
$1002 | tom |  5000 | Admin
$1003 | Joe |  7000 | Developer

```

sed -n '2,4{s/$/*/;p}' file23
## OUTPUT
```
1001 | Ram | 10000 | HR*
1002 | tom |  5000 | Admin*
1003 | Joe |  7000 | Developer*

```

#Sorting File content
cat > file21
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
``` 
sort file21
## OUTPUT
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1004 | Sit |  7000 | Dev
1005 | Sam |  5000 | HR

```

cat > file22
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
``` 
uniq file22
## OUTPUT
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev

```


#Using tr command

cat file23 | tr [:lower:] [:upper:]
 ## OUTPUT
```
1001 | RAM | 10000 | HR
1001 | RAM | 10000 | HR
1002 | TOM |  5000 | ADMIN
1003 | JOE |  7000 | DEVELOPER
1005 | SAM |  5000 | HR
1004 | SIT |  7000 | DEV
1003 | JOE |  7000 | DEVELOPER
1001 | RAM | 10000 | HR
```
cat > urllist.txt
```
www. yahoo. com
www. google. com
www. mrcet.... com
^d
 ```
cat < urllist.txt
```
www. yahoo. com
www. google. com
www. mrcet.... com
 ```
cat urllist.txt | tr -d ' '
 ## OUTPUT

```
www.yahoo.com
www.google.com
www.mrcet....com

```
 
cat urllist.txt | tr -d ' ' | tr -s '.'
## OUTPUT
```
www.yahoo.com
www.google.com
www.mrcet.com
```


#Backup commands
tar -cvf backup.tar *
## OUTPUT
```
bench.py
file1
file11
file2
file21
file22
file23
hello.c
hello.js
newfile
readme.txt
urllist.txt
```

mkdir backupdir
 
mv backup.tar backupdir
 
tar -tvf backup.tar
## OUTPUT
```
drwxr-xr-x root/root         0 2024-08-16 10:12:02 backupdir/
-rw-r--r-- root/root     13312 2024-08-16 10:10:04 backupdir/backup.tar
-rw-r--r-- root/root       114 2020-07-05 23:17:07 bench.py
-rw-r--r-- root/root        61 2024-08-16 09:48:52 file1
-rw-r--r-- root/root        29 2024-08-16 09:52:03 file11
-rw-r--r-- root/root        70 2024-08-16 09:49:11 file2
-rw-r--r-- root/root       131 2024-08-16 10:06:47 file21
-rw-r--r-- root/root       155 2024-08-16 10:07:30 file22
-rw-r--r-- root/root       210 2024-08-16 10:02:59 file23
-rw-r--r-- root/root        76 2020-07-03 14:45:56 hello.c
-rw-r--r-- root/root        22 2020-06-26 14:57:33 hello.js
-rw-r--r-- root/root        96 2024-08-16 09:57:21 newfile
-rw-r--r-- root/root       151 2020-07-05 23:19:13 readme.txt
-rw-r--r-- root/root        52 2024-08-16 10:09:28 urllist.txt
```

tar -xvf backup.tar
## OUTPUT

```
backupdir/
backupdir/backup.tar
bench.py
file1
file11
file2
file21
file22
file23
hello.c
hello.js
newfile
readme.txt
urllist.txt
```
gzip backup.tar

ls .gz
## OUTPUT
 ![image](https://github.com/user-attachments/assets/c4593980-2189-4776-9637-a1cab756655d)

gunzip backup.tar.gz
## OUTPUT

 ![image](https://github.com/user-attachments/assets/2a6ff2c0-1890-4545-a70a-24b2e3193318)


# Shell Script
```
echo '#!/bin/sh' > my-script.sh
echo 'echo Hello World‘; exit 0 >> my-script.sh
```
chmod 755 my-script.sh
./my-script.sh
## OUTPUT

![image](https://github.com/user-attachments/assets/cc845e6f-e162-4625-b356-de8f2678876e)

 
cat << stop > herecheck.txt
```
hello in this world
i cant stop
for this non stop movement
stop
```

cat herecheck.txt
## OUTPUT
```
hello in this world
i cant stop
for this non stop movement

```

cat < scriptest.sh 
```bash
\#!/bin/sh
echo “File name is $0 ”
echo "File name is " `basename $0`
echo “First arg. is ” $1
echo “Second arg. is ” $2
echo “Third arg. is ” $3
echo “Fourth arg. is ” $4
echo 'The $@ is ' $@
echo 'The $\# is ' $1#
echo 'The $$ is ' $$
ps
^d
 ```

cat scriptest.sh 
```bash
\#!/bin/sh
echo “File name is $0 ”
echo "File name is " `basename $0`
echo “First arg. is ” $1
echo “Second arg. is ” $2
echo “Third arg. is ” $3
echo “Fourth arg. is ” $4
echo 'The $@ is ' $@
echo 'The $\# is ' $\#
echo 'The $$ is ' $$
ps
```
 
chmod 777 scriptest.sh
 
./scriptest.sh 1 2 3

## OUTPUT

![image](https://github.com/user-attachments/assets/4a51fd6c-6400-463d-8d94-b172a33de3bf)

 
ls file1
## OUTPUT
```
file1
```
echo $?
## OUTPUT 
```
0

```

./one
bash: ./one: Permission denied
 
echo $?
## OUTPUT 
![image](https://github.com/user-attachments/assets/3a43cb91-bdd5-46b7-967d-fb35ad02fe4d)

abcd
 
echo $?
 ## OUTPUT
![image](https://github.com/user-attachments/assets/fbe4e341-6922-4c34-9fd4-08496299fb9d)


 
# mis-using string comparisons

cat < strcomp.sh 
```
bash
\#!/bin/bash
val1=baseball
val2=hockey
if [ $val1 \> $val2 ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
^d
```

cat strcomp.sh 
```
bash
\#!/bin/bash
val1=baseball
val2=hockey
if [ $val1 \> $val2 ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
```
## OUTPUT

![image](https://github.com/user-attachments/assets/92d3dea9-6e9e-4ee1-b8f1-eb2ae2b31e46)


chmod 755 strcomp.sh
 
./strcomp.sh 
## OUTPUT
```
baseball is less than hockey

```

# check file ownership
cat < psswdperm.sh 
```bash
\#!/bin/bash
if [ -O /etc/passwd ]
then
echo “You are the owner of the /etc/passwd file”
else
echo “Sorry, you are not the owner of the /etc/passwd file”
fi
^d
```

cat psswdperm.sh 
```bash
/#!/bin/bash
if [ -O /etc/passwd ]
then
echo “You are the owner of the /etc/passwd file”
else
echo “Sorry, you are not the owner of the /etc/passwd file”
fi
 ```
./psswdperm.sh
## OUTPUT
![image](https://github.com/user-attachments/assets/3b47acbb-facc-4a3d-983e-ef65e788ca50)


# check if with file location
cat>ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
^d
```
cat ifnested.sh 
```
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
```

./ifnested.sh 
## OUTPUT

![image](https://github.com/user-attachments/assets/4fb578ef-41ef-440f-aad7-b259d71b5a07)


# using numeric test comparisons
cat > iftest.sh 
```bash
\#!/bin/bash
val1=10
val2=11
if [ $val1 -gt 5 ]
then
echo “The test value $val1 is greater than 5”
fi
if [ $val1 -eq $val2 ]
then
echo “The values are equal”
else
echo “The values are different”
fi
^d
```


cat iftest.sh 
```bash
\#!/bin/bash
val1=10
val2=11
if [ $val1 -gt 5 ]
then
echo “The test value $val1 is greater than 5”
fi
if [ $val1 -eq $val2 ]
then
echo “The values are equal”
else
echo “The values are different”
fi
```

$ chmod 755 iftest.sh
 
$ ./iftest.sh 
## OUTPUT
![image](https://github.com/user-attachments/assets/ca6baf69-6ea5-4aae-9bc3-73d7696ad13a)


# check if a file
cat > ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
^d
```

cat ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
```

$ chmod 755 ifnested.sh
 
$ ./ifnested.sh 
## OUTPUT
![image](https://github.com/user-attachments/assets/9a0b3da5-520b-437a-b584-117a41746f52)


# looking for a possible value using elif
cat > elifcheck.sh 
```bash
\#!/bin/bash
if [ $USER = Ram ]
then
echo "Welcome $USER"
echo "Please enjoy your visit"
elif [ $USER = Rahim ]
then
echo "Welcome $USER"
echo "Please enjoy your visit"
elif [ $USER = Robert ]
then
echo "Special testing account"
elif [ $USER = gganesh ]
then
echo "$USER, Do not forget to logout when you're done"
else
echo "Sorry, you are not allowed here"
fi
```

$ chmod 755 elifcheck.sh
 
$ ./elifcheck.sh 
## OUTPUT
![image](https://github.com/user-attachments/assets/2b0d26d1-de93-4d64-a1a1-1ecf838cadf0)


# testing compound comparisons
cat> ifcompound.sh 
```bash
\#!/bin/bash
if [ -d $HOME ] && [ -w $HOME ]
then
echo "The file exists and you can write to it"
else
echo "I cannot write to the file"
fi
```
$ chmod 755 ifcompound.sh
$ ./ifcompound.sh 
## OUTPUT
![image](https://github.com/user-attachments/assets/5b1ab1af-5112-4ea4-a2a4-c5c8dab30c3e)

# using the case command
cat >casecheck.sh 
```bash
case $USER in
Ram | Robert)
echo "Welcome, $USER"
echo "Please enjoy your visit";;
Rahim)
echo "Special testing account";;
gganesh)
echo "$USER, Do not forget to log off when you're done";;
*)
echo "Sorry, you are not allowed here";;
esac
```
$ chmod 755 casecheck.sh 
 
$ ./casecheck.sh 

```
Welcome Ram/Rahim
Please enjoy your visit
Special testing account
gganesh, Do not forget to logout when you're done
Sorry, you are not allowed here
cat > whiletest

#!/bin/bash
#while command test
var1=10
while [ $var1 -gt 0 ]
do
echo $var1
var1=$[ $var1 - 1 ]
done
$ chmod 755 whiletest.sh

$ ./whiletest.sh
```
 
cat > whiletest
```bash
#!/bin/bash
#while command test
var1=10
while [ $var1 -gt 0 ]
do
echo $var1
var1=$[ $var1 - 1 ]
done
```
$ chmod 755 whiletest.sh
 
$ ./whiletest.sh

 
![309350923-81d3e9d1-aef2-4da1-889e-ace086eb57ee](https://github.com/user-attachments/assets/2f41919c-82f8-4291-a6ed-eebaa19e1e9c)


cat untiltest.sh 
```bash
\#using the until command
var1=100
until [ $var1 -eq 0 ]
do
echo $var1
var1=$[ $var1 - 25 ]
done
``` 
$ chmod 755 untiltest.sh

![309350992-7f3f4232-c556-487d-845d-36ad26360a71](https://github.com/user-attachments/assets/29820e40-d26b-4121-a6c7-b0169f4dc70b)

 
 
cat forin1.sh 
```bash
\#!/bin/bash
\#basic for command
for test in Alabama Alaska Arizona Arkansas California Colorado
do
echo The next state is $test
done
 ```
 
$ chmod 755 forin1.sh

 ![309351099-00883fb1-6489-4163-99fc-b750d8b77ef1](https://github.com/user-attachments/assets/5855ca5a-927c-43b2-b0c5-79f6ad32182d)

 
cat forin2.sh 
```bash
\#!/bin/bash
\# another example of how not to use the for command
for test in I don't know if this'll work
do
echo “word:$test”
done
 ```
 
$ chmod 755 forin2.sh

 ![309351204-848dac7e-3175-4701-bf4f-851386219d97](https://github.com/user-attachments/assets/4522ec21-c799-444a-b971-ea465054d7d4)


cat forin3.sh 
```bash
\#!/bin/bash
\# another example of how not to use the for command
for test in I don\'t know if "this'll" work
do
echo "word:$test"
done
```
$ ./forin3.sh 

 ![309351469-29b13d20-62ba-4b80-8206-c4222a39156f](https://github.com/user-attachments/assets/00bf7f78-82cd-4c2f-bfbc-0703787433b0)


cat forin1.sh 
```bash
#!/bin/bash
# basic for command
for test in Alabama Alaska Arizona Arkansas California Colorado
do
echo The next state is $test
done
```
$ chmod 755 forin1.sh

![309350629-ca9c03f0-7d68-4586-9a4d-74bc315f2476](https://github.com/user-attachments/assets/5ff07273-bd1b-467b-bcf8-6c7dc8248663)


## OUTPUT
cat forinfile.sh 
```bash
#!/bin/bash
# reading values from a file
file="cities"
for state in `cat $file`
do
echo "Visit beautiful $file“
done
```
$ chmod 777 forinfile.sh
$ cat cities
Hyderabad
Alampur
Basara
Warangal
Adilabad
Bhadrachalam
Khammam
![309352007-b87b1e50-b514-47b1-a331-cb30ed9cb224](https://github.com/user-attachments/assets/522607af-927c-4eec-a0b5-88ac61b67730)



## OUTPUT


cat forctype.sh 
```bash
#!/bin/bash
# testing the C-style for loop
for (( i=1; i <= 5; i++ ))
do
echo "The value of i is $i"
done
````
$ chmod 755 forctype.sh
$ ./forctype.sh 

![309352096-4f0c3e69-7c5a-4776-887e-2fcabb80c203](https://github.com/user-attachments/assets/5517b990-6870-487d-8e23-303fd00d2191)


## OUTPUT

cat forctype1.sh 
```bash
#!/bin/bash
# multiple variables
for (( a=1, b=5; a <= 5; a++, b-- ))
do
echo "$a - $b"
done
```
$ chmod 755 forctype.sh
$ ./forctype1.sh

![309352128-b5770276-5696-4194-ac63-87877583c233](https://github.com/user-attachments/assets/2caf1de5-afca-4793-a39f-2cbf0ff67ccc)


## OUTPUT

cat fornested1.sh 
```bash
#!/bin/bash
# nesting for loops
for (( a = 1; a <= 3; a++ ))
do
echo "Starting loop $a:"
for (( b = 1; b <= 3; b++ ))
do
echo " Inside loop: $b"
done
done
```
$ chmod 755 fornested1.sh
 
$ ./fornested1.sh 
 ## OUTPUT

![309352154-8fe0ee36-6320-41e3-8fa6-0712430dcfbd](https://github.com/user-attachments/assets/9eb60a24-e9b7-4d3c-a9ab-ab4aa9991e42)

 
cat forbreak.sh 
```bash
#!/bin/bash
# breaking out of a for loop
for var1 in 1 2 3 4 5
do
if [ $var1 -eq 3 ]
then
break
fi
echo "Iteration number: $var1"
done
echo "The for loop is completed“
```
## OUTPUT

![309352213-e936aa33-eb93-4f40-a02a-c6a049b62b56](https://github.com/user-attachments/assets/260870bb-05d0-48cb-8355-36d77d10c6d6)


$ chmod 755 forbreak.sh
 
$ ./forbreak.sh 

 ![309352400-eb338c35-92de-41f7-b849-38e992330a68](https://github.com/user-attachments/assets/b0a3dad5-2934-4da8-905f-c68c7e65cfbc)


cat forbreak.sh 
```bash
#!/bin/bash
# breaking out of a for loop
for var1 in 1 2 3 4 5
do
if [ $var1 -eq 3 ]
then
continue
fi
echo "Iteration number: $var1"
done
echo "The for loop is completed“
```

 
$ chmod 755 forcontinue.sh
 
$ ./forcontinue.sh 
## OUTPUT
 
cat exread.sh 
```bash
#!/bin/bash
# testing the read command
echo -n "Enter your name: "
read name
echo "Hello $name, welcome to my program. "
 ```
 
$ chmod 755 exread.sh 
 
$ ./exread.sh 
## OUTPUT

![309352771-c356b6f6-e74a-42c1-9f9f-6ed4474fcbd2](https://github.com/user-attachments/assets/a95223bc-57b4-46be-961a-d0eb5134c1f0)


 cat exread1.sh
```bash
#!/bin/bash
# testing the read command
read -p "Enter your name: " name
echo "Hello $name, welcome to my program. “
``` 
$ chmod 755 exread1.sh 

## OUTPUT

![309352865-6df3bd1f-1c31-40de-a208-c222cd15bbf9](https://github.com/user-attachments/assets/237d99b8-6c3d-4b28-b66a-738ac19e0561)


$ ./exread1.sh 
 
cat funcex.sh
```bash
#!/bin/bash
# trying to access script parameters inside a function
function func {
echo $[ $1 * $2 ]
}
if [ $# -eq 2 ]
then
value=`func $1 $2`
echo "The result is $value"
else
echo "Usage: badtest1 a b"
fi
```
## OUTPUT
 ./funcex.sh 
 ./funcex.sh 1 2


 
cat argshift.sh
```bash
#!/bin/bash 
 while (( "$#" )); do 
  echo $1 
  shift 
done
```
$ chmod 777 argshift.sh

![309352974-405693cf-99d3-43a1-be48-e550763260de](https://github.com/user-attachments/assets/a4d79bcd-d1a0-4709-a625-f5b768dbff3f)

## OUTPUT
$ ./argshift.sh 1 2 3
 
 cat argshift1.sh
```bash
 #/bin/bash 
 # store arguments in a special array 
args=("$@") 
# get number of elements 
ELEMENTS=${#args[@]} 
 # echo each element in array  
# for loop 
for (( i=0;i<$ELEMENTS;i++)); do 
    echo ${args[${i}]} 
done
```
## OUTPUT
$ chmod 777 argshift.sh

$ ./argshift.sh 1 2 3

![309353031-74e4b687-6cc5-429b-b993-ad7db8f077f6](https://github.com/user-attachments/assets/008412e9-0c26-4dab-b3d0-af9a55aa3d7d)

 
cat argshift.sh
```bash
#!/bin/bash 
set -x 
while (( "$#" )); do 
  echo $1 
  shift 
done
set +x
```
## OUTPUT
 ./argshift.sh 1 2 3
 
 
cat > nc.awk
```bash
BEGIN{}
{
print len=length($0),"\t",$0 
wordcount+=NF
chrcnt+=len
}
END {
print "total characters",chrcnt 
print "Number of Lines are",NR
print "No of Words count:",wordcount
}
 ```
cat>data.dat
```bash
bcdfghj
abcdfghj
bcdfghj
ebcdfghj
bcdfghj
ibcdfghj
bcdfghj
obcdfghj
bcdfghj
ubcdfghj
```
awk -f nc.awk data.dat
## OUTPUT 

![309353118-b13086bf-891d-40e8-953e-eb519fb98979](https://github.com/user-attachments/assets/adbafc9e-5f6e-4da9-b43a-aa0de9798a9c)

 
cat > palindrome.sh
```bash
#num=545
echo "Enter the number"
read num
s=0
rev=""
temp=$num
while [ $num -gt 0 ]
do
	# Get Remainder
	s=$(( $num % 10 ))
	# Get next digit
	num=$(( $num / 10 ))
	# Store previous number and
	# current digit in reverse
	rev=$( echo ${rev}${s} )
done
if [ $temp -eq $rev ];
then
	echo "Number is palindrome"
else
	echo "Number is NOT palindrome"
fi
```
## OUTPUT 

![309353432-27199787-e397-4b51-b87d-e4736a1615fa](https://github.com/user-attachments/assets/1f53a7db-50b4-4152-8dfd-a1501bde1dfb)


# RESULT:
The Commands are executed successfully.
