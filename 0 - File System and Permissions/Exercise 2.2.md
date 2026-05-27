## Exercise 2.2: Understand file permissions

cd ~/devops-lab

# Create practice files
touch file1.txt file2.txt file3.txt
echo "test content" > file1.txt

# 1. chmod with numbers (octal)
# 644 = rw-r--r-- (owner read/write, others read only)
chmod 644 file1.txt
ls -la file1.txt

# 755 = rwxr-xr-x (owner all, others read/execute)
chmod 755 file2.txt
ls -la file2.txt

# 700 = rwx------ (only owner can do anything)
chmod 700 file3.txt
ls -la file3.txt

# 600 = rw------- (owner read/write only)
chmod 600 file1.txt
ls -la file1.txt

# 2. Remove execute permission
chmod -x file2.txt
ls -la file2.txt

# 3. chown (change owner and group)
# Create a test user first
sudo useradd -m testuser

# Change owner of file1.txt to testuser
sudo chown testuser file1.txt
ls -la file1.txt

# Change both owner and group
sudo chown testuser:testuser file2.txt
ls -la file2.txt

# Change only group
sudo chown :testuser file3.txt
ls -la file3.txt

# Change back to yourself
sudo chown $USER:$USER file1.txt file2.txt file3.txt
ls -la file*.txt

# Clean up test user
sudo userdel -r testuser