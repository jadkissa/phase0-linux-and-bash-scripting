# Exercise 1 — Understanding /etc/passwd
----------------------
Run this command:

cat /etc/passwd
----------------------
Example output:

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
jad:x:1000:1000:jad:/home/jad:/bin/bash
----------------------
The 7 fields (separated by :):
Field	Meaning	Example
1	Username	jad
2	Password (x means encrypted in /etc/shadow)	x
3	UID (User ID)	1000
4	GID (Primary Group ID)	1000
5	Comment/GECOS	jad
6	Home directory	/home/jad
7	Shell	/bin/bash
----------------------

