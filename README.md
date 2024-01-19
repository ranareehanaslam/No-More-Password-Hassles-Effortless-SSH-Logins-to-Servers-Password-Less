Sure, I'll guide you through the process of generating SSH keys on Windows 11 and configuring passwordless login to an Ubuntu Server. Follow these steps:

### Step 1: Generate SSH Key Pair on Windows 11

1. Open PowerShell as an administrator.

2. Use the following command to generate an SSH key pair:
   ```bash
   ssh-keygen -t rsa -b 2048
   ```
   This command will create a new SSH key pair with a 2048-bit key size.

3. You will be prompted to enter a file in which to save the key. Press `Enter` to save it in the default location (`C:\Users\YourUsername\.ssh\id_rsa`).

4. You will also be prompted to enter a passphrase for extra security. You can press `Enter` to leave it blank, but adding a passphrase is recommended.

### Step 2: Copy the Public Key to the Ubuntu Server

1. Use the following command to display the content of your public key:
   ```bash
   Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"
   ```
   Copy the entire output.

2. Log in to your Ubuntu Server.

3. Open or create the `~/.ssh/authorized_keys` file for the user you are logging in as. You can use a text editor like `nano` or `vim`.

4. Paste the public key into this file and save it.

### Step 3: Configure SSH on Ubuntu Server

1. Ensure that the permissions on the `~/.ssh` directory and `authorized_keys` file are secure:
   ```bash
   sudo service ssh restart
   ```
### Step 4: Restart SSH on Ubuntu Server

1. Ensure that the permissions on the `~/.ssh` directory and `authorized_keys` file are secure:
   ```bash
   chmod 700 ~/.ssh
   chmod 600 ~/.ssh/authorized_keys
   ```

### Step 5: Test Passwordless Login

1. Open a new PowerShell window on Windows.

2. Use the following command to log in to your Ubuntu Server without being prompted for a password:
   ```bash
   ssh username@your_server_ip
   ```
   Replace `username` with your Ubuntu username and `your_server_ip` with the IP address or domain of your server.

If everything is set up correctly, you should now be able to log in without entering a password. If the key is not found or authentication fails, it will prompt you for a password.

Remember to replace placeholders like `username` and `your_server_ip` with your actual Ubuntu username and server details.
