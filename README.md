# DockerPractice

1. What is Docker?
    - Docker is a container management service. The keywords of Docker are develop, ship and run anywhere. The whole idea of Docker is for developers to easily develop applications, ship them into containers which can then be deployed anywhere.

2. Features
    - Docker has the ability to reduce the size of development by providing a smaller footprint of the operating system via containers.
    - With containers, it becomes easier for teams across different units, such as development, QA and Operations to work seamlessly across applications.
    - You can deploy Docker containers anywhere, on any physical and virtual machines and even on the cloud.
    - Since Docker containers are pretty lightweight, they are very easily scalable.

3. Download and Install Docker (I will be downloading for windows)

4. "docker run hello-world" for Windows or "sudo docker run hello-world" for Ubuntu
    - This command will download the hello-world image, if it is not already present, and run the hello-world as a container.

5. Docker Hub - https://hub.docker.com/

6. docker pull jenkins/jenkins
    - This command will pull all the jenkins required files from dockerhub.

7. docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins
    - jenkins/jenkins is the name of the image we want to download from Docker hub
    - -p is used to map the port number
    - Open http://localhost:8080/ or http://localhost:50000/ in your browser that will redirect you to unlock jenkins screen.
    - you can use password that has been generated in the terminal and paste it in the browser to proceed the installation.

8. Docker Images
    - In Docker, everything is based on Images. An image is a combination of a file system and parameters.
    - docker run hello-world 
        a. Docker command is specific and tells the Docker program on the Operating System that something needs to be done
        b. run command is used to mention that we want to create an instance of an image, which is then called a container
        c. "hello-world" represents the image from which the container is made.

9. docker run -it centos /bin/bash
-> centos is the name of the image we want to download from Docker Hub
-> ─it is used to mention that we want to run in interactive mode
-> /bin/bash is used to run the bash shell once CentOS is up and running

10. docker Images
-> To see the list of Docker images on the system
-> docker Images -q -> It tells the Docker command to return the Image ID’s only

11. docker rmi ImageID
->ImageID − This is the ID of the image which needs to be removed

12. docker inspect jenkins/jenkins
-> see the details of an image or container

13. docker ps
-> will show the currently running containers.
-> docker ps -a -> This command is used to list all of the containers on the system.

14. docker history centos
-> will show all the commands that were run against the centos image

15. docker top ContainerID 
-> ContainerID − This is the Container ID for which you want to see the top processes.

16. docker stop ContainerID 
-> ContainerID − This is the Container ID which needs to be stopped.

17. docker rm ContainerID 
-> ContainerID − This is the Container ID which needs to be removed.

18. docker stats ContainerID 
-> ContainerID − This is the Container ID for which the stats need to be provided.

19. docker attach ContainerID 
-> ContainerID − This is the Container ID to which you need to attach.

20. docker pause ContainerID 
-> This command is used to pause the processes in a running container.

21. docker unpause ContainerID
-> This command is used to unpause the processes in a running container.

22. docker kill ContainerID
-> This command is used to kill the processes in a running container.

23. Configure Docker
-> service docker stop -> This command is used to stop the Docker daemon process.
-> service docker start  -> This command is used to start the Docker daemon process.

24. nsenter 
-> Details will be added soon

25. Dockerfile
->A Docker File is a simple text file with instructions on how to build your images.

26. Check Dockerfile in the repository.

27. docker build –t myimage:0.1. 
-> -t − is to mention a tag to the image
-> myimage − This is the name you want to give to your image.
-> 0.1 − This is the tag you want to give to your image.
-> . − The directory where the Docker File is present.

28. Create repository named "demorep" in docker hub and get the command "docker pull username/demorep"

29. "docker login" in terminal  

30. docker tag imageID Repositoryname 
-> This is the ImageID which needs to be tagged to the repository.
-> This is the repository name to which the ImageID needs to be tagged to.
-> In will be executing this command "sudo docker tag ab0c1d3744dd username/demorep:1.0"
-> Then i will push the changes "docker push username/demorep:1.0"

31. Pull the docker image
-> Now First delete the myimage image from the docker
-> than "docker pull username/demorep:1.0"

32. Private Registry
-> Registry is the container managed by Docker which can be used to host private repositories.

33. docker run –d –p 5000:5000 –-name registry registry:2
-> We are just tagging the registry container as “2”, to differentiate it on the Docker host.
-> The –d option is used to run the container in detached mode. This is so that the container can run in the background

34. Let’s do a docker ps to see that the registry container is indeed running.

35. docker tag 5d0da3dc9764 localhost:5000/centos 
-> let’s tag one of our existing images so that we can push it to our local repository. In our example, since we have the centos image available locally, we are going to tag it to our private repository and add a tag name of centos.

36. docker push localhost:5000/centos 
-> let’s use the Docker push command to push the repository to our private repository.

37. docker rmi centos:latest , docker rmi 67591570dd29
-> let’s delete the local images we have for centos using the docker rmi commands.

38. docker pull localhost:5000/centos
-> we are pulling the centos image to the private repository hosted at localhost:5000.

39. Building a Web Server Docker File
-> Check the Dockerfile for more details

40. docker build –t=”mywebserver” .
-> Run the Docker build command to build the Docker file

41. docker run –d –p 80:80 mywebserver 
-> it’s now time to create a container from the image. We can do this with the Docker run command
-> Check the apache running at http://localhost:80

42. CMD Instruction - CMD command param1 
->This command is used to execute a command at runtime when the container is executed. 

43. FROM ubuntu 
MAINTAINER username@gmail.com 
CMD [“echo” , “hello world”] 
-> CMD is just used to print hello world.
-> Build the image using the Docker build command.
-> Run a container from the image.

44. ENTRYPOINT - ENTRYPOINT command param1 
-> This command can also be used to execute commands at runtime for the container.
-> command − This is the command to run when the container is launched.
-> param1 − This is the parameter entered into the command.

45. FROM ubuntu 
MAINTAINER demousr@gmail.com 
ENTRYPOINT [“echo”]
-> Build the image using the Docker build command.
-> Run a container from the image.

46. ENV - ENV key value 
-> This command is used to set environment variables in the container.
-> Key − This is the key for the environment variable.
-> value − This is the value for the environment variable.

47. FROM ubuntu 
MAINTAINER demousr@gmail.com 
ENV var1=Tutorial var2=point 
-> Build the image using the Docker build command - docker build -t="envdemo" .
-> Run a container from the image - docker run -it envdemo /bin/bash
-> execute the env command to see the environment variables - root@4t34t:/# env

48. WORKDIR - WORKDIR dirname 
-> This command is used to set the working directory of the container.

49. FROM ubuntu 
MAINTAINER demousr@gmail.com 
WORKDIR /newtemp 
CMD pwd
-> Build the image using the Docker build command - docker build -t="tempdemo" .
-> Run a container from the image - docker run tempdemo

50. Container Linking
-> docker jenkins pull
-> run the container, but this time, you can specify a name to the container by using the –-name option. This will be our source container - docker run --name=jenkins -d jenkins
-> launch the destination container, but this time, we will link it with our source container. For our destination container, we will use the standard Ubuntu image - docker run --name=reca --link=jenkins:alias-src -it ubuntu:latest /bin/bash
-> docker ps
-> type env in the root you will notice new variables for linking with the source container.
