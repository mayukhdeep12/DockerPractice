# DockerPractice

1. What is Docker?
-> Docker is a container management service. The keywords of Docker are develop, ship and run anywhere. The whole idea of Docker is for developers to easily develop applications, ship them into containers which can then be deployed anywhere.

2. Features
-> Docker has the ability to reduce the size of development by providing a smaller footprint of the operating system via containers.
-> With containers, it becomes easier for teams across different units, such as development, QA and Operations to work seamlessly across applications.
-> You can deploy Docker containers anywhere, on any physical and virtual machines and even on the cloud.
-> Since Docker containers are pretty lightweight, they are very easily scalable.

3. Download and Install Docker (I will be downloading for windows)

4. "docker run hello-world" for Windows or "sudo docker run hello-world" for Ubuntu
-> This command will download the hello-world image, if it is not already present, and run the hello-world as a container.

5. Docker Hub - https://hub.docker.com/

6. docker pull jenkins/jenkins
-> This command will pull all the jenkins required files from dockerhub.

7. docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins
-> jenkins/jenkins is the name of the image we want to download from Docker hub
-> -p is used to map the port number
-> Open http://localhost:8080/ or http://localhost:50000/ in your browser that will redirect you to unlock jenkins screen.
-> you can use password that has been generated in the terminal and paste it in the browser to proceed the installation.

8. Docker Images
-> In Docker, everything is based on Images. An image is a combination of a file system and parameters.
-> docker run hello-world 
    - Docker command is specific and tells the Docker program on the Operating System that something needs to be done
    - run command is used to mention that we want to create an instance of an image, which is then called a container
    - "hello-world" represents the image from which the container is made.

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
