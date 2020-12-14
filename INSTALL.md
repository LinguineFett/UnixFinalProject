# Install

Hello and welcome to the **Pog Bois Install Markdown file**.

## Before Starting:

The Instructions in this document will assume that prior to beginning any of the listed steps, you already have:
- Basic prior knowledge of Linux/Debian
- A running VPS
- A team GitHub Repository

---
---

## 1. Creating the nginx web server
The first step in hosting your own websites is to install the nginx package. First, you should update your packages and then use the command
```apt-get install nginx``` to install the nginx package. If installation is successful, you should be able to view your web server by typing in your VPS IP address or domain name into your browser.

---

## 2. Uploading personal websites to server
The next step is to navigate to your `/var/www/html/` directory, which is where all your public HTML code will go. If you have a website ready to deploy, feel free to create a new directory with your name and upload your website to that, otherwise you can make one now or skip this step if you do not wish to have a personal website.

---

## 3. Installing Jekyll and creating group website
The next step is setting up your Jekyll website.<br>
Inside your VPS, follow the following commands to install Jekyll:<br>
### 1. Install Ruby and other prerequisites
```bash
sudo apt-get install ruby-full build-essential zlib1g-dev
```
### 2. Create a gem installation in your user folder
```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```
### 3. Install Jekyll and Bundler
```bash
gem install jekyll bundler
```
In order to create your jekyll website, you can simply modify the markdown files or create posts in the posts directory to create your content. You can also get new themes to completely modify the look of your site. You can then run the command `jekyll build` to create the proper HTML files in the directory called `/_site`

---

## 4. Creating auto-deploy script
The auto-deploy script is meant to automatically update the live website by pulling the changes from github. <br>
```bash
while true
do
	cd /home/debian/UnixFinalProject
	git pull
	cd groupSite
	bundle exec jekyll build
	sudo cp -r _site/. /var/www/html/
	sleep 300
done
```

---
---

## Authors
- __Peter Parthimos__
- __Nicolas Spagnolo__