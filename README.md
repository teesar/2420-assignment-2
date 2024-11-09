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
2. If the sudo user variable is empty we can assume the script was run as root, and so we clone the git repository and create symbolic links using ~/ to match the home directory (could also just write /root).
3. If the sudo user variable is NOT empty, we know the script was run with sudo and we clone the git repository and create symbolic links using the home directory variable we created in step one ($YOUR_HOME).
* If the git clone command fails we give the user an error message referring to what may have caused the error, and exit the script.
* We use the -f flag on symbolic link creation to force overwrites if those files already exist.

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
