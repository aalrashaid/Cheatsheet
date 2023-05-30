Certainly! Here's an updated version of the steps that includes the installation of the required packages `software-properties-common`, `ca-certificates`, `lsb-release`, and `apt-transport-https`:

1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages. Run the following command:
   ```
   sudo apt update
   ```

2. Install Required Packages:
   Install the necessary packages `software-properties-common`, `ca-certificates`, `lsb-release`, and `apt-transport-https` by running the following command:
   ```
   sudo apt install software-properties-common ca-certificates lsb-release apt-transport-https
   ```

3. Add PHP Repository:
   Add the repository that contains the desired PHP versions. For example, to add the ondrej/php repository, run the following command:
   ```
   sudo add-apt-repository ppa:ondrej/php
   ```

   This will add the repository to your system.

4. Update Package Lists:
   Update the package lists again to include the packages from the newly added repository:
   ```
   sudo apt update
   ```

5. Install PHP 8.1:
   Run the following command to install PHP 8.1 and its necessary extensions:
   ```
   sudo apt install php8.1 php8.1-cli php8.1-fpm php8.1-mysql php8.1-xml php8.1-mbstring php8.1-curl php8.1-gd php8.1-zip
   ```

   This command installs PHP 8.1 along with commonly used extensions. Feel free to install additional extensions as per your requirements.

6. Install PHP 7.4 (Optional):
   If you also want to install PHP 7.4 alongside PHP 8.1, run the following command:
   ```
   sudo apt install php7.4 php7.4-cli php7.4-fpm php7.4-mysql php7.4-xml php7.4-mbstring php7.4-curl php7.4-gd php7.4-zip
   ```

7. Configure PHP Versions:
   Use the `update-alternatives` command to configure the PHP versions and switch between them. Run the following command:
   ```
   sudo update-alternatives --config php
   ```

   This command will display a list of available PHP versions installed on your system. Enter the number corresponding to the desired PHP version (8.1 or 7.4) and press Enter.

8. Verify PHP Installation:
   After switching PHP versions, you can verify the PHP installation and check the PHP version by running the following command:
   ```
   php -v
   ```

   You should see the PHP version information printed on the console, confirming that the selected PHP version is active.

By following these updated steps, you can install PHP 8.1 and/or PHP 7.4 on your Ubuntu 20.04 server and switch between them using the `update-alternatives` command.