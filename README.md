### Starter Dockerized React Nginx App 

&nbsp;
&nbsp;

Let's build a docker react app using nginx. This app module should give us a good headstart.

Let's start by cloning this app:
git clone https://github.com/prabhakarBU/react-nginx-docker-app.git

OR 

Follow along the tutorial to create files step by step.

Section 1: ( Download Docker )
Let's download and install Docker using below link:
https://www.docker.com/products/docker-desktop/

Section 2: ( Create React app via command line and run it once without the Docker on the local machine )
npx create-react-app npx-react-app
Run it on local once. We should have package.json to build and run the project.
Run npm install to install all packages with node_modules added to your root folder.
Run npm run build to compile and build.
Run npm run start to start the app on port 3000.
Go to -> http://localhost:3000

Section 3: ( Add Nginx )
Copy the contents of nginx to the folder nginx like in this repository to 
your newly created project.
Or, add the following contents to your nginx file manually:


Section 4: ( Add Dockerfile )
Create Dockerfile and .dockerignore in your root folder and copy contents from this repository.
Add following content to Dockerfile if you want to do manually:

Add following content to Dockerfile if you want to do manually:

Section 5: ( Understand package.json )
Our package.json has all the dependencies our react app needs so far with the scripts that
will help it to build and run.


Section 6: ( Run Docker commands to build image and Run container )
1. Build the Docker Image:
From the root of the app, run the following docker build command with tags:
docker build -f Dockerfile -t npx-react-app:latest .
Command Break-down:
-f is used to specify the filename. If you don't specify it then you must rename your file to Dockerfile - that's what the build command looks for in the current directory by default.
-t is used to tag the image. You can tag your image the way you want (e.g v1.0.0, v2.0.0, production, latest, etc.)
. at the end is important, and it should be added to tell docker to use the current directory.
2. Run the Container from the above created image:
docker run -p 80:80 --rm react-app-image:latest
Command Break-down:
-p to expose and bind ports. Here we are exposing port 80 of the container and binding it with port 80 of the host machine. The first one is of your machine (host OS) and the second one is of the docker image container. For example, if you use -p 1234:80 then you will need to go to http://localhost:1234 on your browser.
--rm to remove the container once it is stopped
react-app-image:latest the name:tag of the image we want to run container of
3. Run the webapp:
Go to your browser and type: http://localhost:80

There you go! 
We have successfully dockerized our react web-app and hosted on our local machine.