# Exercise 4: Understand hard links vs soft links


### Create a real file
echo "original content" > original.txt
cat original.txt

### Create a hard link (same data, different name)
ln original.txt hardlink.txt
ls -li original.txt hardlink.txt   # Same inode number = same file

### Create a soft/symbolic link (pointer to filename)
ln -s original.txt softlink.txt
ls -li softlink.txt                 # Different inode

### See the difference
echo "new content" >> original.txt
cat hardlink.txt    # Changes too (same file)
cat softlink.txt    # Also shows changes (points to original)

### Delete original
rm original.txt
cat hardlink.txt    # Still works (data still exists)
cat softlink.txt    # Broken! (points to deleted file)
ls -la softlink.txt # Shows red/blinking = broken

