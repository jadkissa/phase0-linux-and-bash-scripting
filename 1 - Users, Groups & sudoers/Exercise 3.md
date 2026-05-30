# Exercise 3 — Understanding /etc/group
----------------------
Run this command:

cat /etc/group
----------------------
Example output:
root:x:0:
sudo:x:27:jad
docker:x:999:jad,alice
developer:x:1001:jad,bob,alice
----------------------

The 4 fields (separated by :):

Field	Meaning	Example
1	Group name	developer
2	Group password (x means in /etc/gshadow)	x
3	GID (Group ID)	1001
4	Members (comma separated)	jad,bob,alice
----------------------

Practice:

#### View your groups
groups

##### Or
id

#### Find which groups your user belongs to
cat /etc/group | grep $USER
----------------------