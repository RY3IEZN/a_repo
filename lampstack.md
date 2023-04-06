here are the steps to install the LAMP stack on an ubuntu vm

1.Update the package index: Before installing any software, it's a good practice to update the package index on your server. Run the following command to update the package index:

sudo apt update

2. Install Apache web server: To install Apache web server, run the following command:

sudo apt install apache2

Once the installation is complete, Apache should start automatically. You can verify that Apache is running by visiting your server's public IP address in a web browser. You should see the Apache2 Ubuntu Default Page.

<img src="https://user-images.githubusercontent.com/73601265/229630473-e0ebc011-9f39-4698-996b-2c513225bce8.png" alt="alt_text" style="height:50%;width:100%;">

3.Install MySQL database server: To install MySQL database server, run the following command:

sudo apt install mysql-server -y

During the installation, you'll be prompted to set a root password for MySQL. Choose a strong password and remember it.

![image](https://user-images.githubusercontent.com/73601265/229631773-5ad9a9ca-8bfe-41b7-84e1-a2f171544662.png)

4.Install PHP: To install PHP, run the following command:

sudo apt install php libapache2-mod-php php-mysql -y

This will install PHP along with the necessary modules for connecting to MySQL from PHP.

Test PHP: To test if PHP is working correctly, create a new file called info.php in the web root directory:
input and save this code into the file ## <?php phpinfo();##

Then, navigate to http://your_server_IP_address/info.php in your web browser. You should see a page with information about your PHP installation.

![image](https://user-images.githubusercontent.com/73601265/229634618-3de0c71e-7c81-452f-b311-df5e966623a9.png)

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

Save and close the file when you are done editing.
You can now access this page in your web browser by visiting the domain name or public IP address configured for your website, followed by /todo_list.php:

![image](https://user-images.githubusercontent.com/73601265/230256408-e7bb5ff1-7061-4a06-8164-0ee9f8bbf041.png)
