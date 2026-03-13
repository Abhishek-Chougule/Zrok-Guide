# Zrok Installation & Usage Guide (Ubuntu / Linux / Windows)

This guide explains how to install **zrok** on Ubuntu and expose a **local server (like Frappe, Node, or any localhost app)** to the internet using a secure reverse proxy.

---

# What is zrok

zrok is a **secure sharing platform** that allows you to expose local services to the public internet without port forwarding.

Typical use cases:

* Access **localhost apps remotely**
* Share **Frappe / ERPNext development sites**
* Test **webhooks**
* Temporary **public demos**

---

# Prerequisites

* Ubuntu / Linux system
* Internet connection
* Terminal access
* A **zrok account**

Create a free account here:

https://zrok.io

After login, you will receive an **environment token** from:

https://api-v1.zrok.io

---

# Installation Steps (Ubuntu)

## Step 1 — Download zrok

```bash
wget https://github.com/openziti/zrok/releases/download/v1.1.11/zrok_1.1.11_linux_amd64.tar.gz
```

---

## Step 2 — Extract the archive

```bash
tar -xvzf zrok_1.1.11_linux_amd64.tar.gz
```

This will extract a binary named:

```
zrok
```

---

## Step 3 — Move binary to system path

```bash
sudo mv zrok /usr/local/bin/
```

This makes the command available globally.

---

## Step 4 — Verify installation

```bash
zrok version
```

Expected output:

```
zrok version v1.1.11
```

---

# Enable Your zrok Environment

After logging in to the console:

https://api-v1.zrok.io

Copy your **environment token** and run:

```bash
zrok enable <YOUR_TOKEN>
```

Example:

```bash
zrok enable zrktkn_xxxxxxxxxxxxxxxxx
```

This will create configuration files in:

```
~/.zrok
```

---

# Check Environment Status

```bash
zrok status
```

Expected output:

```
Environment: enabled
```

---

# Share a Local Server

To expose a local service running on port **8000**:

```bash
zrok share public 8000
```

or

```bash
zrok share public http://localhost:8000
```

Example output:

```
https://abcd1234.share.zrok.io
```

Now anyone can access your local server via that URL.

---

# Example: Share a Frappe Site

If your Frappe bench is running on:

```
http://localhost:8000
```

Start sharing:

```bash
zrok share public 8000
```

Now your local Frappe site will be accessible from the internet.

---

# Stop Sharing

Press:

```
CTRL + C
```

to stop the share.

---

# Useful Commands

Check environment:

```bash
zrok status
```

Disable environment:

```bash
zrok disable
```

List resources:

```bash
zrok overview
```

---

# Windows Installation

Download the Windows binary from:

https://github.com/openziti/zrok/releases

Extract and move:

```
zrok.exe
```

to:

```
C:/Users/<username>/bin/
```

Then run from Command Prompt or PowerShell:

```powershell
zrok version
```

---

# Security Notes

Do **NOT expose sensitive systems**, including:

* production servers
* databases
* client environments
* private networks

Only expose **development or demo environments**.

---

# Zrok Installation Script Guide (Linux / Ubuntu)   Easy Installation

This guide explains how to use the **automatic installation script** to install zrok on a Linux system.

Instead of manually downloading and installing zrok, the script performs all steps automatically.

---

# What the Script Does

The script performs the following tasks automatically:

1. Checks if required tools (`wget`, `tar`) are installed
2. Downloads the latest **zrok release (v1.1.11)**
3. Extracts the zrok binary
4. Moves the binary to the system path `/usr/local/bin`
5. Verifies the installation
6. Optionally enables the **zrok environment** using your token

---

# Step 1 — Clone or Download the Repository

Clone the repository containing the script.

```bash
git clone https://github.com/<your-username>/<repo-name>.git
```

Navigate into the directory:

```bash
cd <repo-name>
```

---

# Step 2 — Make the Script Executable

Before running the script, give it execution permission.

```bash
chmod +x install_zrok.sh
```

---

# Step 3 — Run the Installation Script

Run the script using:

```bash
./install_zrok.sh
```

This will:

* download zrok
* install it
* verify the installation

After installation you should see:

```
zrok version v1.1.11
```

---

# Step 4 — Enable Your Zrok Environment

Login to the zrok console:

https://api-v1.zrok.io

Copy your **environment token**.

Then run:

```bash
zrok enable <YOUR_TOKEN>
```

Example:

```bash
zrok enable zrktkn_abc123xyz
```

---

# Optional: Run Script with Token

You can also enable your environment directly using the script.

```bash
./install_zrok.sh <YOUR_TOKEN>
```

Example:

```bash
./install_zrok.sh zrktkn_abc123xyz
```

The script will automatically enable the environment after installation.

---

# Verify Installation

Run:

```bash
zrok version
```

Expected output:

```
zrok version v1.1.11
```

---

# Share a Local Server

Once installed and enabled, you can expose a local server.

Example for a service running on port **8000**:

```bash
zrok share public 8000
```

Example output:

```
https://abcd1234.share.zrok.io
```

Anyone with this link can access your local service.

---

# Example: Share a Frappe Site

If your Frappe site runs on:

```
http://localhost:8000
```

Run:

```bash
zrok share public 8000
```

Your local Frappe instance will now be accessible from the internet.

---

# Stop Sharing

To stop the share session press:

```
CTRL + C
```

---

# Troubleshooting

If the `zrok` command is not found, verify installation path:

```
which zrok
```

Expected output:

```
/usr/local/bin/zrok
```

If needed reload the shell:

```
source ~/.bashrc
```

---

# Security Warning

Never expose:

* production environments
* sensitive data
* internal company services

Only expose **development or demo systems**.

---

# References

Official Documentation

https://docs.zrok.io

GitHub Repository

https://github.com/openziti/zrok

---

# Summary

Install zrok

```
wget → extract → move to /usr/local/bin → enable environment
```

Share local server

```
zrok share public <port>
```

Access your local service from anywhere using the generated public URL.

---

Access your local application from anywhere using the generated URL.

---

Author

Abhishek Chougule
