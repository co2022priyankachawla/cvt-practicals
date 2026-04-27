# Connect to a given AWS EC2 instance and deploy the web page.

## Step 1
```
1. Go to Amazon Web Services console
2. Open EC2 Dashboard
3. Click Launch Instance
4. Configure:
    4.1: Name: MyWebServer
    4.2: AMI: Amazon Linux 2 (or Ubuntu)
    4.3: Instance type: t2.micro (free tier)
5. Create or select a Key Pair (download .pem file)
6. Network settings:
    6.1: Allow:
        6.1.1: SSH (Port 22)
        6.1.2: HTTP (Port 80)
7. Click Launch Instance
8. Connect to the Instance
```

## Step 2
```
sudo yum update -y
```

## Step 3
```
sudo yum install httpd -y
```

## Step 4
```
sudo systemctl start httpd
```

## Step 5
```
sudo systemctl enable httpd
```

## Step 6
```
sudo systemctl status httpd
```

## Step 7
```
cd /var/www/html
```

## Step 8
```
sudo nano index.html
```
```bash
<!DOCTYPE html>
<html>
<head>
    <title>AWS Web Server</title>
</head>
<body>
    <h1>Hello from EC2 🚀</h1>
    <p>My website is successfully deployed!</p>
</body>
</html>
```

## Step 9
```
sudo chmod 755 index.html
```

## Step 10 (Just to be sure if httpd is active (running))
```
sudo systemctl restart httpd
```

## Step 11
```
http://your_public_ip/
```

```
If the website is not responding:
1. Go to Amazon Web Services Console
2. Open EC2 → Instances
3. Select your instance
4. Click Security tab
5. Click Security Group
6. Go to Inbound Rules
7. Click Edit Inbound Rules
| Type | Protocol | Port | Source    |
| ---- | -------- | ---- | --------- |
| HTTP | TCP      | 80   | 0.0.0.0/0 |
```
