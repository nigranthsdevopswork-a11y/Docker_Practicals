# Nginx Static Website Deployment

## 📌 Project Overview
This project shows how to deploy a static website using Nginx Docker container.

## 🚀 Steps to Run

1. Pull nginx image
   docker pull nginx

2. Run container
   docker run -d -p 8080:80 nginx

3. Copy website files
   docker cp index.html container_id:/usr/share/nginx/html/

## 📸 Screenshots
(Add images here)

## 👨‍💻 Author
Your Name
