# face_recognition_docker_virtual_machine
This is based on ageitgey/face_recognition with modifications to run as a container inside a virtual machine
The following commands are necessary so that you can run the live webcam samples and get the output when running this container from within a virtual machine
You have to make sure you virtual machine is able to see the camera device (please see lsusb). 

## Make sure that on your host, before running the container you execute: 
```
$ xhost +
```

## To run the container:
```
docker run -e DISPLAY=$DISPLAY --env QT_X11_NO_MITSHM=1 --volume=/tmp/.X11-unix:/tmp/.X11-unix:rw --volume /home/dockerusr/images:/root/images --device /dev/video0:/dev/video0 -it facerec:1.1 /bin/bash
```
