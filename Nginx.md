To install Nginx on an Ubuntu server in the cloud, you can follow these steps:

1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages. Run the following command:
   ```
   sudo apt update
   ```

2. Install Nginx:
   Run the following command to install Nginx on your server:
   ```
   sudo apt install nginx
   ```

   This command will download and install Nginx from the Ubuntu package repository.

3. Start Nginx Service:
   After the installation is complete, start the Nginx service using the following command:
   ```
   sudo systemctl start nginx
   ```

   This command will start the Nginx service and make it active.

4. Enable Nginx on Boot:
   To ensure that Nginx starts automatically when the server reboots, run the following command:
   ```
   sudo systemctl enable nginx
   ```

   This command adds Nginx to the system's startup services.

5. Verify the Installation:
   After starting Nginx, you can verify if it is running correctly by opening a web browser and accessing your server's IP address or domain name. You should see the default Nginx welcome page.

6. Configure Firewall (Optional):
   If you have a firewall enabled on your server, you may need to allow incoming HTTP (port 80) and HTTPS (port 443) traffic to access your Nginx server. Refer to your firewall documentation for instructions on how to open specific ports.

   For example, if you are using UFW as your firewall, you can run the following commands to allow HTTP and HTTPS traffic:
   ```
   sudo ufw allow 'Nginx HTTP'
   sudo ufw allow 'Nginx HTTPS'
   ```

   Replace `Nginx HTTP` and `Nginx HTTPS` with the appropriate service names for your firewall.

With these steps, you should have Nginx successfully installed on your Ubuntu server in the cloud. You can now configure Nginx to host your websites or web applications.