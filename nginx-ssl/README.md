# Nginx SSL Setup

This tutorial helps in configuring Nginx to accept https traffic using a self signed certificate.

## What is HTTPS ?

HTTPS is a secure version of HTTP. While HTTP sends data as plain text over a network, HTTPS uses encryption for securely transferring data over a network.

## How to generate a self signed certificate ?

We're using Nginx here as a TLS server to encrypt the communication between the internet and our Nginx server. To do so we'll need to generate a self signed certificate.

First let's create a new directory for our ssl certificates and private key:

```
sudo mkdir /etc/nginx/ssl
sudo chmod 700 /etc/nginx/ssl
```

Now the following command will generate a self signed certificate and private key. For private key we're using RSA key algorithm with a key 2048 bits size.

```
sudo openssl req -newkey rsa:2048 -keyout /etc/nginx/ssl/example.key -x509 -nodes -days 365 -out /etc/nginx/ssl/example.crt
```

Lastly we'll create nginx conf in `conf.d`:

```
cd /etc/nginx/conf.d/
sudo vim www.example.org.conf
```

And signal nginx to reload the configurations without restarting nginx:

```
sudo nginx -s reload
```
