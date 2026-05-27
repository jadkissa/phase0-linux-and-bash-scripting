### Exercise 1: Create and manipulate files

### Create files in different ways
touch projects/app.py
touch projects/README.md
echo "print('Hello DevOps')" > projects/app.py
echo "# My First Project" > projects/README.md

#### View file contents
cat projects/app.py
cat projects/README.md

### Copy files
cp projects/app.py projects/app_backup.py

### List everything with details
ls -la projects/