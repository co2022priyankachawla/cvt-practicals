# Create multiple Docker images using Dockerfiles, run containers from those images, and verify them by listing both images and running containers.

## Step 1
```
1. Go to EC2 Dashboard
2. Select your instance
3. Click Connect → EC2 Instance Connect → Connect
```

## Step 2
```
sudo yum update -y
```

## Step 3
```
sudo yum install docker -y
```

## Step 4
```
sudo systemctl start docker
```

## Step 5
```
sudo systemctl enable docker
```

## Step 6
```
docker --version
```

## Step 7
```
mkdir docker-lab
cd docker-lab
```

## Step 8 (First App)
```
mkdir nginx-app
cd nginx-app
```

## Step 9
```
echo "<h1>Hello from Nginx on AWS</h1>" > index.html
```

## Step 10
```
nano Dockerfile
Content: FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```

## Step 11
```
sudo docker build -t nginx-image1 .
```

## Step 12
```
sudo docker run -d -p 8081:80 --name nginx-container1 nginx-image1
```

## Step 13 (Second App)
```
cd ..
mkdir apache-app
cd apache-app
```

## Step 14
```
echo "<h1>Hello from Apache on AWS</h1>" > index.html
```

## Step 15
```
nano Dockerfile
Content: FROM httpd:latest
COPY index.html /usr/local/apache2/htdocs/index.html
```

## Step 16
```
sudo docker build -t apache-image2 .
```

## Step 17
```
sudo docker run -d -p 8082:80 --name apache-container2 apache-image2
```

## Step 18 (Verify)
```
sudo docker images
sudo docker ps
```

## Step 19 (To access these ports)
```
Your containers won’t load unless ports are open.

Go to:
EC2 → Security Groups → launch-wizard-?  -> Inbound Rules → Edit
Add:
Port 8081 → Anywhere (0.0.0.0/0)
Port 8082 → Anywhere (0.0.0.0/0)

to see launch-wizard-number:
👉 EC2 → Instances
👉 Click your instance

Scroll down → Security tab

You will see something like:

Security groups: launch-wizard-?
```

## Step 20
```
http://your_public_ip:8081/
http://your_public_ip:8082/
```
