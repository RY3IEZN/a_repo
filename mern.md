# step1 install nodejs
as usual apt update and upgrade

`sudo apt update && sudo apt upgrade`

then apt install nodejs

`sudo apt install -y nodejs`

check if it installed properly check the version

`node -v`

# step2 install mongodb
ill leave a link to a guide on how to install mongodb and test it by using the command mongod
https://www.linode.com/docs/guides/install-mongodb-on-ubuntu-20-04/

# step3 install npm and body parser express moongoose

`sudo apt install -y npm`

`sudo npm install body-parser`

`sudo npm install express`

`sudo npm install mongoose`

# step4 create the folder directories, copy the code and files

`mkdir Books && cd Books`

intialise the project in the books directory

`npm init`

create a file called server.js and update it with code from the repo

then

`mkdir apps && cd apps`

create a file called route.js and update it with code from the repo

in the "apps folder", make a directory and update as below

`mkdir models && cd models`

create a file called book.js and update it with code from the repo

***change back to the main directory"book" and then continue***

`cd ../..`








when you are done vist your publicIP:3300 and you should have something looking like this
![image](https://user-images.githubusercontent.com/73601265/232447555-bb296fc4-9207-4b16-88dc-f57e7cfe7152.png)
