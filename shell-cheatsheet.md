# Unix Cheat Sheet

Authored with the help of ChatGPT, this cheat sheet ensures that all paths and directories exist for smooth execution:



## Basic Commands

### Displaying Files and Directories

```bash
# List files and directories
ls

# List all files, including hidden files
ls -a

# List files with detailed information
ls -l
```

### Creating and Removing Folders. Going inside them

```bash

# Print the current directory
pwd

# Create and change to a new directory
mkdir -p ~/example_dir
cd ~/example_dir

# Go to home directory
cd ~

cd ~/example_dir
# Go up one directory level
cd ..

# Create a new directory
mkdir ~/new_directory

# Remove an empty directory
rmdir ~/new_directory
```

### File Operations

```bash

# Create a new file
touch ~/example_dir/new_file.txt

# Copy a file
cp ~/example_dir/new_file.txt ~/example_dir/copied_file.txt

# Move or rename a file
mv ~/example_dir/copied_file.txt ~/example_dir/renamed_file.txt

# Delete a file
rm ~/example_dir/renamed_file.txt

# Display file contents
echo "This is a test file." > ~/example_dir/file.txt
cat ~/example_dir/file.txt

# Display file contents one page at a time
less ~/example_dir/file.txt
# hit q or ctrl-c to quit
```

### Viewing and Searching

```bash

# View the beginning of a file
head ~/example_dir/file.txt

# View the end of a file
tail ~/example_dir/file.txt

# Search for a pattern in a file
grep 'test' ~/example_dir/file.txt

# Find files and directories
find ~/example_dir -name "file.txt"
```

## Advanced Commands

### Process Management

```bash

# Display running processes
ps

# Display all running processes
ps aux

# Terminate a process by PID (replace 1234 with a real PID)
# kill 1234

# Terminate a process by name (replace process_name with a real process name)
# pkill process_name
```

### Disk Usage

```bash

# Display disk usage
df -h

# Display disk usage of a directory
du -sh ~/example_dir
```

### Useful Shortcuts

```bash

# Clear the terminal screen
clear

# Repeat the last command
!!

# Run the previous command with sudo
sudo !!

# Autocomplete command/filename
TAB
```

## Example Script

```bash
#!/bin/bash
# This script demonstrates creating a directory, navigating into it, creating a file, and displaying its contents.
mkdir -p ~/example_dir
cd ~/example_dir
echo "Hello, Unix!" > hello.txt
cat hello.txt
```

You can save this file as `script.bash` and run it as `bash script.bash`.

she