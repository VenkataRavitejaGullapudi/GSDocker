# Getting Started With Docker

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







* Content here is gathered from various online resources and just gathering notes for understanding.
