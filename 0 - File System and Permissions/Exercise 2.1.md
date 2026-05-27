# Exercise 2.1: Understand file permissions

### Check current permissions
ls -la projects/

### You'll see something like: -rw-r--r--
### First character: - = file, d = directory
### Next 9 chars: rwx (owner) | rwx (group) | rwx (others)

### Change permissions (make script executable)
chmod +x projects/app.py
ls -la projects/app.py   # Now shows -rwxr-xr-x

### Create a script and make it executable
cat > scripts/hello.sh << 'EOF'
#!/bin/bash
echo "Hello from my first script!"
echo "Current date: $(date)"
EOF

chmod +x scripts/hello.sh
./scripts/hello.sh