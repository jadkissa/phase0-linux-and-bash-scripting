# Exercise 5 — Sticky Bit, SetUID, SetGID (Research)

### Sticky Bit (`chmod +t`)

### Create a shared directory
mkdir sticky_test
ls -ld sticky_test
### Shows: drwxrwxr-x

### Add sticky bit
chmod +t sticky_test
ls -ld sticky_test
### Shows: drwxrwxr-t  (the 't' at the end)

### Alternative way using numbers (1777)
mkdir sticky_test2
chmod 1777 sticky_test2
ls -ld sticky_test2
### Shows: drwxrwxrwt

### When to use: /tmp directory
ls -ld /tmp
### Shows: drwxrwxrwt



### Create a test script
cat > checkscript.sh << 'EOF'
#!/bin/bash
echo "Running as: $(whoami)"
cat /etc/shadow
EOF

chmod 755 checkscript.sh

### Try to run as normal user (will fail for /etc/shadow)
./checkscript.sh
### Should show "Permission denied" for /etc/shadow

### Add SetUID
sudo chown root:root checkscript.sh
sudo chmod u+s checkscript.sh
ls -la checkscript.sh
### Shows: -rwsr-xr-x  (the 's' in owner position)

### Now the script runs as root (DANGEROUS - just for learning)
### DO NOT actually run this on production


ls -la /usr/bin/passwd
## Shows: -rwsr-xr-x
## Why? Regular users need to change passwords (modify /etc/shadow)


### Create a directory for team project
mkdir team_data
chmod 770 team_data
ls -ld team_data
### Shows: drwxrwx---

### Add SetGID
chmod g+s team_data
ls -ld team_data
### Shows: drwxrws---  (the 's' in group position)

### Create a file inside (inherits group)
touch team_data/newfile.txt
ls -la team_data/
### Notice: group ownership matches parent directory

### Without SetGID, new files use your primary group
mkdir normal_dir
touch normal_dir/file.txt
ls -la normal_dir/
### Group is your primary group (not inherited)


cd ~/devops-lab
rm -rf sticky_test sticky_test2 checkscript.sh team_data normal_dir