# Pi Pico Docker Image
This is a Docker image for Raspberry Pi Pico development, which includes the following:
- Pi Pico C/C++ SDK
- Pi Pico C/C++ Examples
- Pi Pico C/C++ Extras
- Pi Pico C/C++ Playground
- Picotool
- Required tools for Pi Pico development (e.g. cmake, make, gcc, gdb, etc.)

## Buiding the docker image    
    $ docker build -t picodev/picodev_build:1.0 -f .devcontainer/Dockerfile .

## Running the docker image
The following command will run the docker image and mount the current directory to the docker container. This will allow you to edit the files on your host machine and compile them in the docker container.
```    
$ docker run -it --rm --name=picodev \
    --mount type=bind,source=${PWD},target=/usr/src/pico-dev \
 	picodev/picodev_build:1.0 bash
```

## VSCode: Attach to Running Container
Install the [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension in VSCode. 

Open the folder containing the Pi Pico project you want to work on. Click on the green icon in the lower left corner of the VSCode window and select "Remote-Containers: Attach to Running Container". 

Select the container named "picodev" and you should be able to compile and debug your Pi Pico project.