# Getting Started With Docker

### Docker Concept
**What is a Docker**
- Docker is a containerization technology which enables us to share the kernel, system resources & dependencies.That means, it enables developers to package applications into containers. 
- Containers are standardized executable components combining application source code with the operating system libraries and dependencies required to run that code in any environment.
-  It also provides isolated environment and resource management to our application on an operating system level.
- It consists of a Docker Engine Application. A Docker Engine consists of 
  1. A server with a long running daemon process called dockerd.
  2. APIs which specify interfaces that programs can use to talk and instruct the Docker Daemon.
  3. A Command Line Interface (CLI) client called Docker.
- Docker CLI uses the docker APIs to control or interact with docker daemon.

**Dockerd**
- The docker daemon dockerd listens for the docker API requests and creates or manages the docker objects such as images, containers, networks and volumes.
- Docker Daemon can also communicate with other Daemons to manage the Docker Services.

**Docker CLI**
- It is the primary way that many Docker users interact with the Docker. When we uses the commands such as `docker run` the client send these commands to the dockerd which carries and work on them.
- The Docker command uses Docker APIs.
- The Docker Client can communicate with more that one daemon.

**Docker Desktop**
- Docker Desktop is an easy-to-install application for your Mac or Windows environment that enables you to build and share containerized applications and microservices. Docker Desktop includes the Docker daemon (dockerd), the Docker client (docker), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper.

**Docker registries**
- Docker registry stores the Docker Images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own private registry.
- When we use the `docker pull` or `docker run` commands, the required images are pulled from your configured registry and When we use the `docker push` command, our current image is pushed to the configured registry.

**Docker Objects**
- When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects.

**Images**
- An image is read only template with instructions for creating a Docker Container. Often, an image is based on another image, with some additional customization. For example, you may build an image which is based on the ubuntu image, but installs the Apache webserver and your application, as well as the configuration details needed to make your application run.
- You might create your own images or you might only use those created by others and published in a registry. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.

*Containers*
- A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.
- By default, a container is relatively well isolated from other containers and its host machine. You can control how isolated a container’s network, storage, or other underlying subsystems are from other containers or from the host machine.
- A container is defined by its image as well as any configuration options you provide to it when you create or start it. When a container is removed, any changes to its state that are not stored in persistent storage disappear.

**docker run command**
- The following command runs an ubuntu container, attaches interactively to your local command-line session, and runs /bin/bash.
`docker run -i -t ubuntu /bin/bash`
- Docker starts the container and executes /bin/bash. Because the container is running interactively and attached to your terminal (due to the -i and -t flags), you can provide input using your keyboard while the output is logged to your terminal.
- When you type exit to terminate the /bin/bash command, the container stops but is not removed. You can start it again or remove it.
- When you run this command, the following happens (assuming you are using the default registry configuration):
  1. If you do not have the ubuntu image locally, Docker pulls it from your configured registry, as though you had run `docker pull ubuntu` manually.
  2. Docker creates a new container, as though you had run a `docker container create` command manually.
  3. Docker allocates a read-write filesystem to the container, as its final layer. This allows a running container to create or modify files and directories in its local filesystem.
  4. Docker creates a network interface to connect the container to the default network, since you did not specify any networking options. This includes assigning an IP address to the container. By default, containers can connect to external networks using the host machine’s network connection.

- Docker is written in the *Go programming language* and takes advantage of several features of the Linux kernel to deliver its functionality. 
- Docker uses a technology called *namespaces* to provide the isolated workspace called the container. 
- When you run a container, Docker creates a set of namespaces for that container.
- These namespaces provide a layer of isolation. Each aspect of a container runs in a separate namespace and its access is limited to that namespace.

### Docker in action
##### Hello worlding in docker
`docker run hello-world`
- As we dont have any hello-world image or container locally, it will pull in from the default registry Docker hub. 
- Output of hello world
```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.
```

### VM vs LXC vs Docker
- If we are running the virtual machine, that VM would actually reserve some hard disk space, network bandwidth, RAM, CPU for itself. And it would run like a guest kind of operating system with our main operating system. And will have truly virtualized environment for ourself. On host operating system, multiple VMs can be ran and actually a complete full-blown operating system running inside each VM. By default they cannot communicate with each other but we can make them to communicate b/w those. And they are isolated from each other in lot of cases on a hardware level as well. 
- LXC - Linux Containers are basically same as a virtual machine but instead of installing full operating system, what it does is that it will not install all the components of OS but a kind of a minimal version of it. But there is a thin line b/w VMs and LXC. These are a light weight version of VMs.
- Docker, unlike VMs and LXCs, it will not include the functionality of an OS at all. The thing with docker is it uses lot of resources of the host operating system. 
- It able to use the host os resources by using the linux kernel functionalities.
- If docker installed correctly, we can make a great use of it. We can run a lot of containers which might simultaneously share the CPU cycles, CPU control and everything. 
- Docker contains a engine which allows us to run multiple containers sharing a lot of resources with each other but the same time providing isolation as well.


* Content here is gathered from various online resources and just gathering notes for understanding.
