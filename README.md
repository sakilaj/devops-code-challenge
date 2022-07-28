# Overview
This demo project contains two apps, the Backend and the Frontend.

In each app's folder, there is a Dockerfile to containerize the apps.

# Objective
In this project demo, I am deploying the two app in different containerized forms using docker containers. This is done using an EC2 ubuntu instance.
Instead of using localhost, I am using the public IP of my EC2 instance for this demonstration.
# Submission
1. Firstly, I have created an ec2 instance from AWS and accessed the server via SSH
2. Then I have also forked and cloned the challenge project to my server
3. I downloaded Docker to my ec2 instance using (sudo apt install docker.io -y)
4. I performed the following steps to create a docker image for my backend app:
* Inside the backend folder, I have created a Dockerfile which is use to create image for the backend app
* I ran ($ sudo docker build -t backend .) command to provision the image specified in the Dockerfile from DockerHub.
* I located this image by running ($ sudo docker images) which showed the image info.
* The image for backend app is successfully created.
5. To create image for the frontend application, I followed the below steps:
* I cd inside the frontend folder and created a Dockerfile in that folder.
* My Dockerfile created a frontend image using the command ($sudo docker build -t frontend .)
* I also verified that the frontend image is created by running ($ sudo docker images) command.
6. At this point, I have created the images for both the frontend and the backend apps. 
7. The next was to create a container
 
# Configuration changes in the application code

1. I needed some configuration changes done in the config.js of both the Frontend and the Backend apps.
2. to do these, I went to the frontend app folder and inside src folder to locate a config.js
* Inside config.js, I replaced localhost with the public ip of my current ec2 instance and the port will remained same.
3. Similary, I went to the backend app folder and edited the config.js.
* Inside config.js, I replaced localhost with the public ip of my current ec2 instance and the port will remained same.

# Running the application container

1. Now, I run the backend app in a container with the container name "backend_app", I used following commands to set up the backend app and to map the port 8080 to server port 8080:
* sudo docker run -itd --name backend_app -p 8080:8080 backend sh
2. Now container for backend app was created. I ran the application in the container and the prot is listened 8080 using my pulic ip by running these:
* sudo docker exec -it backend_app /bin/sh
* npm ci
* npm start
3. Next step was to make sure that the backend app was running on port 8080, I checked this by using "http://public_ip:8080"

4. Similary, I started another terminal to run the frontend app in a container with the container name "frontend_app". I used following commands to set up the frontend application in a container and mapped the port 3000 to server port 3000. To do this, I ran:
* sudo docker run -itd --name frontend_app -p 3000:3000 frontend sh

5. The container for backend app was created, I ran the application in the container and listened the app's port 3000 using my pulic ip by running these:
* sudo docker exec -it frontend_app /bin/sh
* npm ci
* npm start
6. Next step was to make sure that the backend app was running on port 3000, I checked this by using "http://public_ip:3000"

# outcome of this demostration

1. when you hit the  url for backend app by using "http://public_ip:8080" you will get respose with an id of the Backend app.
2. In the Frontend app, there is a function App() which is returning response id of the Backend app as an output if the connectivity is good between the Backend and the Frontend or else it gives error "fail to fetch" message.

# realtime demo urls:

- for my backend app use: http://44.203.45.158:8080
- for my frontend app use: http://44.203.45.158:3000

Note: If connectivity is in place, the Frontend app will display same ID as the Backend app as a message.
There is no "SUCCESS" message as this is not indicated in the code by the developer. In order to get the "SUCCESS" message, the developer will need to update the App.js file.