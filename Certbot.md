To install Certbot on a cloud server running Ubuntu, follow these steps:

1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages. Run the following command:
   ```
   sudo apt update
   ```

2. Install Certbot:
   Install Certbot and the necessary components by running the following command:
   ```
   sudo apt install certbot
   ```

3. Choose Certbot Plugin:
   Certbot supports various plugins depending on the web server you're using. Choose the appropriate plugin based on your web server:
   
   - For Nginx, use the following plugin:
     ```
     sudo apt install python3-certbot-nginx
     ```

   - For Apache, use the following plugin:
     ```
     sudo apt install python3-certbot-apache
     ```

   Make sure to replace `python3-certbot-nginx` or `python3-certbot-apache` with the correct package name for your web server.

4. Obtain SSL/TLS Certificate:
   Run Certbot to obtain and install the SSL/TLS certificate for your domain. Replace `example.com` with your actual domain name:
   
   - For Nginx, use the following command:
     ```
     sudo certbot --nginx -d example.com -d www.example.com
     ```

   - For Apache, use the following command:
     ```
     sudo certbot --apache -d example.com -d www.example.com
     ```

   Certbot will guide you through the process of generating and installing the certificate. Follow the prompts and provide the necessary information when asked.

5. Automatic Certificate Renewal:
   Certificates obtained with Certbot expire after a certain period. To ensure automatic renewal of certificates, set up a cron job to run the Certbot renewal command. Run the following command to open the crontab file:
   ```
   sudo crontab -e
   ```

   Add the following line to the crontab file to run Certbot renewal every day at a specified time (e.g., 2:30 AM):
   ```
   30 2 * * * certbot renew --quiet
   ```

   Save the file and exit. Certbot will automatically check for expiring certificates and renew them if necessary.

By following these steps, you can install and configure Certbot on your Ubuntu server to obtain and manage SSL/TLS certificates for your domains.