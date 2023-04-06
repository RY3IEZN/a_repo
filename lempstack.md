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


# some extra steps to ensure php and mysql are communicating
login, create a new db, and save
create a schema also


CREATE TABLE example_database.todo_list (
     item_id INT AUTO_INCREMENT,
     content VARCHAR(255),
     PRIMARY KEY(item_id)
);

![image](https://user-images.githubusercontent.com/73601265/230253393-a3289764-98b4-44b7-a61c-360fa9e3f203.png)

add some dummy data
INSERT INTO example_database.todo_list (content) VALUES ("My 2ndt important item");
INSERT INTO example_database.todo_list (content) VALUES ("My 3rd important item");

it should look like this 
![image](https://user-images.githubusercontent.com/73601265/230254170-98ecf61b-1189-4054-838a-967676b551b7.png)

then create a php script that connects php to mysql

sudo nano /var/www/projectLEMP/todo_list.php and add the following

`
<?php
$user = "example_user";
$password = "password";
$database = "example_database";
$table = "todo_list";


try {
  $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}`

//

7. Save and close the file when you are done editing.
You can now access this page in your web browser by visiting the domain name or public IP address configured for your website, followed by /todo_list.php

#####################################3
![image](https://user-images.githubusercontent.com/73601265/230256734-fc8fdb67-07f3-42ad-883c-6a940db0d514.png)

