# Homelab
Home lab notes and docs

# Kuberneties setup

## Load Balancer

create an LXC ubuntu 22.04 container

apt update && apt upgrade -y
adduser xxxxx
usermod -aG sudo xxxxx

apt install nginx vim net-tools curl

vim /etc/nginx/nginx.conf

events {}

stream {
  upstream k3s_servers {
    server 192.168.60.20:6443;
    server 192.168.60.21:6443;
  }

  server {
    listen 6443;
    proxy_pass k3s_servers;
  }
}

systemctl start nginx
systemctl enable nginx
systemctl status nginx

netstat -plnt | grep -i 6443

nc -vz localhost 6443

nc -vz 10.11.11.60 6443

## Database

## Contol Node One

## Contol Node One

## Worker Nodes 

