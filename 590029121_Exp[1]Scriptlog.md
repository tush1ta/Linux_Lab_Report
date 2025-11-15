## Experiment [1]: [Linux OS Environment Setup]

### Name: Tushita Sharma, Roll No.: 590029121, Date: 2025-09-17

### AIM: 
* To install and configure different Linux operating system environments on a Windows machine. We will use two distinct technologies: **Windows Subsystem for Linux (WSL)** for a lightweight command-line environment and **Oracle VirtualBox** for a full graphical virtual machine.

### Requirements:
* A Windows 10/11 PC.
* Administrator access and **hardware virtualization enabled in the BIOS/UEFI**.
* An internet connection.

### Theory: 
* This experiment is designed to provide hands-on experience with two primary methods of running Linux on a Windows host.This is ideal for developers and system administrators who require a Linux command-line without the overhead of a full virtual machine.
* **Oracle VirtualBox**, on the other hand, is a traditional Type 2 hypervisor. It creates a complete, virtualized computer system on which a guest operating system (like Ubuntu or Linux Mint) can be installed. This method provides a fully isolated environment, complete with a graphical user interface (GUI).

---

## Procedure & Observations

### Part 1: Installing and Configuring WSL (Ubuntu)

#### Exercise 1: [Installing WSL on Windows]
* **Task Statement:** Enable the required Windows features and install the Ubuntu Linux distribution using a single command.
* **Explanation:** This demonstrates how the modern `wsl --install` command simplifies the entire setup process, automating what previously required multiple manual steps.
* **Command(s):**
    ```
    wsl --install -d ubuntu
    ```
* **Observation:** The command automatically enabled the "Virtual Machine Platform" and "Windows Subsystem for Linux" optional components. It then proceeded to download the Ubuntu distribution. The system requested a reboot to complete the final stage of the installation.

#### Exercise 2: [Configuring the Ubuntu Distribution]
* **Task Statement:** After the initial installation and reboot, configure the Ubuntu environment by creating a new user account.
* **Explanation:** This step is crucial for security and user management within the Linux environment. The new UNIX username and password created are separate from the Windows user account.

* **Observation:** Upon reboot, a terminal window opened automatically. It prompted for a "New UNIX username" and a password. After entering the credentials, the setup was complete and the command-line interface became available.

#### Exercise 3: [Verifying WSL Installation]
* **Task Statement:** Confirm that the WSL installation is successful and the Ubuntu distribution is ready for use.
* **Explanation:** This command provides a simple way to list all installed WSL distributions, showing their names, versions, and current state.
* **Command(s):**
    ```
    wsl -l -v
    ```
* **Output:**
    ```
      NAME      STATE     VERSION
    * Ubuntu    Running   2
    ```
* **Observation:** The output confirmed that Ubuntu was correctly installed and was currently in a "Running" state, with version 2 (indicating it is running on the WSL 2 architecture).

---

### Part 2: Installing VirtualBox and a Linux VM (Linux Mint)

#### Exercise 4: [Installing Oracle VirtualBox]
* **Task Statement:** Download and install the Oracle VirtualBox hypervisor on the Windows host machine.
* **Procedure:** The VirtualBox installer was downloaded from the official website.  Permission to install device software for network interfaces was granted.
* **Observation:** The VirtualBox application was successfully installed on the Windows system, along with the necessary drivers to support virtual machines.

#### Exercise 5: [Creating a Virtual Machine]
* **Task Statement:** Create a new virtual machine to host the Linux Mint operating system.
* **Procedure:** In the VirtualBox Manager, a new VM was created. The name was set to "Linux Mint", and a downloaded `.iso` file was selected as the installation medium. Hardware resources were configured with **4096 MB RAM** and **2 CPUs**. A new dynamically allocated virtual hard disk of **25 GB** was created.
* **Observation:** The VM was configured with the specified resources, creating a virtualized hardware environment ready to receive an operating system.

#### Exercise 6: [Installing Linux Mint]
* **Task Statement:** Install the Linux Mint OS on the virtual machine.
* **Procedure:** The newly created VM was started, which booted directly from the Linux Mint `.iso`. 
* **Observation:** The installation proceeded without issues, partitioning the virtual disk and copying the OS files. The process was identical to a standard installation on a physical computer.



---

## Result
* The experiment was successfully completed by setting up two distinct Linux environments. **Windows Subsystem for Linux** and a complete **virtual machine** with Linux Mint. This project demonstrated proficiency in using both a compatibility layer and a full hypervisor to meet different virtualization needs.