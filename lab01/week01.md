# Week 1 Lab Practice: Introduction to Git and GitHub

## 1. Objective:
   - 1.1. Create a virtual machine (VM) using VMware Workstation Pro.
   - 1.2. Install Ubuntu 24.04 LTS on the VM.
   - 1.3. Save the VM on your personal hard drive for portability and future use.
   - 1.4. Set up a Git repository and perform basic Git operations.
   - 1.5. Create a GitHub account using their Seneca email account.
   - 1.6. Join GitHub's Education Program as a student.
   - 1.7. Create a private repository for lab submissions.
   - 1.8. Add the instructor as a collaborator to their private repository for submission access.
---

## 2. Instructions:

### Step 1: Set Up the Virtual Machine
   - 2.1. Launch VMware Workstation Pro:
      - Open VMware Workstation Pro from your desktop or start menu.
   - 2.2. Create a New Virtual Machine:
      - Click on "Create a New Virtual Machine".
      - In the New Virtual Machine Wizard, select "Typical (recommended)" and click Next.
   - 2.3. Select Installation Media:
      - Choose "Installer disc image file (ISO)".
      - Browse the location of the Ubuntu 24.04 LTS ISO file and select it.
      - VMware should automatically detect the operating system.
   - 2.4. Name the VM and Save It on the Personal Hard Drive:
      - In the "Name the Virtual Machine" screen:
      - Enter a name for the VM, e.g.,"AnsibleControlNode".
      - Click Browse, navigate to your personal hard drive, and select a folder to save the VM files.
   - 2.5.	Set Disk Capacity:
      -  Allocate 20 GB of disk space.
      -	Choose "Store virtual disk as a single file" for better portability.
   - 2.6.	Customize Hardware:
      - Customize Hardware:
      - Allocate 4 GB RAM.
      - Set 2 processors.
      - Ensure the Network Adapter is set to NAT.

### Step 2: Set Up the Virtual Machine
   - 2.7. Power on the Virtual Machine:
      - Select the newly created VM in VMware and click Power On.
   - 2.8. Install Ubuntu:
      - Follow the on-screen instructions to install Ubuntu:
         - Select Install Ubuntu.
         - Choose your keyboard layout.
         - Choose Normal Installation and tick the option to install third-party software for graphics and Wi-Fi hardware.
         - Select Erase Disk and Install Ubuntu (safe to do on a VM).
         - Set your time zone and create a user account with a password.
   - 2.9. Complete Installation:
      - After installation, reboot the VM.
      - Log in with the credentials you created.

### Step 3: Optimize and Save the VM
   - 2.10. Update Ubuntu:
      - Open a terminal and run:
```bash
sudo apt update && sudo apt upgrade -y
```
   - 2.11. Shut Down the VM:
      - Shut down the virtual machine properly from Ubuntu.
   - 2.12. Compact the VM Disk (Optional):
      - Go to VM > Manage > Clean Up Disks in VMware to reduce the VM size.

### Step 4: Setting Up Git

   - 2.13. Verify Git is installed on your system:
```bash
git --version
```
   - 2.14. If Git is not installed, install it using your system’s package manager:
```bash
sudo apt install git
```
   - 2.15. Configure Git:
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

   - 2.16. Verify configuration:
```bash
git config --list
```
---
### Step 5: Creating a Local Repository
   - 2.17. Create a new directory for your project:
```bash
mkdir repos
cd repos
mkdir str205-labs
cd str205-labs
```

   - 2.18. Initialize the Git repository:
```bash
git init
```

   - 2.19. Create a sample file:
```bash
echo "Hello Git!" > README.md
```
   - 2.20. Add the file to staging and commit:
```bash
git add README.md
git commit -m "Initial commit"
```
---

### Step 6: Create a GitHub Account and Setup
   - 2.21. Go to GitHub [Sign Up Page](https://github.com/Seneca-polytechnic).
   - ~~2.22. Enter the following details:~~
      - ~~Use your Seneca email address for the email field.~~
      - ~~Create a username (use a professional format, e.g., sf-seneca).~~
      - ~~set a secure password.~~
   - ~~2.22. Access GitHub Enterprise using MySeneca credential.~~
   - ~~2.23. Verify your email address by clicking the confirmation link sent to your inbox.~~
   - ~~2.24. Complete the account creation process.~~
   - ~~2.25. Join the GitHub Education Program (optional)~~
   - 2.26. Generate an SSH Key
      - Open a terminal and generate a new ssh key:
```bash
ssh-keygen -t rsa -b 4096 -C "yourname@myseneca.ca"
```
   - replace "yourname@myseneca.ca" with the email address you use for your GitHub account.
   - 2.27. When prompted to "Enter a file in which to save the key," press Enter to accept the default location (~/.ssh/id_rsa).
   - 2.28. You will be asked to set a passphrase. Either enter a passphrase for added security or press Enter to skip.
   - 2.29. Add the SSH Key to GitHub
      - Copy your public SSH key to the clipboard:
```bash
cat ~/.ssh/id_rsa.pub
```
   - 2.30. Add key to your GitHub account:
      -  On your GitHub [settings page](https://github.com/settings), navigate to Access > SSH and GPG keys.
      - Click **New SSH key**.
      - Provide a title (e.g., "sf@AnsibleControlNode") and paste the SSH key into the "Key" field.
      - Click **Add SSH Key**.
      - Test SSH Connection:
```bash
ssh -T git@github.com
```
   - you should see a message like:
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```
### Step 7: Pushing to GitHub

   - 2.31. Create a new repository on GitHub:
      - Navigate to [create a new repository page](https://github.com/new)
      - Enter your repository name (str205-labs).
      - Enter description (e.g. This repo is for my lab submission).
      - Change the repo type to **Private**
      - Click  **Create repository**.
   - 2.32. Link the local repository to GitHub:
```bash
git remote add origin git@github.com:<your-username>/<repository-name>.git
```
   - 2.33. Push the local repository to GitHub:
```bash
git branch -m main
git push -u origin main
```
---
### Step 8: Basic Git Operations
   - 2.34. Clone a repository from GitHub (another location):
```bash
git clone git@github.com:<username>/<repository-name>.git
```
   -2.35. Create a new branch:
```bash
git checkout -b feature_branch
```
   2.36. Make changes, add, and commit:
```bash
echo "New Feature" >> README.md
git add README.md
git commit -m "Added new feature"
```
   -2.37. Push the branch to GitHub:
```bash
git push origin feature_branch
```
   - 2.38. Create a pull request on GitHub to merge the changes.
---

### Step 9: Add your instructor as a Collaborator
   - 2.39. Open your newly created private repository.
   - 2.40. Go to the "Settings" tab.
   - 2.41. In the sidebar, navigate to "Collaborators and teams".
   - 2.42. Under "Collaborators", search for the instructor’s GitHub username (sf-seneca).
   - 2.43. Click **Add collaborator**.
   - 2.44. Confirm by clicking **Send invitation**.

## 3. Deliverables:
You should create a folder for each lab submission in your **str205-labs** repository, following the naming convention (e.g., `lab01`, `lab02`). Each folder should contain a markdown file for the lab report. Use the provided `report_template.md` as a base for your report submissions.

This weeks deliverables are:

- 3.1. **Code Block**: after VM creation, run command `lsb_release -a` and record the output. (10%)
- 3.2. **Code Block**: after VM creation, run command `uname -a` and record the output. (10%)
- 3.3. **Image**: screenshot of your GitHub dashboard. (10%)
- 3.4. **Image**: screenshot of your **str205-labs** repository's collaborator page showing instructor invitation status. (10%)
- 3.5. **Code Block**: Output of `git config --list`. (10%)
- 3.6. **Code Block**: Output of `git log` showing at least your initial commit. (10%)
- 3.7. **Image**: screenshot of branches <github.com/<username>/<repository-name>/branches after successfully pushed a branch to GitHub. (10%)
- 3.8. Reflection on Completing the Lab:
   - **What did you learn?** Provide a brief summary of your takeaways from this lab. (10%)
   - **Challenges Faced**: Highlight any difficulties you encountered during the lab. (10%)
   - **How You Overcame Challenges**: Describe the steps you took or solutions you implemented to resolve the challenges. (10%)
---

## 4. Summary:
By completing this lab, you will:
- 4.1. Understand how to use Git for version control.
- 4.2. Learn the basics of creating and managing repositories on GitHub.
- 4.3. Prepare for collaborative work in future labs.

