# Mysql Client Server Archichtecure 

we are going to implement basic client-server using MySQL Relational Database Management System (RDBMS)


# step1 create 2 VM instances.
login in to your desired csp and create 2 virtual machines

![image](https://user-images.githubusercontent.com/73601265/232483380-71cd7e6c-1102-4054-8a12-5500584f6541.png)

# step2 install mysql server on 1 vm and mysql client on the other vm

### vm1 mysql server
as usual update, upgrade, install run as follows

`sudo apt update`

`sudo apt upgrade`

`sudo apt install mysql-server`
 
 to confirm its has intall run:
 
 `mysql --version`
 
 ![image](https://user-images.githubusercontent.com/73601265/232487618-1cfc1e6d-7fb1-48d2-82e0-960e9d5dac2e.png)

### vm2 mysql client

heres a 1 liner
`sudo apt update && sudo apt upgrade -y && sudo apt install mysql-client -y`
works like a charm

to confirm its has intall run:
 
 `mysql --version`
 
 ![image](https://user-images.githubusercontent.com/73601265/232489105-f68e99a3-304f-4f23-ad10-90bedc2f2b19.png)

# step3 run a secure mysql installation to secure the db

run it on both to secure the db in the vm

`sudo mysql_secure_installation`

# step4 check for connectivity between both vm
ping the client from the server and vice versa
using the "ping" command
eg `ping <private_ip_address>`
