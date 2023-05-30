To install Node.js on a server running Ubuntu in the cloud, you can follow these steps:

Option 1:
1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages.Run the following command:
```
   sudo apt update
   ```

2. Install Node.js and npm:
   Run the following command to install Node.js and npm(Node Package Manager):
```
   sudo apt install nodejs
   ```

   This command will install the latest version of Node.js available in the Ubuntu package repository.

3. Verify the Installation:
   After the installation is complete, you can check the version of Node.js by running the following command:
```
   node -v
   ```

   You should see the installed version of Node.js printed on the console.

4. Install npm(Node Package Manager):
   npm is typically installed along with Node.js.You can verify the version of npm by running the following command:
```
   npm -v
   ```

   This will display the installed version of npm.

    Option 2:
1. Update Package Lists:
   Connect to your Ubuntu server via SSH and update the package lists to ensure you have the latest information about available packages.Run the following command:
```
   sudo apt update
   ```

2. Install Node.js Using NodeSource:
   Run the following commands to add the NodeSource repository and install Node.js:
```
   cd ~
   curl -sL https://deb.nodesource.com/setup_16.x -o /tmp/nodesource_setup.sh
   sudo bash /tmp/nodesource_setup.sh
   sudo apt install nodejs
   ```

   This will add the NodeSource repository, download and install the latest version of Node.js.

3. Verify the Installation:
   After the installation is complete, you can check the version of Node.js by running the following command:
```
   node -v
   ```

   You should see the installed version of Node.js printed on the console.

    Option 3(Using NVM - Node Version Manager):
1. Install NVM:
   Run the following commands to install NVM(Node Version Manager):
```
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
   source ~/.bashrc
   ```

   This will download and install NVM and update the bash configuration.

2. Install a Specific Node.js Version:
   Run the following commands to install a specific version of Node.js using NVM:
```
   nvm install v14.10.0
   nvm list
   ```

   This will install Node.js version 14.10.0 and list the installed Node.js versions.

With these steps, you should have Node.js successfully installed on your Ubuntu server in the cloud.You can now start using Node.js and npm to run your applications.