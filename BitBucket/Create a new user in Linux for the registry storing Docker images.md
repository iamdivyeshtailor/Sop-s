To create a new user in Linux for storing Docker images in the registry, you can follow these steps:

1. Connect to your Linux server via SSH as a user with administrative privileges.
    
2. Open a terminal or SSH session and run the following command to create a new user:
    
    ```bash
    sudo adduser registry-user
	```
    Replace `registry-user` with the desired username for the user.
    
3. You will be prompted to set a password and provide additional user information. Follow the instructions and provide the necessary details.
    
4. Grant the new user sudo privileges (optional):
    
    - If you want to grant the new user sudo privileges, run the following command:
        
    ```bash
    sudo usermod -aG sudo registry-user
	```
    
        This command adds the user to the `sudo` group, allowing them to execute commands with administrative privileges. Replace `registry-user` with the actual username.
    - If you don't want to grant sudo privileges, you can skip this step.
5. Set permissions for the Docker registry data directory (if applicable):
    
    - If you previously created a directory for storing Docker registry data (e.g., `/docker-registry`), ensure that the new user has appropriate read and write permissions.
    - Run the following command to change the ownership of the directory to the new user:
        
    ```bash
    sudo chown -R registry-user:registry-user /docker-registry
	```
        
        Replace `/docker-registry` with the actual path to the directory and `registry-user` with the username you created.

Now you have successfully created a new user in Linux for storing Docker images in the registry. You can use this user to authenticate and interact with the Docker registry, depending on your specific setup and requirements.