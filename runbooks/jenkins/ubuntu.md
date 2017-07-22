# Install Jenkins on Ubuntu

```
wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
```

## Optional

Use NGINX 

```
sudo apt -y install nginx
```

Remove the default site

```
cd /etc/nginx/sites-available
sudo rm default ../sites-enabled/default
```

```
sudo cat > jenkins
upstream app_server {
    server 127.0.0.1:8080 fail_timeout=0;
}
 
server {
    listen 80;
    listen [::]:80 default ipv6only=on;
    server_name ci.yourcompany.com;
 
    location / {
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_redirect off;
 
        if (!-f $request_filename) {
            proxy_pass http://app_server;
            break;
        }
    }
}
```

Link the newly created site

```
sudo ln -s /etc/nginx/sites-available/jenkins /etc/nginx/sites-enabled/
```

Restart NGINX

```
sudo service nginx restart
```
