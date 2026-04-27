# Create a repository on Docker Hub, push a Docker image to it, and pull the image from Docker Hub.

## Step 1
```
Go to: https://hub.docker.com/
signup and login
```
## Step 2
```
create a new repository name: my-docker-repo
```

## Step 3
```
1. Open AWS Console
2. Go to: Amazon Web Services
3: Launch EC2 Instance
4. Go to EC2 Dashboard
5. Click Launch Instance
    Configure:
    Name: docker-instance
    OS: Amazon Linux 2
    Instance type: t2.micro (free tier)
    Allow:
    SSH (port 22)
    HTTP (port 80)
6. Click Launch
7. Click connect
```

## Step 4
```
sudo yum update -y
sudo yum install docker -y
```

## Step 5
```
sudo systemctl start docker
```

## Step 6
```
sudo usermod -aG docker ec2-user
```

## Step 7
```
mkdir myapp
cd myapp
```

## Step 8
```
1. nano index.html
    Content: <h1>Hello from Docker on AWS EC2!</h1>
2. nano Dockerfile
    Content: FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```

## Step 9
```
sudo docker build -t my-image .
```

## Step 10
```
sudo docker tag my-image yourusername/my-docker-repo:latest
```

## Step 11
```
docker login
```

## Step 12
```
sudo docker push pihuuhuu/my-docker-repo:latest
```

## Step 13
```
Verify on Docker Hub
Go back to Docker Hub website
Open your repository
You’ll see your image (latest tag)
```

## Step 14
```
sudo docker pull yourusername/my-docker-repo:latest
```
