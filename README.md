Docker-Node Application
=======================

This repository contains a basic Node.js application that is set up to run inside a Docker container.

Prerequisites
-------------

Before you begin, make sure your development environment includes Docker and Node.js.

Project Setup
-------------

1.  Clone the repository:

    `git clone https://github.com/ajinsunny/dockernodeapp.git
    cd dockernodeapp`

Dockerizing the Application
---------------------------

1.  Build the Docker image:

    `docker build -t dockernodeapp .`

2.  Run the Docker container:

    `docker run -p 8080:3000 dockernodeapp`

The application is now running inside a Docker container and listening on port 8080 of your host machine. You can access it at [http://localhost:8080](http://localhost:8080/).

Making Changes
--------------

Since the Docker image is a static snapshot of the application, any changes you make to the application code after building the Docker image will not be reflected in the Docker container.

To see changes in the Docker container, you need to rebuild the Docker image and rerun the Docker container:

1.  Make changes to your application code.

2.  Rebuild the Docker image:

    `docker build -t dockernodeapp .`

3.  Stop the running Docker container. Get the container ID with:

    `docker ps`

    Then stop the container with:

    `docker stop [CONTAINER_ID]`

4.  Rerun the Docker container:

    `docker run -p 8080:3000 dockernodeapp`

You can use Docker volumes to avoid having to rebuild the Docker image every time you make changes to the application code:

`docker run -p 8080:3000 -v $(pwd):/usr/src/app dockernodeapp`

This command mounts the current directory (`$(pwd)`) on your host machine as `/usr/src/app` inside the Docker container. Now, any changes you make to the application code in your host machine directory will be reflected in the Docker container.

Stopping the Application
------------------------

To stop the Docker container from listening on port 8080, you can use the `docker stop` command with the ID of your Docker container.

Get the container ID with `docker ps`, then stop the container with `docker stop [CONTAINER_ID]`. Replace `[CONTAINER_ID]` with your actual container ID.
