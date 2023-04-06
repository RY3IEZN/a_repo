here are the steps to install the LEMP stack with Nginx:

1.Update the package index: Before installing any software, it's a good practice to update the package index on your server.
Run the following command to update the package index:

sudo apt update

2.Install Nginx web server: To install Nginx web server, run the following command:

sudo apt install nginx

Once the installation is complete, Nginx should start automatically. You can verify that Nginx is running by visiting your server's public IP address in a web browser.
You should see the Nginx default welcome page.
![image](https://user-images.githubusercontent.com/73601265/230247568-64127789-5c8d-4895-acde-cabec362a89c.png)

3.Install MySQL database server: To install MySQL database server, run the following command:
sudo apt install mysql-server

NB:During the installation, you'll be prompted to set a root password for MySQL. Choose a strong password and remember it.
![image](https://user-images.githubusercontent.com/73601265/230247851-8f45caf4-e44e-4529-b861-c6762dc6b77c.png)

4,Install PHP: To install PHP, run the following command:
sudo apt install php-fpm php-mysql

This will install PHP along with the necessary modules for connecting to MySQL from PHP.
after this a few other configurations will need tibe done to setup php and nginx together

A.Configure Nginx to use PHP-FPM: Nginx doesn't have built-in PHP support like Apache does, so we need to configure it to use PHP-FPM. To do this,

create a new server block configuration file in the /etc/nginx/sites-available directory:
sudo nano /etc/nginx/sites-available/default
 edit it with the following details
 
 `server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/html;
    index index.php index.html index.htm index.nginx-debian.html;

    server_name _;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }
}`


Save and close the file. This configuration sets the root directory to /var/www/html and tells Nginx to use PHP-FPM to process PHP files.

B.Test PHP: To test if PHP is working correctly, create a new file called info.php in the web root directory:
sudo nano /var/www/html/info.php

Add the following code to the file:
<?php
phpinfo();
?>

Save and close the file. Then, navigate to http://your_server_IP_address/info.php in your web browser. You should see a page with information about your PHP installation.
![image](https://user-images.githubusercontent.com/73601265/230250065-2dfbe981-a59e-4d2e-b3a9-07cdab8c54a5.png)



