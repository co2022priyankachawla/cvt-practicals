# Create a simple web application, create a Dockerfile for the application, build a Docker image, and run a container to serve the web application.

## Step 1
```
Create an new EC2 Instance and Click Connect.
```

## Step 2
```
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
```

## Step 3
```
mkdir mywebapp
cd mywebapp
```

## Step 4
```
1. nano index.html
    Content: <!DOCTYPE html>
            <html>
            <head>
                <title>My Docker App</title>
            </head>
            <body>
                <h1>Hello from Docker on AWS 🚀</h1>
            </body>
            </html>
2. nano Dockerfile
    Content: FROM nginx:latest
            COPY index.html /usr/share/nginx/html/index.html
```

## Step 5
```
sudo docker build -t mywebapp-image .
sudo docker images
```

## Step 6
```
sudo docker run -d -p 8080:80 --name mywebapp-container mywebapp-image
sudo docker ps -a
```

## Step 7
```
Allow Port in AWS
Go to EC2 → Security Groups → Edit Inbound Rules
Add:
Type: Custom TCP
Port: 8080
Source: Anywhere (0.0.0.0/0)
```

## Step 8
```
Go to: http://<your-ec2-public-ip>:8080
```

## Step 9 (Optional)
```
sudo docker stop mywebapp-container
sudo docker rm mywebapp-container
sudo docker rmi mywebapp-image
```
