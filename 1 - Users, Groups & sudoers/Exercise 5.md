# Exercise 5 – Configuring sudoers with visudo

## Always use visudo — never edit /etc/sudoers directly
run this command : sudo visudo


Common sudoers entries

Entry	                Meaning
username ALL=(ALL) ALL	User can run any command as any user
username ALL=(ALL) /usr/bin/systemctl	User can only run systemctl
%groupname ALL=(ALL) ALL	All users in group can run any command

Practice

### Open visudo
sudo visudo

Add this line at the end of the file:


### Allow your user to run systemctl without password
jad ALL=(ALL) NOPASSWD: /usr/bin/systemctl

Save and exit (in nano: Ctrl+O, Enter, Ctrl+X)

Verify sudo access

### Check what commands your user can run
sudo -l

You should see the systemctl permission you added.

Remove the line (cleanup)

sudo visudo
#### Delete the line you added
#### Save and exit