# Automated Apache Web Server Deployment on AWS EC2

This project demonstrates how to automate the setup of a web server on Amazon Linux 2023 using **AWS User Data** and **Bash Scripting**.

## 🎯 Project Objective
The goal was to launch an EC2 instance and automatically install, configure, and start an Apache HTTP server using bootstrapping.

## 🛠️ Tech Stack
* **Cloud Provider:** AWS (Amazon Web Services)
* **Service:** EC2 (Elastic Compute Cloud)
* **OS:** Amazon Linux 2023
* **Automation:** Bash Scripting
* **Web Server:** Apache (httpd)

---

## 📸 Step-by-Step Implementation

### Step 1: Choosing Amazon Machine Image (AMI)
I selected the **Amazon Linux 2023 AMI** (Free Tier eligible) as the base operating system.
![EC2 Setup](ec2_1.png)

### Step 2: Creating a Secure Key Pair
Created a new RSA key pair named `mywebserver-key` for secure access.
![Key Pair](keypair.png)

### Step 3: Automating with User Data Script
Added a **Bash script** in the User Data field to automate the installation of Apache.
![User Data Script](script.png)

### Step 4: Launching the Instance
The infrastructure is being provisioned and the script is executing.
![Launching Progress](launch.png)

### Step 5: Final Result (Success!)
The web server is live! The custom "Welcome" message is visible via the Public IP.
![Final Output](output.png)

---

## 📜 The Automation Script
```bash
#!/bin/bash
# Update the system
sudo yum update -y

# Install Apache web server
sudo yum install -y httpd

# Start and enable Apache
sudo systemctl start httpd
sudo systemctl enable httpd

# Create a custom landing page
echo "<html><h1>Welcome to Apache Web Server on Amazon Linux!</h1></html>" > /var/www/html/index.html
