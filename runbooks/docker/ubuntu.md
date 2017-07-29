# Install Docker on Ubuntu

As root

```
apt-get install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"
apt-get update

apt-get install -y docker-ce
```

As normal user

```
usermod -aG docker $USER
```
