# 3 tier app, switching things up!

# step1 create a vm with a redHat distro
by now, you know how to spin up a vm with the desired specs

# step2 add 3 block storages to your vm
lets go

click on the "volumes" tab, create a new volume and then attach to your vm

![image](https://user-images.githubusercontent.com/73601265/232903281-5f15c7bc-6f0e-42f7-a80a-c302e8f4d9e9.png)

run the command `lsblk`

![image](https://user-images.githubusercontent.com/73601265/232903864-9ce73920-7389-44b4-8e4d-8486fd0e8cb9.png)



# step4 install wordpress apache on the WEB SERVER

 this time around its `sudo yum -y update`
 
 ***install apache and its other dependencies php wget***
 
 `sudo yum install httpd php wget`
 
 ***enable,start,check status of apache***
 
 `sudo systemctl start httpd`
 
 `sudo systemctl status httpd`

![image](https://user-images.githubusercontent.com/73601265/232910532-7ce2afd5-6549-4352-b156-7bcc8a716b47.png)

***install wordpress, move it to /var/html/www***

run this cmds in the order

``` 
mkdir wordpress

cd   wordpress

sudo wget http://wordpress.org/latest.tar.gz

sudo tar xzvf latest.tar.gz

sudo rm -rf latest.tar.gz

cp wordpress/wp-config-sample.php wordpress/wp-config.php

cp -R wordpress /var/www/html/ 

```
***install and connect mysql to wordpress***
NB. THIS SHOULD BE DONE ON THE DB SERVER FIRST
quickly run

```
sudo yum update
sudo yum install mysql-server
```

enable start status of mysql

```
sudo systemctl restart mysqld
sudo systemctl enable mysqld
```

create a user and a db
```
sudo mysql
CREATE DATABASE wordpress;
CREATE USER `myuser`@`<Web-Server-Private-IP-Address>` IDENTIFIED BY 'mypass';
GRANT ALL ON wordpress.* TO 'myuser'@'<Web-Server-Private-IP-Address>';
FLUSH PRIVILEGES;
SHOW DATABASES;
exit
```

![image](https://user-images.githubusercontent.com/73601265/232915592-49f55438-da3c-4083-9162-b7299771ccb4.png)

***install mysql clinet and confirm you can reach the otherdb***

![image](https://user-images.githubusercontent.com/73601265/232916181-462df927-da2c-48a0-8a2f-1eaccda3262e.png)

NB. THIS SHOULD BE DONE ON THE WEBSERVER NEXT

```
sudo yum update
sudo yum install mysql-client
```
***connect to the other db***

sudo mysql -u admin -p -h <DB-Server-Private-IP-address>
 
 
 # finally visit your website via yourPublicIp/wordpress
 
 ![image](https://user-images.githubusercontent.com/73601265/232920120-b3dc47d5-c66f-4357-943e-8ec65a8db6ab.png)





