# Git and GitHub Cheat Sheet 



## Git Basics 

### Setup

```bash
## # Configure your Git username and email 
git config --global user.name "Your Name" 

git config --global user.email "your.email@example.com"
```

### Initializing a Repository

```bash
# Create a new directory and navigate into it
mkdir -p ~/git_example
cd ~/git_example

# Initialize a new Git repository
git init
```

### Working with Files

```bash
# Create a new file and add some content
echo "Hello, Git!" > file.txt

# Add the file to the staging area
git add file.txt

# Commit the file to the repository
git commit -m "Initial commit with file.txt"
# or just git commit...let nano handle the commit message
```

### Viewing the Repository

```bash
# View the commit history
git log

# View the status of the working directory and staging area
git status

# View the differences between the working directory and the staging area
git diff
```

### Branching and Merging

```bash
# Create a new branch
git branch new-feature

# Switch to the new branch
git checkout new-feature

# both together
git checkout -b new-feature

# Make some changes and commit them
echo "Some changes" >> file.txt
git add file.txt
git commit -m "Add changes to file.txt"

# Switch back to the main branch
git checkout main

# Merge the new branch into the main branch
git merge new-feature
```

### Stashing Changes

```bash
# Make some changes but do not commit them
echo "Temporary changes" >> file.txt

# Stash the changes
git stash

# Apply the stashed changes
git stash apply
```

### Undoing Changes

```bash
# Undo changes in the working directory
git checkout -- file.txt

# Reset the staging area
git reset file.txt

# Undo the last commit
git revert HEAD
```



## GitHub Basics

### Creating a Repository on GitHub

1. Navigate to [GitHub](https://github.com/) and log in.
2. Click on the `+` icon in the upper right corner and select `New repository`.
3. Fill in the repository name (e.g., `git_example`) and description.
4. Choose `Public` or `Private` and click `Create repository`. (Make sure you dont add any other files like a README or gitignore because you have already created the repo locally)

### Connecting Local Repository to GitHub

```bash
# Add the remote repository URL
git remote add origin https://github.com/yourusername/git_example.git

# Push the local repository to GitHub
git push -u origin main
```

### Working with GitHub CLI (`gh`)

You can download the github command line interface `gh` from https://cli.github.com . I have found this a very useful interface to work with github. After installing, do:

```bash

# Authenticate with GitHub
gh auth login

# Create a new repository on GitHub
gh repo create git_example2 --public --source=.

# Clone an existing repository
gh repo clone yourusername/git_example2

# View repository details
gh repo view yourusername/git_example2
```

### Creating and Managing Pull Requests

This gives you an idea of an entire development workflow

```bash
# Create a new branch for the feature
git checkout -b feature-branch

# Make some changes and commit them
echo "New feature" >> file.txt
git add file.txt
git commit -m "Add new feature"

# Push the feature branch to GitHub
git push origin feature-branch

# Create a pull request using `gh`
gh pr create --title "Add new feature" --body "This PR adds a new feature" --base main --head feature-branch

# List open pull requests
gh pr list

# View a pull request
gh pr view 1  # Replace 1 with the actual PR number

# Merge a pull request
gh pr merge 1  # Replace 1 with the actual PR number
```

### Issues and Project Management

```bash
# Create a new issue
gh issue create --title "Bug report" --body "There is a bug in the application"

# List open issues
gh issue list

# View an issue
gh issue view 1  # Replace 1 with the actual issue number
```

### Forking a Repository and Adding Upstream

1. Navigate to the repository you want to fork on [GitHub](https://github.com/).
2. Click on the `Fork` button in the upper right corner.
3. Choose your account to fork the repository.

```bash
# Clone the forked repository to your local machine
gh repo clone yourusername/forked_example

# Navigate to the repository
cd forked_example

# Add the original repository as upstream
git remote add upstream https://github.com/originaluser/original_example.git

# Verify the new remote
git remote -v

# Fetch the upstream repository
git fetch upstream

# Merge changes from upstream into your local main branch
git checkout main
git merge upstream/main
```

## Example Script 1 (full example)

```bash
# This script demonstrates creating a repository, making changes, and pushing to GitHub.
mkdir -p ~/git_example
cd ~/git_example
git init
echo "Hello, Git!" > file.txt
git add file.txt
git commit -m "Initial commit with file.txt"
gh auth login
gh repo create git_example --public --source=.
git push -u origin main
```

## Example Script 2 (full example)

```bash
# This script demonstrates creating another repository, making changes, and pushing to GitHub.
mkdir -p ~/git_example2
cd ~/git_example2
git init
echo "Hello again, Git!" > file2.txt
git add file2.txt
git commit -m "Initial commit with file2.txt"
gh repo create git_example2 --public --source=.
git push -u origin main
```

## Example Script 3 (full example)

```bash
# This script demonstrates creating yet another repository, making changes, and pushing to GitHub.
mkdir -p ~/git_example3
cd ~/git_example3
git init
echo "Hello once more, Git!" > file3.txt
git add file3.txt
git commit -m "Initial commit with file3.txt"
gh repo create git_example3 --public --source=.
git push -u origin main
```

## Example Script 4 (full example)

```bash
# This script demonstrates forking a repository, adding an upstream remote, and merging changes.
gh repo fork originaluser/original_example --clone
cd original_example
git remote add upstream https://github.com/originaluser/original_example.git
git remote -v
git fetch upstream
git checkout main
git merge upstream/main
```

------