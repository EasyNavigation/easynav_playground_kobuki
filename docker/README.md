# EasyNav ROS 2 Kilted - Docker

This repository contains the 'Dockerfile' to use SummitXL playground, the image builds a ROS2 Kilted environment and the EasyNav workspace ready to use. Also contains a launcher for a easy use of the docker.

## Instalation

```bash
docker build -t easynav_playground:kobuki_kilted .
```

## Usage

### Option A: using the script `launch.sh`
 
The first time Grant execute permissions to the script:
```bash
chmod +x launch.sh
```
 
Execute: 
```bash
./launch.sh
```
 
This script:

- Temporarily allows the Docker the access to the graphic server  (`xhost +local:docker`).
- Launch the docker allowing to see the Gazebo and RVIZ windows.
- When exiting Docker, revoke access to the graphical server.

### Option B: in our terminal
 
```bash
xhost +local:docker
 
docker run -it --rm \
  --net=host \
  -e DISPLAY=$DISPLAY \
  --device /dev/dri \
  --name playground_kobuki \
  --gpus all \
  -e ROS_DOMAIN_ID=$ROS_DOMAIN_ID \
  easynav_playground:kobuki_kilted
 
xhost -local:docker
```
