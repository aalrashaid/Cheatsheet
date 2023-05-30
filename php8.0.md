To install PHP 8 on a cloud server running Ubuntu, you can follow these steps:

1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages. Run the following command:
   ```
   sudo apt update
   ```

2. Install PHP 8:
   Run the following command to install PHP 8 and its necessary extensions:
   ```
   sudo apt install php8.0 php8.0-cli php8.0-fpm php8.0-mysql php8.0-xml php8.0-mbstring php8.0-curl php8.0-gd php8.0-zip
   ```

   This command installs PHP 8 along with commonly used extensions such as MySQL, XML, MBstring, cURL, GD, and ZIP. Feel free to install additional extensions as per your requirements.

3. Configure PHP-FPM:
   Open the PHP-FPM configuration file in a text editor. For example, using Nano:
   ```
   sudo nano /etc/php/8.0/fpm/php.ini
   ```

   Make any necessary configuration changes according to your application requirements. For example, you can adjust the `memory_limit` or `upload_max_filesize` settings.

   Save the file and exit the editor.

4. Configure PHP-FPM Pool:
   Open the PHP-FPM pool configuration file in a text editor:
   ```
   sudo nano /etc/php/8.0/fpm/pool.d/www.conf
   ```

   Adjust the `listen` parameter to specify the socket or IP address and port on which PHP-FPM will listen. By default, it listens on the Unix socket. You can also set it to an IP address and port, such as `127.0.0.1:9000`.

   Save the file and exit the editor.

5. Start and Enable PHP-FPM:
   Start the PHP-FPM service and enable it to start automatically on system boot:
   ```
   sudo systemctl start php8.0-fpm
   sudo systemctl enable php8.0-fpm
   ```

6. Verify PHP Installation:
   Run the following command to verify the PHP installation and check the PHP version:
   ```
   php -v
   ```

   You should see the PHP version information printed on the console, confirming that PHP 8 is successfully installed.

By following these steps, you should have PHP 8 installed on your Ubuntu server in the cloud. You can now configure your web server (e.g., Nginx or Apache) to work with PHP 8 and start hosting your PHP-based applications.