To install phpMyAdmin on a server running Ubuntu with Nginx in the cloud, you can follow these steps:

1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages. Run the following command:
   ```
   sudo apt update
   ```

2. Install phpMyAdmin and PHP-FPM:
   Run the following command to install phpMyAdmin and PHP-FPM:
   ```
   sudo apt install phpmyadmin php-fpm
   ```

   During the installation, you will be prompted to choose the web server that should be automatically configured to run phpMyAdmin. **DO NOT** select any web server option. Press Tab, then Enter to continue without selecting a web server.

   You will also be prompted to configure a database for phpMyAdmin. Choose "Yes" and enter your MySQL root password when prompted.

3. Configure PHP-FPM:
   Open the PHP-FPM configuration file in a text editor. For example, using Nano:
   ```
   sudo nano /etc/php/7.4/fpm/php.ini
   ```

   Find the line that starts with `cgi.fix_pathinfo` and set it to `0`:
   ```
   cgi.fix_pathinfo=0
   ```

   Save the file and exit the editor.

4. Configure Nginx:
   Create a new server block configuration file for phpMyAdmin:
   ```
   sudo nano /etc/nginx/conf.d/phpmyadmin.conf
   ```

   Add the following configuration to the file:
   ```
   server {
       listen 80;
       server_name your_domain_or_ip;

       root /usr/share/phpmyadmin;
       index index.php;

       location / {
           try_files $uri $uri/ =404;
       }

       location ~ \.php$ {
           include snippets/fastcgi-php.conf;
           fastcgi_pass unix:/run/php/php7.4-fpm.sock;
       }

       location ~ /\.ht {
           deny all;
       }
   }
   ```

   Replace `your_domain_or_ip` with your actual domain name or server's IP address.

   Save the file and exit the editor.

5. Test Nginx Configuration:
   Run the following command to test the Nginx configuration:
   ```
   sudo nginx -t
   ```

   If the configuration test is successful, restart Nginx:
   ```
   sudo systemctl restart nginx
   ```

6. Access phpMyAdmin:
   You can now access phpMyAdmin by opening a web browser and entering your server's IP address or domain name. For example:
   ```
   http://your_domain_or_ip
   ```

   You should see the phpMyAdmin login page where you can enter your MySQL username and password to access your databases.

By following these steps, you should have phpMyAdmin installed and accessible on your Ubuntu server with Nginx in the cloud. You can use phpMyAdmin to manage your MySQL databases through a user-friendly web interface.