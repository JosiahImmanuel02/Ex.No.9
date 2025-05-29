# 19CS545-Ex1 - User Access and System Configuration in Linux in GitHub

# AIM:
To create a Repository

## Procedure:
Switching user to natasha: The command su natasha is used to switch the user from root to natasha.

Entering password: The next three lines with only [ and ] symbols likely represent the password being entered by the user natasha. Typing a password on the terminal screen won't display the characters for security reasons.

Edi ng the bash profile: The command vim .bash_profile is used to edit the hidden file .bash_profile in the user's home directory. The .bash_profile file is a shell script that is run whenever the user logs in.

Content of the bash profile: The lines following vim .bash_profile show the contents of the .bash_profile file. These lines appear to be comments and configura on op ons for the shell.

Sourcing the bash profile: The command source .bash_profile is used to source the .bash_profile file. This means that the commands in the file are executed as if they were typed at the command prompt.

Checking file permissions: The command umask is used to display the current file mode crea on mask. This mask affects the permissions of newly created files and directories.

Crea ng a file: The command touch file1 is used to create a new file named "file1" in the current directory.

Crea ng a directory: The command mkdir dir1 is used to create a new directory named "dir1" in the current directory.

Lis ng directory contents: The command ls -l is used to list the contents of the current directory in long format. The output shows that there are two new entries: a directory named "dir1" and a file named "file1".

10.In summary, these commands are used to switch user, edit a shell configura on file, verify file permissions, and create a new file and directory.

## OUTPUT:

![Screenshot 2025-05-29 113928](https://github.com/user-attachments/assets/51ee12d3-122c-4967-8e7c-15a13816a930)


## 9.2 Set the Password expire date
# PROCEDURE:
Edi ng the login defini ons file: The command vim /etc/login.defs is used to edit the file /etc/ login.defs. This file contains configura on op ons for various aspects of user accounts on the system, including password complexity requirements and password aging policies. The vim command is a text editor commonly used in Linux. Se ng password aging policy: The lines following the second line show the contents of the /etc/ login.defs file. The relevant lines for se ng password expiry are: PASS_MAX_DAYS: This se ng defines the maximum number of days a password can be used before it needs to be changed. The value in the image is set to 0, which means passwords never expire by default. PASS_MIN_DAYS: This se ng defines the minimum number of days a password must be used before it can be changed by the user. The value in the image is commented out with #, which means this se ng is not currently enforced. PASS_WARN_AGE: This se ng defines the number of days before a password expira on a user receives a warning message to change their password. The value in the image is set to 7, which means users will receive a warning message 7 days before their password expires (assuming PASS_MAX_DAYS is not set to 0). PASS_MIN_LEN: This se ng defines the minimum length for passwords. The value in the image is not shown; it might be commented out with #. Note: These changes will only affect new users created a er the configura on file is saved. Exis ng users won't be affected by this change. Saving the changes: Once you've made the necessary edits to the file, you can save the changes and exit the text editor. How you do this depends on the text editor you're using. In vim, you can press Esc to enter command mode, then type :wq and press Enter to save your changes and quit. In summary, these commands edit the password aging policy on a Linux server to set the password expira on for new users to 20 days.

# 9.3 Assign Sudo Privilege
## PROCEDURE:
Edi ng the sudoers file: The command vim /etc/sudoers is used to edit the file /etc/ sudoers. Edi ng this file with improper permissions can poten ally compromise the security of the system, so it's important to be cau ous when modifying it. The vim command is a text editor commonly used in Linux.

[Content of the sudoers file]: The specific lines shown will vary depending on your system's configura on. However the sudoers file typically contains lines in the format:

username ALL=(ALL) NOPASSWD: command_name

This line grants the user username permission to run the command command_name with root privileges without entering a password.

Saving the changes: Once you've made the necessary edits to the file, you can save the changes and exit the text editor. How you do this depends on the text editor you're using. In vim, you can press Esc to enter command mode, then type :wq and press Enter to save your changes and quit.

## OUTPUT:

![image](https://github.com/user-attachments/assets/c7023780-ec60-4a2e-a967-d8e25f9dfa43)


## 9.4 Configure the applica on RHCSA When login it will show the message
"Welcome to Advantage Pro”

## PROCEDURE:
Switching user to root: The first line su root is used to switch the user from alies to root. The su command is used to switch users on the system, and root is the privileged account on a Linux system.

Entering password: The next three lines with only [ and ] symbols likely represent the password being entered by the user root. Typing a password on the terminal screen won't display the characters for security reasons.

Edi ng the bash profile: The command vim .bash_profile is used to edit the hidden file .bash_profile in the user's home directory. The .bash_profile file is a shell script that runs whenever the user logs in.

Content of the bash profile: The lines following vim .bash_profile show the contents of the .bash_profile file. In the image, the line RHCSA="Welcome to Advantage Pro" appears to be a variable assignment. It creates a variable named RHCSA and assigns it the value "Welcome to Advantage Pro". The line echo $RHCSA appears to be a command that prints the value of the variable RHCSA to the terminal.

Sourcing the bash profile: The command source .bash_profile is used to source the .bash_profile file. This means that the commands in the file are executed as if they were typed at the command prompt.

Verifying the message: The last line echo $RHCSA shows the output of the command executed from the sourced .bash_profile file. It prints the message "Welcome to Advantage Pro" to the terminal.

## OUTPUT:

![image](https://github.com/user-attachments/assets/340e2a3f-e76c-4fbf-a26e-71acba615db5)


# 9.5 Create the script file
Create a mysearch script to locate file under /usr/share having size less than 1M." A er execu ng the mysearch script file and listed(searched) files has to be copied under /root/ myfiles.

## PROCEDURE:
Lines 1-3: #!/bin/bash find /usr/share -type f -size -1M > /root/myfiles • #!/bin/bash: This line specifies the interpreter that will be used to execute the script. In this case, the script will be executed by the Bash shell. • find /usr/share -type f -size -1M: This line uses the find command to search for files in the /usr/share directory and its subdirectories. Here's a breakdown of the op ons used: ◦-type f: This op on specifies that the search should only include regular files (not directories, symbolic links, etc.). ◦ /usr/share: This is the star ng directory for the search. ◦-size -1M: This op on specifies that the file size should be less than 1 Megabyte. The -1M indicates size and M specifies units in Megabytes. • > /root/myfiles: This redirects the output of the find command to a file named / root/myfiles. The find command will list the paths of any files that meet the search criteria. So, this line is basically saving the list of files to the /root/myfiles file. Note: • The script assumes the user running the script has permission to read files in /usr/share and write to the /root/myfiles directory. • By default, /root requires root privileges to write to. If the user running the script doesn't have root privileges, you would need to modify the script to copy the files to a writable directory. How to run the script:

Save the script as mysearch (or any name you prefer).
Make the script executable using the chmod command: chmod +x mysearch
Run the script from the command line: ./mysearch This will run the script and create the /root/myfiles file (if it doesn't exist) containing a list of files under /usr/share that are less than 1 Megabyte.

## Output:

![image](https://github.com/user-attachments/assets/722b11ca-5f4e-462a-aead-02b102d3dc85)

## Result:
Thus a Repository has been created successfully.
