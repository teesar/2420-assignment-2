# 2420-assignment-2





# create-install
* 
![](./Assets/install-1.png)
1. Ensure script is run with sudo or by root. Check if id of user running script is not equal to 0. If so, this indicates the script was not run with sudo or by the root user, so we return an error message and exit the script.

![](./Assets/install-2.png)
2. Sync, refresh, and update current packages. Using --noconfirm so that user does not need to enter input to confirm installation.

![](./Assets/install-3.png)
3. Iterate through packages file and install each package name listed. Using --needed so that it only installs if it isn't already installed. No user confirmation required.

# create-links
![](./Assets/install-1.png)
1. Ensure script is run with sudo or by root. Check if id of user running script is not equal to 0. If so, this indicates the script was not run with sudo or by the root user, so we return an error message and exit the script.

![](./Assets/links-1.png)
2. $SUDO_USER is a variable set by sudo containing the user that used the sudo command. We can match this user in /etc/passwd with getent and then cut the user's home directory to set it to a variable.

![](./Assets/links-2.png)
3. If the sudo user variable is empty we can assume the script was run as root and we configure directories appropriately using ~/ (could also use /root)
4. If the sudo user variable is NOT empty we can assume the script was run with sudo and we configure directories appropriately using the variable we created in step 1.
5. We force delete any existing .dotfiles directory and any files/folders within it so that our clone can procede.
6. We clone the git repository into desired location, if the command fails we give the user an error message asking them to check specific git issues.
7. We force create the desired symbolic links, overwriting any current files of the same name. 

# create-main
![](./Assets/main-1.png)
1. Ensure script is run with sudo or by root. Check if id of user running script is not equal to 0. If so, this indicates the script was not run with sudo or by the root user, so we return an error message and exit the script.

![](./Assets/main-2.png)
2. We use getopts to allow the person runing the script to specify whether they want to run the installation script, the clone and link creation script, or both. The -a flag sets INSTALL variable to true, -b flag sets LINKS variable to true, any other flag returns an error message to the user and exits the script.

![](./Assets/main3.png)
3. If installation variable has been set to true we run create-install script. If this command fails we return an error message asking user to ensure the required script exists in the necessary directory and then exits the script.


![](./Assets/main4.png)
4. If links variable has been set to true we run create-links script. If this command fials we return an error message asking user to ensure the required script exists in the necessary directory and then exits the script.

# create-user
![](./Assets/install-1.png)
1. Ensure script is run with sudo or by root. Check if id of user running script is not equal to 0. If so, this indicates the script was not run with sudo or by the root user, so we return an error message and exit the script.

![](./Assets/user-1.png)
2. We use getopts to allow the person running the script to specify the username (-a flag), password (-b flag), custom shell (-c flag), and groups (-d flag) for the new user. 
* Each flag requires an argument and the script will return an error and exit the script if an argument is missing. 
* If any incorrect flags are used the script will return an error message and exit the script.  

![](./Assets/user-2.png)
3. If the username has not been set the script will return an error informing the user that it's required and exit the script.

![](./Assets/user-3.png)
4. Assigning all existing users to a variable by cutting the correct segment of /etc/passwd file.

![](./Assets/user-4.png)
5. we iterate over the existing users to check if the desired username has already been taken. If it has, we return an error and exit the script. If the username is available, we continue.



![](./Assets/user-5.png)
6. We assign the last user id and group id on the system to variables.
7. We check to see if each are greater than or equal to 1000, if they are then we can simply increment by 1 to set a new user id and group id that have not yet been used. If they are not greater than or equal to 1000, we can set this user to user id 1000 and group id 1000.
![](./Assets/user-6.png)
![](./Assets/user-7.png)
![](./Assets/user-8.png)
![](./Assets/user-9.png)
![](./Assets/user-10.png)
