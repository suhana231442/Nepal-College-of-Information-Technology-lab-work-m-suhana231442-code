# Lab 1: Hosting a Web Server on the Cloud

## 📌 Objective

- Access the AWS Console through the sandbox environment.
- Launch an AWS EC2 instance.
- Connect to the EC2 instance and install Nginx.
- Deploy a sample web page.
- Access the hosted web page through a web browser.

---

## 📖 Background Theory

### Cloud Computing in IoT

Cloud computing provides scalable computing resources over the internet, enabling IoT devices to store, process, and analyze data remotely. It reduces infrastructure costs while improving flexibility, reliability, and scalability.

### AWS EC2 (Elastic Compute Cloud)

Amazon EC2 is a cloud service that provides virtual servers (instances) for running applications. Users can choose different operating systems, instance types, and storage options based on their requirements.

### Nginx Web Server

Nginx is a lightweight, high-performance web server that can also function as a reverse proxy, load balancer, and HTTP cache. It is widely used for hosting websites due to its speed and reliability.

---

## 🛠 Requirements

- AWS Academy Learner Lab (Sandbox)
- AWS Console Access
- Ubuntu EC2 Instance
- SSH Client (Terminal or PuTTY)
- Internet Connection

---

## 🚀 Procedure

### Step 1: Launch an EC2 Instance

1. Log in to the AWS Console.
2. Open the **EC2 Dashboard**.
3. Click **Launch Instance**.
4. Configure:
   - **AMI:** Ubuntu Server
   - **Instance Type:** t2.micro
   - **Key Pair:** Create or use an existing key pair
   - **Security Group:** Allow SSH (22) and HTTP (80)
5. Launch the instance.

---

### Step 2: Connect to the EC2 Instance

```bash
ssh -i your-key.pem ubuntu@<Public-IP>
```

---

### Step 3: Update the System

```bash
sudo apt update
sudo apt upgrade -y
```

---

### Step 4: Install Nginx

```bash
sudo apt install nginx -y
```

Verify installation:

```bash
sudo systemctl status nginx
```

---

### Step 5: Create a Sample Web Page

```bash
sudo nano /var/www/html/index.html
```

Example HTML:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My AWS Web Server</title>
</head>
<body>
    <h1>Hello from AWS EC2!</h1>
    <p>This web server is hosted using Nginx on Amazon EC2.</p>
</body>
</html>
```

Save the file.

---

### Step 6: Access the Website

Open your browser and enter:

```
http://<Public-IP>
```

The sample web page should be displayed.

---

## 📂 Project Structure

```
Lab-1/
│
├── README.md
├── screenshots/
│   ├── ec2-instance.png
│   ├── nginx-installed.png
│   ├── webpage-output.png
│   └── security-group.png
└── index.html
```

---

## 📸 Output

### EC2 Instance Running

> *(Insert Screenshot)*

---

### Nginx Installed Successfully

> *(Insert Screenshot)*

---

### Hosted Web Page

> *(Insert Screenshot)*

---

## ✅ Result

- Successfully launched an AWS EC2 instance.
- Installed and configured the Nginx web server.
- Deployed a sample HTML webpage.
- Verified successful hosting by accessing the webpage using the EC2 public IP.

---

## 🎯 Conclusion

In this lab, a cloud-based web server was successfully deployed using Amazon EC2 and Nginx. The experiment demonstrated how cloud infrastructure can be used to host websites efficiently. This practical exercise provided hands-on experience with launching virtual machines, configuring web servers, and deploying web applications on the AWS cloud, highlighting the importance of cloud computing in modern IoT systems.

---

