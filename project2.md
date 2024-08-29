# setting up multiple static website on a single server using Nginx virtual host

## Introduction

On my second project, i practiced setting up multiple static websites on a single server using Nginx virtual 

host. Below are the steps i took

### Step 1 
Installing and configuring Nginx on a server

1. i created my instance, associated my elastic ip to my instance 

2. i ssl my ubuntu server instance into my terminal

3. i installed Nginx by Excuting the following commands
'''
sudo apt update
sudo apt upgrade
sudo apt install nginx
,,,
4. i activated the Nginx server by running the command 'sudo systemctl start nginx' ,enable it to start on a boot by executing 'sudo systemctl enable nginx' , and i confirm if it's running with the 'sudo systemctl status nginx' command

 i visited my instance ip address to view the default Nginx startup page

 ![1](img/nginx%20setup.png)

 ### Step 2
 Creating two website directories with two diffrent website templates
 
 1. i used 2 free template from Tooplate

 2. i navigated to the '/var/www/html directory where the file would be stored

 3.i install the unzip tool by running the command 'sudo apt install unzip'

 4. i downloaded and unzipped the website file by running the command 'sudo curl -o /var/www/html/2098_health.zip https://www.tooplate.com/zip-templates/2098_health.zip && sudo unzip -d /var/www/html/ /var/www/html/2098_health.zip && sudo rm -f /var/www/html/2098_health.zip'

 Ran the command 'sudo curl -o /var/www/html/2132_clean_work.zip' to download the website file
   used the command 'https://www.tooplate.com/zip-templates/2132_clean_work.zip &&' to save it as a 2132_clean_work.zip in the /var/www/html directory ran the command 'sudo unzip -d /var/www/html/' to extract the contents of the zip file into the '/var/www/html/' directory 
   ' /var/www/html/2132_clean_work.zip' specifies the path to the zip file to be unzipped 
     '&& sudo rm -f' removes the specified file forcefully
      '/var/www/html/2132_clean_work.zip' specifies the path to the zip file to  be deleted

5. Downloaded and unzipped the second template by running the command 'sudo curl -o /var/www/html/2133_moso_interior.zip https://www.tooplate.com/zip-templates/2133_moso_interior.zip && sudo unzip -d /var/www/html/ /var/www/html/2133_moso_interior.zip && sudo rm -f /var/www/html/2133_moso_interior.zip'

6. i set up a website configuration by first of all running 'sudo nano /etc/nginx/sites-available/cleaning' to create a blank file in the nginx sites-available directory

7. I ran the following command in the new file and edited the root directive within my server block to point to the directory where the downloaded website content is stored.
'''
 server {
    listen 80;
    server_name example.com www.example.com;

    root /var/www/html/example.com;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
'''
8. i configured my second website by running 'sudo nano /etc/nginx/sites-available/health' to create a new file in the nginx sites available directory

9. Then i ran the command then edited my root directory like the first one
server {
    listen 80;
    server_name placeholder.com www.placeholder.com;

    root /var/www/html/placeholder.com;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

10. Created a symbolic link for both websites by running 'sudo ln -s /etc/nginx/sites-available/cleaning /etc/nginx/sites-enabled/'  'sudo ln -s /etc/nginx/sites-available/health /etc/nginx/sites-enabled/'

11. Run the 'sudo nginx -t' command to check the syntax of the Nginx configuration file.

12. I Deleted the default files in the sites-available and sites-enabled directories by executing the following commands:
'''
sudo rm /etc/nginx/sites-available/default
sudo rm /etc/nginx/sites-enabled/default
'''
Restart the Nginx server by executing the following command: 'sudo systemctl restart nginx'

###Step 3
I made my website accssible via my domain name rather than ip address. I did that by buying my domain name from **qservers.ng** and then moving hosting to Aws Route 53, where i set up my A record

1. In route 53, i created 2 record (subdomains) on my already exising domain name for project 1

![1](img/A%20record%20in%20route%2053.png)

2. I edited the settings of my terminal to enter my domain name for the first website by running 'sudo nano /etc/nginx/sites-available/cleaning' then saved the setting using ctrl + x

3. Edited the setting fo the second website too by running  'sudo nano /etc/nginx/sites-available/health'

4. Restart Nginx by running 'sudo systemctl restart nginx'

5. Then i checked my domain name on a web browser **cleaning.somto.com.ng**  **health.somto.com.ng**

![1](img/Screenshot%202024-08-25%20231201.png)  ![1](img/Screenshot%202024-08-25%20231538.png)

### Step 4

Install certbot and Request for an ssl/Tcl certificate

1. Install certbot by executing the following commands: 'sudo apt update sudo apt install python3-certbot-nginx sudo certbot --nginx'

2. requested for a certificate by running 'sudo certbot --nginx' the i followed the instruction provided by the certbot

3. Verify the website's SSL using the OpenSSL utility with the command: openssl s_client -connect cleaning.somto.com.ng:443

4. visited https://cleaning.somto.com.ng   https://health.somto.com.ng 

![1](img/secured%20cleaning.png)   ![1](img/secured%20health.png)

### In conclusion
In this project i was able to successfully host two static websites on a single server, and each accessible via its own domain and i also got ssl certificate to secure both

End of project


 


