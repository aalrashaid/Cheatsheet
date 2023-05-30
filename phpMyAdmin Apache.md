To install phpMyAdmin on a server running Ubuntu in the cloud, you can follow these steps:

1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages. Run the following command:
   ```
   sudo apt update
   ```

2. Install phpMyAdmin:
   Run the following command to install phpMyAdmin:
   ```
   sudo apt install phpmyadmin
   ```

   During the installation, you will be prompted to choose the web server that should be automatically configured to run phpMyAdmin. Use the spacebar to select Apache and press Enter.

   You will also be prompted to configure a database for phpMyAdmin. Choose "Yes" and enter your MySQL root password when prompted.

3. Configure Apache to Allow phpMyAdmin:
   By default, phpMyAdmin is not accessible from the web. You need to configure Apache to allow access to the phpMyAdmin interface. Run the following command to open the Apache configuration file:
   ```
   sudo nano /etc/apache2/conf-available/phpmyadmin.conf
   ```

   In the configuration file, find the line that says `Require ip 127.0.0.1` and add a new line below it with your server's public IP address or the IP addresses you want to allow access from. For example:
   ```
   Require ip 127.0.0.1
   Require ip 192.168.1.100
   ```

   Save the file and exit the editor.

4. Enable the phpMyAdmin Configuration:
   Run the following command to enable the phpMyAdmin configuration:
   ```
   sudo ln -s /etc/apache2/conf-available/phpmyadmin.conf /etc/apache2/conf-enabled/
   ```

5. Restart Apache:
   To apply the changes, restart the Apache web server by running the following command:
   ```
   sudo systemctl restart apache2
   ```

6. Access phpMyAdmin:
   You can now access phpMyAdmin by opening a web browser and entering your server's IP address or domain name followed by "/phpmyadmin". For example:
   ```
   http://your_server_ip_address/phpmyadmin
   ```

   You should see the phpMyAdmin login page where you can enter your MySQL username and password to access your databases.

By following these steps, you should have phpMyAdmin installed and accessible on your Ubuntu server in the cloud. You can use phpMyAdmin to manage your MySQL databases through a user-friendly web interface.