To install and configure MySQL 8 on a server running Ubuntu in the cloud, you can follow these steps:

1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages. Run the following command:
   ```
   sudo apt update
   ```

2. Install MySQL Server:
   Run the following command to install MySQL Server:
   ```
   sudo apt install mysql-server
   ```

3. Secure the MySQL Installation:
   Run the following command to run the MySQL secure installation script and configure basic security settings:
   ```
   sudo mysql_secure_installation
   ```

   This script will prompt you to configure a root password, remove anonymous users, disallow root login remotely, remove the test database, and reload privileges.

4. Create a MySQL User:
   You can create a new MySQL user by running the following commands:
   ```
   sudo mysql
   CREATE USER 'username'@'host' IDENTIFIED WITH authentication_plugin BY 'password';
   ```

   Replace 'username' with your desired username and 'host' with the appropriate host. For example, 'localhost' or '%'.

5. Grant Privileges to the User:
   Grant the necessary privileges to the user by running the following command:
   ```
   GRANT PRIVILEGE ON database.table TO 'username'@'host';
   ```

   Replace 'database.table' with the specific database and table you want to grant access to.

6. Flush Privileges:
   After granting privileges, flush the privileges to apply the changes by running the following command:
   ```
   FLUSH PRIVILEGES;
   ```

7. Verify MySQL Installation:
   To check the status of the MySQL service, run the following command:
   ```
   systemctl status mysql.service
   ```

8. Check MySQL Version:
   You can check the MySQL version by running the following command:
   ```
   sudo mysqladmin -p -u [username] version
   ```

   Replace [username] with the MySQL username you created.

9. Adjust Authentication Method (Optional):
   By default, MySQL 8 uses the `caching_sha2_password` authentication method. If you encounter any issues with authentication, you can switch back to the older `mysql_native_password` method by following these steps:

   a. Connect to the MySQL server:
      ```
      sudo mysql
      ```

   b. Alter the user to use the `mysql_native_password` method:
      ```
      ALTER USER 'username'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
      ```

      Replace 'username' with the appropriate username and 'password' with the desired password.

   c. Flush privileges:
      ```
      FLUSH PRIVILEGES;
      ```

   d. Verify the changes:
      ```
      SELECT user, authentication_string, plugin, host FROM mysql.user;
      ```

10. Configure Password Validation Plugin (Optional):
    If you want to configure the password validation plugin, run the following command:
    ```
    SHOW VARIABLES LIKE 'validate_password%';
    ```

    This will display the current settings for password validation. You can adjust the configuration based on your requirements.

By following these steps, you should have MySQL 8 installed and configured on your Ubuntu server in the cloud. You can now start using MySQL for your applications.