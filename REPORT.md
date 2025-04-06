# Software Build Automation Tools - Laboratory Report
**Student Name:** Hüseyin Tunay Çelik  
**Date:** April 6, 2025  
**Repository:** [https://github.com/Tunaycel/proje-software.git](https://github.com/Tunaycel/proje-software.git)

## Overview
This report summarizes the completion of laboratory exercises focused on Git version control and automation capabilities. The laboratory work encompassed initializing repositories, branch management, conflict resolution, Git hooks implementation, and CI/CD pipeline setup.

## Tasks Completed

### Task 1: Initialize a Git Repository and Commit Changes
- Created a new Git repository using `git init`
- Configured Git with personal information using:
  ```
  git config --global user.name "Hüseyin Tunay Çelik"
  git config --global user.email "h.tunaycelik@gmail.com"
  ```
- Created a README.md file with project description
- Staged and committed the file using `git add` and `git commit`
- Modified the file with additional content and committed changes

### Task 2: Work with Branches
- Created a new branch named `feature-branch` using `git checkout -b feature-branch`
- Modified README.md by adding a "New Feature Section"
- Committed changes to the feature branch
- Merged the feature branch into main with `git merge feature-branch`
- Successfully pushed changes to the remote GitHub repository

### Task 3: Handle Merge Conflicts
- Created two separate branches: `branch1` and `branch2`
- Modified the same line in README.md in both branches
- Successfully merged `branch1` into `main`
- When attempting to merge `branch2`, a conflict occurred as expected
- Resolved the conflict manually by:
  1. Identifying the conflict markers in the file (`<<<<<<<`, `=======`, `>>>>>>>`)
  2. Editing the file to combine both changes meaningfully
  3. Marking resolution with `git add` and committing with an appropriate message

### Task 4: Implement a Git Hook
- Created a pre-commit hook in the `.git/hooks` directory
- Implemented logic to detect and prevent committing `.log` files:
  ```sh
  #!/bin/sh
  
  # Pre-commit hook to prevent committing .log files
  if git diff --cached --name-only | grep -E '\.log$'; then
      echo "ERROR: Attempt to commit .log files detected."
      echo "Please remove these files from your commit using git reset <file>."
      exit 1
  fi
  
  exit 0
  ```
- Made the hook executable using `attrib +x`
- Successfully tested the hook by attempting to commit a `.log` file, which was correctly blocked

### Task 5: Set Up a CI/CD Pipeline
- Created a GitHub Actions workflow configuration in `.github/workflows/main.yml`
- Configured the workflow to run on push events to the main branch
- Implemented a simple test process that:
  1. Checks out the code
  2. Runs a simulated test
  3. Checks for the presence of `.log` files (as an additional verification)
- Successfully pushed the workflow to GitHub where it will automatically run on future pushes

## Challenges and Solutions

### Challenge 1: Git Configuration
Initially encountered an error when committing changes because Git identity was not configured. Solved by properly setting up Git with user name and email.

### Challenge 2: Merge Conflicts
The merge conflict resolution required careful manual editing to ensure both changes were properly integrated without breaking functionality.

### Challenge 3: Making Git Hooks Executable
Ensuring proper execution permissions for the Git hook script required using the Windows-specific `attrib +x` command instead of the Unix `chmod +x` command.

### Challenge 4: GitHub Actions Workflow
Creating an appropriate CI/CD workflow required understanding the structure of GitHub Actions YAML configuration. I implemented a simple but extensible workflow that can be enhanced with more sophisticated testing in the future.

## Conclusion
This laboratory exercise provided practical experience with essential Git operations and automation tools. I successfully implemented all required tasks, demonstrating proficiency in version control systems, branch management, conflict resolution, and automation techniques.

The repository structure now includes:
- A well-documented README.md
- A functional pre-commit hook that enforces code quality standards
- A CI/CD pipeline for automated testing
- A branch structure demonstrating proper Git workflow

These skills are directly applicable to real-world software development environments, where version control and automation are critical for ensuring code quality and team collaboration.
