# Launch and connect to an AWS EC2 instance and create a custom website using Chef. And prove idepotency.

## Step 1
```
Go to AWS Console → EC2
Click Launch Instance
    Configure:
    AMI: Amazon Linux 2
    Instance Type: t2.micro (free tier)
    Key Pair: create/download .pem
    Security Group:
    SSH → Port 22 → Anywhere
    HTTP → Port 80 → Anywhere
Click Launch
Click Connect
```

## Step 2
```
sudo yum update -y
```

## Step 3
```
curl -L https://omnitruck.chef.io/install.sh | sudo bash -s -- -P chef-workstation
chef -v
```

## Step 4
```
mkdir chef-repo
cd chef-repo
```

## Step 5
```
chef generate cookbook mywebsite
```

## Step 6
```
cd mywebsite
```

## Step 7
```
nano recipes/default.rb
Content: package 'httpd' do
  action :install
end

service 'httpd' do
  action [:enable, :start]
end

file '/var/www/html/index.html' do
  content '<h1>Welcome to My Chef Website</h1>'
  action :create
end
```

## Step 8
```
cd ~/chef-repo
sudo chef-client -z -o 'recipe[mywebsite]' --config-option cookbook_path=~/chef-repo/cookbooks
```

## Step 9
```
Refer this chatgpt link: https://chatgpt.com/share/69efa988-9374-83e8-b9fa-8d33db699ed9
```
