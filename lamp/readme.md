# DOCKER LAMP

This repository contains a Docker image for creating a LAMP development environment.

## How to install

I think you have already cloned the [repository](https://github.com/juanmacivico87/docker) containing the image, so let's go straight to the steps to create your container: 

1. Enter the *lamp* folder in the repository by running ```cd lamp``` command.
2. Replace the contents of *app* directory by the code of your PHP project.
3. Now, run ```docker build . -t lamp:latest``` to build the image you are going to use to build your container.
4. Edit the *hosts* file of your operating system and add the following line:

```
127.0.0.1 test.docker.com
::1 test.docker.com
```

5. The next step is to lift the container. To do this, run ```docker run -d -p 80:80 lamp:latest``` command. This will bind port 80 of your machine to port 80 of your container.
6. If you are in a development environment, the above command can look like this: ```docker run -d -p 80:80 -v /path/to/repository/app:/var/www/html lamp:latest``` This way, you will create a volume inside the container so that you can see the changes you make in real time in the container.

With these simple steps, you now have a LAMP environment ready to work with your PHP project.
