# Docker Usage for Beginners

## Docker Workflow
1. Start the docker engine/daemon
2. Get an image
    * pull from Docker Hub
        * you can use the following command
        ```
            docker pull <image>
        ```
    * create image from a Dockerfile
        ```
            docker build .
        ```
3. Create a container using an existing image
    ```
        docker run -it --name <name> -p 8080:8080  <image>
    ```
    * -it : starts an interactive terminal from container
    * --name : custom name to identify container
    * -p <local\>:<container\> : port to connect container with local computer

## Additional Utilities
* Check your exisiting images
    ```
        docker images
    ```
* Check your running containers
    ```
        docker ps
    ```
    * -a : show all containers (even not running)
* Attach to a running container
    ```
        docker attach <container-name>
    ```
* Start a stopped containers
    ``` 
        docker start <container-name>
    ```
* Stop a running container
    ```
        docker stop <container-name>
    ```

## Favorite images 
Image | Utility | Use-case | Description
--- | --- | --- | --- |
alpine | linux-minimal | development, deployment | barebones linux distro, very lightweight
jupyter/minimal-notebook | jupyter | data, machine learning | allow jupyter server from container (remember to set port connection on run)
jupyter/pyspark-notebook | jupyter, pyspark | data, machine learning | jupyter server with pyspark setup