## Exercise 3: Practice what you learned

# Create this structure:

~/devops-lab/
├── projects/
│   ├── web-app/
│   │   ├── index.html
│   │   └── style.css
│   └── api/
│       └── server.py
├── scripts/
│   └── backup.sh
└── logs/
    └── access.log



# Commands : 
cd ~/devops-lab
mkdir -p projects/web-app projects/api
touch projects/web-app/index.html projects/web-app/style.css
touch projects/api/server.py
touch scripts/backup.sh logs/access.log
tree   

# If tree isn't installed: sudo apt install tree -y