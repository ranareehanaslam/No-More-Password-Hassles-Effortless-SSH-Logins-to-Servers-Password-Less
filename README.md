
### Step 1: Generate SSH Key Pair

#### Windows and Linux:

1. 🖥️ **Open a terminal or PowerShell window.**

2. 💻 Generate a new SSH key pair with a 2048-bit key size:
   ```bash
   ssh-keygen -t rsa -b 2048
   ```
   This command initiates the creation of a secure SSH key pair.

3. 📂 Choose a location to save the key. Press `Enter` for the default location (`~/.ssh/id_rsa` on Linux, or `C:\Users\YourUsername\.ssh\id_rsa` on Windows).

4. 🔒 Optionally, add a passphrase for enhanced security.

### Step 2: Copy the Public Key to the Server

1. 💻 Display the content of your public key:
   ```bash
   cat ~/.ssh/id_rsa.pub   # On Linux
   Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"   # On Windows
   ```
   Copy the entire output.

2. 🌐 **Log in to your server.**

###  Configure SSH for Root (Additional Step)

1. 🖥️ Execute the following commands to set up SSH for the root user on your server:
   ```bash
   sudo mkdir -p ~/.ssh
   sudo chmod 700 ~/.ssh
   sudo touch ~/.ssh/authorized_keys
   sudo chmod 600 ~/.ssh/authorized_keys

   ```

### Step 3: Open or Create the `~/.ssh/authorized_keys` File

1. 📝 Open or create the `~/.ssh/authorized_keys` file for the user you are logging in as. Use a text editor like nano or vim:
   ```bash
   sudo nano ~/.ssh/authorized_keys
   ```

2. 📋 Paste the public key into this file and save it.

### Step 4: Configure SSH on the Server

1. 🛠️ Ensure secure permissions on the `~/.ssh` directory and `authorized_keys` file:
   ```bash
   chmod 700 ~/.ssh
   chmod 600 ~/.ssh/authorized_keys
   ```

2. 🔄 Restart the SSH service on the server:
   ```bash
   sudo service ssh restart   # On Linux
   ```
   For Windows, the service restart is not necessary.

### Step 5: Test Passwordless Login

1. 🖥️ Open a new terminal or PowerShell window.

2. 💻 Log in to your server without being prompted for a password:
   ```bash
   ssh username@your_server_ip
   ```
   Replace `username` with your server username and `your_server_ip` with the IP address or domain.

If set up correctly, you can now log in without entering a password. If the key is not found or authentication fails, it will prompt you for a password.

Remember to replace placeholders like `username` and `your_server_ip` with your actual server details.
