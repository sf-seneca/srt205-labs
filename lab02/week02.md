# Week 2 Lab Practice: Ansible Installation

## 1. Objective:

- 1.1. Use the Ubuntu VM created in the previous lab.
- 1.2. Install Ansible on the VM.
- 1.3. Verify the installation and run a simple Ansible playbook.

---

## 2. Instructions:

### Step 1: Update the VM and Install Prerequisites

- 2.1. Start the VM:
  - Open VMware Workstation Pro, select your Ubuntu VM, and power it on.
- 2.2. Log In:
  - Log in with the username and password you created during the VM setup.
- 2.3. Update the System:
  - Open a terminal and run:
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```

### Step 2: Add the Ansible Repository and Install Ansible

- 2.4. Add the Ansible PPA:
  - Run the following command to add the official Ansible repository:
  ```bash
   sudo add-apt-repository --yes --update ppa:ansible/ansible
  ```
- 2.5. Install Ansible:
  - After adding the repository, install Ansible:
  ```bash
  sudo apt install -y ansible
  ```
- 2.6. Verify the Installation:
  - Check the installed version of Ansible:
  ```bash
  ansible --version
  ```

### Step 3: Configure and Test Ansible

- 2.7. Set Up a Test Inventory File:
  - Create a directory for your Ansible files:
  ```bash
  mkdir ~/repos/str205-labs/lab02
  cd ~/repos/str205-labs/lab02
  ```
  - Create an inventory file named `hosts`:
  ```bash
  nano hosts
  ```
  - Add the following content to define a localhost inventory:
  ```ini
  [local]
  localhost ansible_connection=local
  ```
  - Save and exit.
- 2.8. Run a Simple Ad-Hoc Command:
  - Test Ansible by running a simple ping command:
  ```bash
  ansible -i hosts local -m ping
  ```

### Step 4: Create and Run a Simple Playbook

- 2.9. Create a Playbook File:

  - Create a playbook named `setup.yml`:

  ```bash
  nano setup.yml
  ```

  - Add the following content:

  ```yaml
  ---
  - name: Test Ansible Playbook
  hosts: local

  become: yes
  tasks:
     - name: Install curl
     apt:
        name: curl
        state: present
  ```

  - Save and exit.

- 2.10. Run the Playbook:
  - Execute the playbook using Ansible:
  ```bash
  ansible-playbook -i hosts setup.yml -u [YourUserName] --become --ask-become-pass
  ```
  - Verify that the curl package is installed by running:
  ```bash
  curl --version
  ```

### Step 5: Push to GitHub Repository

- 2.12. Add and Commit Files:
  - Add all files to the repository:
  ```bash
  git add .
  ```
  - Commit the changes:
  ```bash
  git commit -m "Added lab02 files"
  ```
- 2.13. Check Git Status:
  - Check git status:
  ```bash
  git status
  ```
- 2.14. Push to GitHub:
  - Push the changes to the repository:
  ```bash
  git push
  ```

---

## 3. Challenges:

- 3.1. Create another VM:
  - Name it `ManagedNode01` (details provided in week01).
- 3.2. Install OpenSSH-server:
  - **Install** and **start** the SSH service on `ManagedNode01`.
- 3.3. Set Up SSH Key Authentication:
  - Create an SSH key on the control node and add the public key to `ManagedNode01`.
- 3.4. Update the Ansible Inventory File:

  - Update the inventory file to include `ManagedNode01`:

  ```ini
  [local]
  localhost ansible_connection=local

  [remote]
  managed_node01 ansible_host=<ip_of_managed_node01>
  ```

- 3.5. Test the Connection:
  - Test the connection to `ManagedNode01` using the Ansible ping module.
  ```bash
  ansible -i hosts remote -m ping
  ```
  - **Hint**: you may need to check `man ansible` for method of add your private key to the ansible command
- 3.6. Repeat Step5 in Section 2 Instruction to update any changes.
## 4. Deliverables:

You should create a folder for each lab submission in your **str205-labs** repository, following the naming convention (e.g., `lab01`, `lab02`). Each folder should contain a markdown file for the lab report. Use the provided `report_template.md` as a base for your report submissions.

This weeks deliverables are:

- 4.1. **Code Block:** Output of the `ansible --version` command. (15%)
- 4.2. **Code Block:** Output of the successful execution of the `ansible-playbook -i hosts setup.yml -u [YourUserName] --become --ask-become-pass` command. (10%)
- 4.3. **Code Block:** Output of the successful execution of the `ansible -i hosts local -m ping` command. (10%)
- 4.4. **Code Block:** Output of the `curl --version` command showing the installed version. (10%)
- 4.5. **Code Block:** Output of `git log` after successfully update remote repo with your lab02 updates. (10%)
- 4.6. **Code Block:** Output of the successful execution of the Ansible connection test for `ManagedNode01`. (25%)
- 4.7. Reflection on Completing the Lab:
  - **What did you learn?** Provide a brief summary of your takeaways from this lab. (10%)
  - **Challenges Faced**: Highlight any difficulties you encountered during the lab. (10%)
  - **How You Overcame Challenges**: Describe the steps you took or solutions you implemented to resolve the challenges. (10%)

## 5. Summary:

By completing this lab, you will:

- 5.1. Learn to install and configure Ansible.
- 5.2. Understand the basics of inventory management and running playbooks.
- 5.3. Gain experience in setting up and managing SSH connections for remote system administration.
