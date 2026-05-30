# Exercise 6 – Research: su vs sudo

su (Switch User)

#### Switch to root (requires root password)
su -

#### Switch to another user
su - alice

### Exit back to your user

exit

## Security: You need the target user's password.


sudo (Superuser Do)

### Run one command as root (uses YOUR password)
sudo cat /etc/shadow

### Run command as another user
sudo -u alice whoami

### Get root shell (logged)
sudo -i

## Security: Uses YOUR password, every command is logged.


### Key Differences
Feature	su	sudo
Requires	Target user's password	Your password
Logging	Minimal	Every command logged
Control	All or nothing	Per command
Root password	Everyone knows	Only root knows


### Why sudo is better for DevOps

    No need to share root password

    Every command is audited (/var/log/auth.log)

    Grant specific permissions (not everything)

    Can allow commands without password (NOPASSWD:)


### Practice


#### Check sudo logs
sudo cat /var/log/auth.log | grep sudo | tail -10

#### Try su (if you know root password)
su -
exit

#### Try sudo
sudo whoami