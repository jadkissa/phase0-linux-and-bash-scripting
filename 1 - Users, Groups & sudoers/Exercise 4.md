# Exercise 4 — Creating and Managing Users
----------------------
### Create a user:

#### Create user with home directory
sudo useradd -m testuser

#### Set password
sudo passwd testuser

----------------------
### View user information

#### Check if user exists
id testuser

#### See home directory
ls -la /home/testuser
----------------------

### Modify user (add to sudo group)

#### Add testuser to sudo group
sudo usermod -aG sudo testuser

#### Verify
groups testuser

----------------------

### Lock and unlock user

#### Lock account
sudo usermod -L testuser

#### Try to switch to testuser (should fail)
sudo -u testuser bash
exit

#### Unlock account
sudo usermod -U testuser

----------------------

### Delete user

#### Delete user with home directory
sudo userdel -r testuser

#### Verify deletion
id testuser
ls -la /home/testuser

----------------------

### Practice (run all at once):

#### Create
sudo useradd -m testuser
sudo passwd testuser

#### View
id testuser

#### Modify
sudo usermod -aG sudo testuser
groups testuser

#### Delete
sudo userdel -r testuser