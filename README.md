# Jenkins Installation Guide

## Introduction
Jenkins is an open-source automation server that helps automate the software development process, including building, testing, and deploying applications. This guide provides step-by-step instructions on how to install Jenkins on Ubuntu.

## Prerequisites
Before installing Jenkins, ensure you have the following:
- A system running Ubuntu (20.04 or later recommended)
- A user account with sudo privileges
- Java installed (Jenkins requires Java to run)

## Step 1: Update System Packages
```sh
sudo apt update && sudo apt upgrade -y
```

## Step 2: Install Java
Jenkins requires Java. Install OpenJDK by running:
```sh
sudo apt install openjdk-11-jdk -y
```
Verify the installation:
```sh
java -version
```

## Step 3: Add the Jenkins Repository
```sh
wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian/jenkins.io-2023.key
```
```sh
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

## Step 4: Install Jenkins
```sh
sudo apt update
sudo apt install jenkins -y
```

## Step 5: Start and Enable Jenkins Service
```sh
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
Check the status:
```sh
sudo systemctl status jenkins
```

## Step 6: Allow Firewall Access
Jenkins runs on port **8080** by default. Allow it through the firewall:
```sh
sudo ufw allow 8080
sudo ufw enable
sudo ufw status
```

## Step 7: Access Jenkins
Open a web browser and go to:
```sh
http://your-server-ip:8080
```

## Step 8: Retrieve Jenkins Administrator Password
To unlock Jenkins, retrieve the initial admin password:
```sh
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Copy and paste this password into the Jenkins web interface.

## Step 9: Complete Jenkins Setup
1. Choose **Install suggested plugins**.
2. Create an **Admin User**.
3. Configure Jenkins settings.

## Step 10: Start Using Jenkins
Jenkins is now installed and ready to use! 🎉

## Troubleshooting
- If Jenkins fails to start, check logs:
  ```sh
  sudo journalctl -u jenkins -f
  ```
- If firewall issues occur, reset rules:
  ```sh
  sudo ufw reset
  ```

## Conclusion
You have successfully installed Jenkins on Ubuntu. Now you can start automating your development workflow! 🚀

