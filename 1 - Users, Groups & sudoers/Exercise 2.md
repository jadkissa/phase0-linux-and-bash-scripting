# Exercise 1 — Understanding /etc/passwd
----------------------
Run this command:

sudo cat /etc/shadow
----------------------
Example output:
root:$y$j9T$3zX8...:19876:0:99999:7:::
jad:$y$2a$4Fg...:19876:0:99999:7:::
----------------------

The 9 fields (separated by :):

Field	Meaning
1	Username
2	Encrypted password
3	Last password change (days since 1970-01-01)
4	Minimum days between changes
5	Maximum days before password expires
6	Warning period (days)
7	Inactivity period
8	Expiration date
9	Reserved
----------------------