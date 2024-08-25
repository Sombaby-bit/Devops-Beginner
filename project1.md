# my name is Somto

i'm an aspiring Devops Engineer

-First task

1. i bought a domain from qserver.ng
![1](img/Screenshot%202024-08-24%20210214.png)

2. i spinned up my ubuntu server by opening a terminal in the directory where my .pem file was downloaded and i associated the ip address of my instance to the elastic ip associated to it

3. i installed Nginx by running  sudo apt update  sudo apt upgrade  sudo apt install nginx  on my ubuntu server. started nginx by running sudo systemctl start nginx , enabled it to run on a boot by excuting sudo systemctl enable nginx ,then i confirmed if it was running with sudo systemctl status nginx . i copied my public IPv4 address and the pasted it in a web browser to view my nginx set up

4. i downloaded free HTML website from Tooplate then copid the url to my terminals

5. i downloaded and unzipped the website files to the nginx directory 

6. i input my public IPv4 address on my web browser to see if its working

![1](img/website.png)

7. i created an A record in route 53 and added my ip address

![1](img/A%20record%20in%20route%2053.png)

8. i used my domain name to varify my website on a web browser

9.  i installed certbot and request for ssl/tls certificte to enable https on my website

10. i validated the website ssl using the openssl utility


