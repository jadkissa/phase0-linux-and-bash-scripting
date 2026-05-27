# Exercise 2.3: Mastering chattr and lsattr

cd ~/devops-lab

### Create a test file
echo "sensitive data" > secret.txt
cat secret.txt

### 1. Make file immutable (cannot be modified or deleted)
sudo chattr +i secret.txt
lsattr secret.txt
### Output shows: ----i--------- secret.txt

### Try to modify (fails)
echo "new data" >> secret.txt
### Error: Permission denied

### Try to delete (fails)
rm secret.txt
# Error: Operation not permitted

### 2. Remove immutable flag
sudo chattr -i secret.txt
lsattr secret.txt
### Output shows: -------------- secret.txt

### Now you can modify and delete
echo "new data" >> secret.txt
cat secret.txt
rm secret.txt

### 3. Append-only mode (can add, cannot delete or overwrite)
echo "log entry 1" > app.log
sudo chattr +a app.log
lsattr app.log
### Output shows: -----a-------- app.log

### Can append
echo "log entry 2" >> app.log
cat app.log

### Cannot overwrite
echo "new log" > app.log
### Error: Operation not permitted

### Cannot delete
rm app.log
### Error: Operation not permitted

### Remove append-only flag
sudo chattr -a app.log
rm app.log

### 4. Check attributes on system files
lsattr /etc/passwd
lsattr /etc/shadow
