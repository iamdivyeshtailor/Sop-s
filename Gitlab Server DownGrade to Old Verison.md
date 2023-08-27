## Downgrade 

The example below demonstrates the downgrade procedure when downgrading between minor and patch versions (for example, from 13.0.6 to 13.0.5).

When downgrading between major versions, take into account the specific version changes that occurred when you upgraded to the major version you are downgrading from.

These steps consist of:

-   Stopping GitLab
-   Removing the current package
-   Installing the old package
-   Reconfiguring GitLab
-   Restoring the backup
-   Starting GitLab

Steps:

1.  Stop GitLab and remove the current package:

    ```
    # If running Puma
    sudo gitlab-ctl stop puma
    
    # Stop sidekiq
    sudo gitlab-ctl stop sidekiq
    
    # If on Ubuntu: remove the current package
    sudo dpkg -r gitlab-ee
    
    # If on Centos: remove the current package
    sudo yum remove gitlab-ee
    ```

2.  Identify the GitLab version you want to downgrade to:

    ```
    # (Replace with gitlab-ce if you have GitLab FOSS installed)
    
    # Ubuntu
    sudo apt-cache madison gitlab-ee
    
    # CentOS:
    sudo yum --showduplicates list gitlab-ee
    ```

3.  Downgrade GitLab to the desired version (for example, to GitLab 13.0.5):

    ```
    # (Replace with gitlab-ce if you have GitLab FOSS installed)
    
    # Ubuntu
    sudo apt install gitlab-ee=13.0.5-ee.0
    
    # CentOS:
    sudo yum install gitlab-ee-13.0.5-ee.0.el8
    ```

4.  Reconfigure GitLab:

    ```
    sudo gitlab-ctl reconfigure
    ```

5.  Restore GitLab to complete the downgrade.

Done.