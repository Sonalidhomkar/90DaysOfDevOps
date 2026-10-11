# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

Today I am learning how to deploy a web server on a cloud instance using AWS EC2, Docker, and Nginx. I am also learning about SSH access, security groups, and log management.

## 1. Connect to the Cloud Server

Connect to an Ubuntu EC2 instance using SSH:

```bash
ssh -i your-key.pem ubuntu@<your-instance-public-ip>
```

This command connects to the remote server using an SSH private key.

## 2. Update the System

```bash
sudo apt update
sudo apt upgrade -y
```

These commands update the package list and install available system updates.

## 3. Install Docker

```bash
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker
```

These commands install Docker, start the service, enable it at startup, and check its status.

## 4. Install and Configure Nginx

```bash
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
```

Nginx is a web server used to serve web pages over HTTP.

## 5. Configure Security Groups

Configure the EC2 security group to allow the required inbound traffic:

| Protocol | Port | Purpose |
|---|---:|---|
| SSH | 22 | Remote server access |
| HTTP | 80 | Access the Nginx webpage |

For better security, restrict SSH access to your own IP address whenever possible.

## 6. Verify the Nginx Webpage

Open the following URL in your browser:

```text
http://<your-instance-public-ip>
```

Replace the placeholder with your instance's public IP address.

If Nginx is running and the network configuration is correct, the default Nginx welcome page should appear.

## 7. Check Nginx Logs

### View Access Logs

```bash
sudo tail -n 50 /var/log/nginx/access.log
```

Displays the latest 50 lines of the Nginx access log.

### View Error Logs

```bash
sudo tail -n 50 /var/log/nginx/error.log
```

Displays the latest 50 lines of the Nginx error log.

## 8. Save Logs to a File

```bash
sudo tail -n 50 /var/log/nginx/access.log > ~/nginx-logs.txt
cat ~/nginx-logs.txt
```

The first command saves the latest access-log entries to `nginx-logs.txt`. The second command displays the saved contents.

## 9. Download the Log File

Run this command from your **local computer**, not from the EC2 SSH session:

```bash
scp -i your-key.pem ubuntu@<your-instance-public-ip>:~/nginx-logs.txt .
```

This copies the log file from the EC2 instance to the current local directory. Replace the key filename and public IP with your actual values.

## 10. What I Learned Today

- How to connect to a cloud server using SSH.
- How to install and manage Docker and Nginx.
- How to configure security groups for web access.
- How to verify a webpage using a public IP address.
- How to inspect and save Nginx logs for troubleshooting.

## 11. Why This Matters for DevOps

Cloud server deployment is an important DevOps skill. It helps me understand infrastructure provisioning, remote server management, service deployment, network security, and log analysis.

These skills are useful when deploying and troubleshooting applications in cloud environments.

## Day 08 Takeaway

Today I learned the steps involved in setting up a cloud server, installing a web server, configuring network access, and collecting logs.

**Day 08: Building my practical cloud deployment skills for my DevOps journey.**
