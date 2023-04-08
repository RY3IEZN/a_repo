In this project we are going to be installing react,node,mongodb and create a todo application. as usual

### step1 update your machinee

`sudo apt update && sudo apt upgrade -y`

### step2 install nodejs
this can be done by using the following commands, and then check the version to be sure it installed
<!--  -->
`sudo sudo apt-get install -y nodejs`

`node -v`

![image](https://user-images.githubusercontent.com/73601265/230696717-058ffeaa-b5d2-45fd-a5f2-da6d3732576f.png)

### step3 make a project folder, navigate into the folder, run `npm init`
to achivece this, follow the commands in this order

a `mkdir todo`

b `cd todo`

c `npm init` and follow the prompt clicking or selecting yes and inputting the correct values

### step 4 install expressjs and dotenv

run the command `npm install express` to install express
run the command `npm install dotenv` to install dot env

![image](https://user-images.githubusercontent.com/73601265/230696962-0141424f-172a-4aa7-a0aa-9d1f63bc8c72.png)

![image](https://user-images.githubusercontent.com/73601265/230696979-6b8cf9a9-a857-4ec4-8134-c62a8d5fec6f.png)


create a file index.js and update it with the provided information
`touch index.js`
feel free to use your editor of choice nano vi vim, i personally use nano.

#### start and test the application.
to start the application your run the `node index.js` and then visit your browser and go to `public_ip:5000`
![image](https://user-images.githubusercontent.com/73601265/230697194-2f07ffc1-1f26-4e93-8cbc-bcef3290136b.png)

#### before we procced

a.we need to write some code so help us work on the next section effectively, go ahead create a folder called `routes`, navigate into the folder `cd routes` create a file called `api.js` by typing `touch api.js` and fill it with the provided information

b.we also need to create models for our app, go ahead create a folder called `models`, navigate into the folder `cd models` create a file called `todo.js` by typing `touch todo.js` and fill it with the provided information:

heres a shortcut `mkdir models && cd models && touch todo.js && nano todo.js` this will do the above step and open an editor for you

### step 5 create the frontend
we will get back to create the db using mongo but for now lets quickly create the front end, wont take that much time
install the following

run `npx create-react-app clinet` - creates a folder called client with the react app in it
install the following
`
npm install concurrently

npm install nodemon

npm install axios
`

