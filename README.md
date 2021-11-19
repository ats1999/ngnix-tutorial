# NGNIX Tutorial

> I have used ubuntu 20.04 LTS for this turorial

## Setup NGNIX

### Install NGNIX
Because Nginx is available in Ubuntu’s default repositories, it is possible to install it from these repositories using the apt packaging system.

```js
sudo apt install nginx
```

#### Check installation
```js
ngnix -v
```

### Adjusting the Firewall
Before testing Nginx, the firewall software needs to be adjusted to allow access to the service. Nginx registers itself as a service with ufw upon installation, making it straightforward to allow Nginx access.
#### Enable the Firewall
```js
sudo ufw enable

sudo ufw app list
```
It is recommended that you enable the most restrictive profile that will still allow the traffic you’ve configured. Right now, we will only need to allow traffic on port 80.

```js
sudo ufw allow 'Nginx HTTP'
```
You can verify the change by typing:
```js
sudo ufw status
```

The output will indicated which HTTP traffic is allowed:
```js
rahul@rahul:~/Desktop/projects/vyorius/Maintenancedashboard$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
Nginx HTTP                 ALLOW       Anywhere                  
Nginx HTTP (v6)            ALLOW       Anywhere (v6)    
```

### Checking your Web Server
At the end of the installation process, Ubuntu 20.04 starts Nginx. The web server should already be up and running.

We can check with the systemd init system to make sure the service is running by typin
```js
systemctl status nginx
```
Output
```js
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2021-11-19 10:42:42 IST; 13min ago
       Docs: man:nginx(8)
   Main PID: 35108 (nginx)
      Tasks: 3 (limit: 8137)
     Memory: 5.3M
     CGroup: /system.slice/nginx.service
             ├─35108 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
             ├─35109 nginx: worker process
             └─35110 nginx: worker process

Nov 19 10:42:42 rahul systemd[1]: Starting A high performance web server and a reverse proxy server...
Nov 19 10:42:42 rahul systemd[1]: Started A high performance web server and a reverse proxy server.
```

As confirmed by this out, the service has started successfully. However, the best way to test this is to actually request a page from Nginx.

You can access the default Nginx landing page to confirm that the software is running properly by navigating to your server’s IP address. If you do not know your server’s IP address, you can find it by using the icanhazip.com tool, which will give you your public IP address as received from another location on the internet

#### Getting the default HTML
```js
curl localhost
```
#### Go to local server
http://localhost

## Cheers
