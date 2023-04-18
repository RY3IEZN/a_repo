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
 
 *** enable,start,check status of apache***
 
 `sudo systemctl start httpd`
 `sudo systemctl status httpd`
