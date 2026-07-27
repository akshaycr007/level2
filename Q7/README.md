# Question 7: HTTPS Configuration for pddtestapp.luluone.com

## Overview
Configured Nginx as a reverse proxy with SSL termination on Port 443 using a self-signed OpenSSL certificate for pddtestapp.luluone.com.

## Configuration Details
- Domain: pddtestapp.luluone.com
- SSL Certificate: /etc/nginx/ssl/pddtestapp.crt
- SSL Key: /etc/nginx/ssl/pddtestapp.key
- Backend Container: http://127.0.0.1:8082 (myapp1)
- HTTP Redirection: Port 80 automatically redirects to HTTPS Port 443.

## How to Test
curl -I http://pddtestapp.luluone.com/
curl -k https://pddtestapp.luluone.com/
