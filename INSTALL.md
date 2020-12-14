# Install

## Before Starting:
The Instructions in this document will assume that prior to beginning any of the listed steps, you already have:
- Basic prior knowledge of Linux/Debian
- A running VPS
- A team GitHub Repository

---
---

## 1. Creating the nginx web server
The first step in hosting your own websites is to install the nginx package. First, you should update your packages and then use the command
`apt-get install nginx` to install the nginx package. If installation is successful, you should be able to view your web server by typing in your VPS IP address or domain name into your browser.

---

## 2. Uploading personal websites to server
The next step is to navigate to your `/var/www/html/` directory, which is where all your public HTML code will go. If you have a website ready to deploy, feel free to create a new directory with your name and upload your website to that, otherwise you can make one now or skip this step if you do not wish to have a personal website.

---

## 3. Installing Jekyll and creating group website
The next step is setting up your Jekyll website.

---

## 4. Creating auto-deploy script
The auto-deploy script is meant to automatically update the live website by pulling the changes from github. 
`while true
	do
		cd /home/debian/UnixFinalProject
		git pull
		cd groupSite
		bundle exec jekyll build
		sudo cp -r _site/. /var/www/html/
		sleep 300
	done
`

---
---

### Authors
- Peter Parthimos
- Nicolas Spagnolo