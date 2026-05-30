# Here's Exercise 6 (Shared Directory with Group Permissions)

```markdown

### Step 1: Create a group


sudo groupadd devops-team

### Step 2: Add your user to the group

sudo usermod -aG devops-team $USER
groups $USER   # May need logout/login to see change

### Step 3: Create shared directory with SetGID

sudo mkdir -p /opt/devops-shared
sudo chown root:devops-team /opt/devops-shared
sudo chmod 2770 /opt/devops-shared
ls -ld /opt/devops-shared

 Shows: drwxrws--- root devops-team


### Step 4: Test

touch /opt/devops-shared/team-file.txt
ls -la /opt/devops-shared/
 File group is 'devops-team'(inherited)


 ### Step 5: Verify another user in group can access

 sudo useradd -m -G devops-team alice
sudo -u alice touch /opt/devops-shared/alice-file.txt
ls -la /opt/devops-shared/


### Step 6: Cleanup

sudo userdel -r alice
sudo rm -rf /opt/devops-shared
sudo groupdel devops-team


---
