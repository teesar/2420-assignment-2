# 2420-assignment-2





# create-install
* 
![](./Assets/install-1.png)
1. Check if id of user running script is not equal to 0. If so, this indicates the script was not run with sudo or by the root user, so we return an error message and exit the script.

![](./Assets/install-2.png)
2. Sync, refresh, and update current packages. Using --noconfirm so that user does not need to enter input to confirm installation.

![](./Assets/install-3.png)
3. Iterate through packages file and install each package name listed. Using --needed so that it only installs if it isn't already installed. No user confirmation required.

# create-links
![](./Assets/links-1.png)
1. $SUDO_USER is a variable set by sudo containing the user that used the sudo command. We can match this user in /etc/passwd with getent and then cut the user's home directory to set it to a variable.

![](./Assets/links-2.png)
2. If the sudo user variable is empty we can assume the script was run as root and we configure directories appropriately using ~/ (could also use /root)
3. If the sudo user variable is NOT empty we can assume the script was run with sudo and we configure directories appropriately using the variable we created in step 1.
4. We force delete any existing .dotfiles directory and any files/folders within it so that our clone can procede.
5. We clone the git repository into desired location, if the command fails we give the user an error message asking them to check specific git issues.
6. We force create the desired symbolic links, overwriting any current files of the same name. 

# create-main
![](./Assets/main-1.png)
![](./Assets/main-2.png)
![](./Assets/main3.png)
![](./Assets/main4.png)

# create-user
![](./Assets/user-1.png)
![](./Assets/user-2.png)
![](./Assets/user-3.png)
![](./Assets/user-4.png)
![](./Assets/user-5.png)
![](./Assets/user-6.png)
![](./Assets/user-7.png)
![](./Assets/user-8.png)
![](./Assets/user-9.png)
![](./Assets/user-10.png)
