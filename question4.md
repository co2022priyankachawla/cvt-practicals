# Pull Docker images (like python, hello-world, ubuntu) from Docker Hub, run containers, inspect running and stopped containers, and remove containers using Docker commands.

## Step 1
```
Go to Amazon Web Services Console
Navigate to EC2 → Instances
Click Launch Instance
    Configure:
    Name: docker-practical
    AMI: Amazon Linux 2
    Instance type: t2.micro (free tier)
    Key pair: create/download .pem
Click Launch
Connect
```

## Step 2
```
sudo yum update -y
sudo yum install docker -y
```

## Step 3
```
sudo systemctl start docker
```

## Step 4
```
sudo usermod -aG docker ec2-user
```

## Step 5
```
docker --version
docker login
```

## Step 6
```
docker pull hello-world
docker pull python
docker images
```

## Step 7
```
docker run hello-world
```

## Step 8
```
docker run -it python
inside python: print("Hello from Python container")
```

## Step 9
```
docker ps -a
```

## Step 10
```
docker stop <container_id>
```

## Step 11
```
docker rm <container_id>
```
