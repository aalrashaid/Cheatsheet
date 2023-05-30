To configure Nginx on an Ubuntu server in the cloud, you can follow these steps:

1. Create a Server Block Configuration File:
   By default, Nginx configuration files are located in the `/etc/nginx/sites-available` directory. Create a new configuration file for your website or application using a text editor. For example:
   ```
   sudo nano /etc/nginx/sites-available/example.com
   ```

   Replace `example.com` with your domain or a descriptive name for your configuration.

2. Configure the Server Block:
   In the configuration file, add the following server block to define the behavior of your website or application:

   ```
   server {
       listen 80;
       listen [::]:80;

       server_name example.com;

       root /var/www/example.com/public;

       index index.html index.htm index.php;

       location / {
           try_files $uri $uri/ /index.php?$query_string;
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

   Make sure to replace `example.com` with your actual domain or server name. Adjust the `root` directive to the path of your website or application's public directory.

   If you're using PHP, ensure that the `fastcgi_pass` directive points to the correct PHP-FPM socket file. The example above assumes PHP 7.4. If you're using a different PHP version, adjust the path accordingly.

3. Enable the Server Block:
   Create a symbolic link to enable the server block configuration by running the following command:
   ```
   sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
   ```

   Replace `example.com` with the actual configuration file name.

4. Test the Configuration:
   Before applying the configuration, it's recommended to test it for syntax errors. Run the following command:
   ```
   sudo nginx -t
   ```

   If there are no errors, you'll see a message indicating that the configuration file is valid.

5. Restart Nginx:
   Once the configuration is validated, restart Nginx to apply the changes:
   ```
   sudo systemctl restart nginx
   ```

   Nginx will now use the new server block configuration for your website or application.

6. Adjust Firewall (Optional):
   If you have a firewall enabled on your server, make sure to allow incoming HTTP (port 80) and HTTPS (port 443) traffic to access your Nginx server. Refer to your firewall documentation for instructions on how to open specific ports.

   For example, if you are using UFW as your firewall, you can run the following commands to allow HTTP and HTTPS traffic:
   ```
   sudo ufw allow 'Nginx HTTP'
   sudo ufw allow 'Nginx HTTPS'
   ```

   Replace `Nginx HTTP` and `Nginx HTTPS` with the appropriate service names for your firewall.

With these steps, you should have Nginx successfully configured on your Ubuntu server in the cloud. Your website or application should now be accessible through Nginx using the specified server block configuration.