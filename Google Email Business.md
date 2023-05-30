To configure a cloud server on DigitalOcean to use Google Email Business (G Suite) for sending and receiving emails, follow these steps:

1. Set up G Suite:
   If you haven't already, sign up for G Suite (Google Workspace) and set up your domain to use Google Email Business. Follow the instructions provided by Google to verify your domain ownership and configure the necessary DNS records.

2. Create a Cloud Server:
   Sign in to your DigitalOcean account and create a new cloud server. Choose the desired configuration based on your requirements. Make sure to select the Ubuntu operating system.

3. Set Up DNS Records:
   In the DigitalOcean control panel, navigate to the Networking section and access the DNS settings for your domain. Add the necessary DNS records provided by Google for G Suite. These records typically include MX, SPF, DKIM, and DMARC records.

4. Install Postfix:
   Connect to your cloud server via SSH and install the Postfix mail transfer agent using the following command:
   ```
   sudo apt update
   sudo apt install postfix
   ```

5. Configure Postfix for Google Email Business:
   Open the Postfix configuration file for editing:
   ```
   sudo nano /etc/postfix/main.cf
   ```

   Modify the following settings in the file:
   ```
   relayhost = [smtp.gmail.com]:587
   smtp_use_tls = yes
   smtp_sasl_auth_enable = yes
   smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd
   smtp_sasl_security_options = noanonymous
   ```

6. Create SASL Password File:
   Create a SASL password file using the following command:
   ```
   sudo nano /etc/postfix/sasl/sasl_passwd
   ```

   Add the following line to the file, replacing `<username>` and `<password>` with your G Suite email address and password:
   ```
   [smtp.gmail.com]:587    <username>@<domain>:<password>
   ```

   Save the file and close the editor.

7. Generate Hashed SASL Password:
   Generate the hashed SASL password file by running the following command:
   ```
   sudo postmap /etc/postfix/sasl/sasl_passwd
   ```

8. Restart Postfix:
   Restart the Postfix service to apply the changes:
   ```
   sudo systemctl restart postfix
   ```

9. Test Email Sending:
   To test if your server can send emails through Google Email Business, you can use the `mail` command. Run the following command:
   ```
   echo "This is a test email" | mail -s "Test" recipient@example.com
   ```

   Replace `recipient@example.com` with an email address where you want to receive the test email. If the email is successfully sent, you should receive it in the specified inbox.

Your cloud server on DigitalOcean is now configured to use Google Email Business for sending emails. Make sure to configure your email clients or applications to use the Google Email Business servers for both incoming and outgoing email settings.