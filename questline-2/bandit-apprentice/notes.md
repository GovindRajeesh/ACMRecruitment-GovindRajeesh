## Level 0
~~~
ssh bandit0@bandit.labs.overthewire.org -p 2220
~~~

## Level 0 -> 1
~~~
ls
~~~
This command gave me the list of files in it.

Found the readme

then used

~~~
cat readme
~~~
to read the file and got the password:
~~~
6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
~~~

## Level 1 -> 2
~~~
ssh bandit1@bandit.labs.overthewire.org -p 2220
~~~
Loggedin into bandit1 using the password obtained previously

Opened the - file using the following command
~~~
cat ./-
~~~

and obtained another password

~~~
PK8fYLZg2hnHSz83plBL1iEPKdD3QToB
~~~


## Level 2 -> 3
~~~
ssh bandit2@bandit.labs.overthewire.org -p 2220
~~~
Loggedin into bandit2 using the password obtained previously

Opened the - file using the following command
~~~
cat -- "--spaces in this filename--"
~~~

and obtained another password

~~~
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
~~~

## Level 3 -> 4

```
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

Logged in to bandit3 using the password obtained previously.

Listed the files in the home directory using:

```
ls -la
```

Found a directory named `inhere`. Entered the directory:

```
cd inhere
```

Listed all files, including hidden files:

```
ls -la
```

Found a hidden file named `...Hiding-From-You`.

Opened the hidden file using:

```
cat "...Hiding-From-You"
```

and obtained another password:

```
xzTXq1rDJQVVazdv5cHq1TQytTWufAMq
```

## Level 4 -> 5

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

Logged in to bandit4 using the password obtained previously.

Entered the `inhere` directory and checked the type of all files using:

```bash
file ./*
```

Most files were identified as `data`, but `./-file07` was identified as **ASCII text**.

Opened the human-readable file using:

```bash
cat ./-file07
```

and obtained the next password:

```text
6C7h9GDB6ai5nr7wo1R0nrFjJ9yIrG
```

## Level 5 -> 6

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

Logged in to bandit5 using the password obtained previously.

Entered the `inhere` directory:

```bash
cd inhere
```

The directory contained many subdirectories, so instead of checking each one manually, used `find` to search for a file with the required properties:

```bash
find . -type f -size 1033c ! -executable
```

This returned:

```text
./maybehere07/.file2
```

The file was exactly **1033 bytes** and was **not executable**, matching the given conditions.

Opened the file using:

```bash
cat ./maybehere07/.file2
```

and obtained the next password:

```text
pA2hXQmCzV3sDtOaH4r9K2eLoSW
```

## Level 6 -> 7

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

Logged in to bandit6 using the password obtained previously.

The password is stored somewhere on the server with the following properties:

* Owned by user `bandit7`
* Owned by group `bandit6`
* Exactly 33 bytes in size

Used the `find` command to search the entire filesystem:

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

The `2>/dev/null` part hides the `Permission denied` error messages.

The command returned:

```text
/var/lib/dpkg/info/bandit7.password
```

Opened the file using:

```bash
cat /var/lib/dpkg/info/bandit7.password
```

and obtained the next password:

```text
Bmnnv6RZqkLfxgAi2lzYb1u3p5E3
```

## Level 7 -> 8

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

Logged in to bandit7 using the password obtained previously.

Listed the files in the home directory:

```bash
ls
```

Found a file named `data.txt`.

The password is stored in `data.txt` next to the word `millionth`.

Used `grep` to search for the word:

```bash
grep "millionth" data.txt
```

and obtained:

```text
millionth        VR1JMayciFxbnUokuQmJFW6QC9VKtub
```

Therefore, the next password is:

```text
VR1JMayciFxbnUokuQmJFW6QC9VKtub
```
