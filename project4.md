# PROJECT 4  SETTING WORDPRESS WEBSITE USING LAMP STACK

## INTRODUCTION

In my project 4 i was able to use lamp stack which consists of Linux,Apache,MySQL,PHP to set up a Wordpress website.

**Linux** is major component of lamp stack,it serves as the operating system that support the entire configuration. In Lamp stack, Linux coordinates the interaction between Apache,MySQL & PHP,ensuring seamless operation between these components. This foundation allows for high performance, flexibility, and scalability, making Linux a crucial element in the successful deployment and management of a LAMP-based WordPress website.

**Apache** acts as the web server that handles client requests and serve web contents. Apache is known for its reliability, security, and flexibility. In a LAMP stack, Apache processes incoming HTTP requests, fetching and delivering web pages to users' browsers. It also supports various modules that extend its functionality, such as URL redirection, authentication, and load balancing

**MySQL** is the database management system within the LAMP stack, responsible for storing and managing the data that powers the web applications. As an open-source relational database, MySQL offers robust performance, scalability, and security. In the context of a LAMP stack, MySQL works closely with PHP to handle data operations such as storing user information, retrieving content, and managing transactions. For a WordPress website, MySQL stores all the content, user data, settings, and other essential information, allowing for dynamic content generation and efficient data retrieval. 

**PHP** is the scripting language in the LAMP stack, responsible for generating dynamic web content. In the LAMP stack, PHP works in tandem with Apache to handle web requests and interact with the MySQL database to retrieve and manipulate data. For a WordPress website, PHP executes the core logic that powers the site, managing everything from user authentication to content management and plugin functionality. By seamlessly integrating with Apache and MySQL, PHP ensures that your WordPress site is dynamic, interactive, and capable of delivering a rich user experience.


### Step 1; Deploying an ubuntu server

 i successsfully deployed my ubuntu server


### Step 2; Setting up Lamp Stack on the server

1. i step my inbound rule for my MySQL in my security group

2. i installed Apache running the following command

sudo apt update

sudo apt install apache2

sudo systemctl enable apache2

![1](<img/Screenshot 2024-09-16 230838.png>)

3. install MYSQL

sudo apt install mysql-server

sudo mysql_secure_installation

sudo systemctl enable mysql

4. Install Php

sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip

sudo apt install php libapache2-mod-php php-mysql

5. Created a vitual host for my website using Apache

i successfully created the directory for projectlamp

6. Enable PHP on the website

i successfully enabled my php on the website


### Step 3;  Install Wordpress

i proceeded to configure wordpress on the lampstack

1. Wordpress download and setup

cd /var/www/html

sudo wget -c http://wordpress.org/latest.tar.gz

sudo tar -xzvf latest.tar.gz

2. Database configuration for wordpress


sudo mysql -u root -p

 CREATE DATABASE wp_db;

 GRANT ALL PRIVILEGES ON wp_db.* TO jay@localhost;

 FLUSH PRIVILEGES;

 ![1](<img/Screenshot 2024-09-17 022848.png>)


### Step 4; Dns configuring and mapping

For public accessibility, i mapped the ip address to the DNS A record;

1. I successfully created an A record for my domain and sub domain

![1](<img/Screenshot 2024-09-17 022848.png>)


### Step 5; Securing the website with SSL/TLS

To enhance security, i installed ssl certificates using cartbot by running the following command;

sudo apt update 

sudo apt install certbot python3-certbot-apache

sudo certbot --apache

![1](<img/Screenshot 2024-09-17 024003.png>)

![1](<img/Screenshot 2024-09-17 024144.png>)


### CONCLUSION

Completing this project gave me an understanding of deploying WordPress with a LAMP stack and also gave me an understanding of what's possible in terms of setting up various tech stacks

End of project 4
 
 Thank you









