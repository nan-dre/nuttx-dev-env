# Docker environment for Embedded Systems lab

## Prerequisites
* Linux host
* Docker
* ESP32 board needs to be connected to your laptop before starting the Docker container, otherwise it will throw an error that /dev/ttyUSB0 couldn't be found.

## Building
```
docker build -t nuttx .devcontainer
```

## Running
```
docker run -it --device=/dev/ttyUSB0 -v nuttx:/root/nuttxspace/nuttx -v apps:/root/nuttxspace/apps nuttx
```
Now you can attach vscode to this running container, or you can use Dev Containers (no need to build/run the docker container)

## Vscode Dev Container setup
1. Clone this repo: ```git clone --recurse-submodules git@github.com:nan-dre/nuttx-dev-env.git```
2. Open inside vscode: ```code nuttx-dev-env```
3. Install [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
4. Ctrl+Shift+P -> Dev Containers: Rebuild and Reopen in Container
