# face_recognition_docker_virtual_machine
This is based on ageitgey/face_recognition with modifications to run as a container inside a virtual machine
The following commands are necessary so that you can run the live webcam samples and get the output when running this container from within a virtual machine
You have to make sure you virtual machine is able to see the camera device (please see lsusb). 

When you fork ageitgey/face_recognition just update the Dockerfile in there with the one in this repository.

## Make sure that on your host, before running the container you should execute: 
```
$ xhost +
```

## To run the container:
```
docker run -e DISPLAY=$DISPLAY --env QT_X11_NO_MITSHM=1 --volume=/tmp/.X11-unix:/tmp/.X11-unix:rw --volume /home/dockerusr/images:/root/images --device /dev/video0:/dev/video0 -it facerec:1.1 /bin/bash
```
Fixes issues like:
```
Error: BadDrawable (invalid Pixmap or Window parameter) 9 Major opcode: 62 (X_CopyArea)
```
```
No protocol specified : cannot connect to X server :0 
```
```
[WARN:0] global /io/opencv/modules/videoio/src/cap_v4l.cpp (802) open VIDEOIO ERROR: V4L: can't open camera by index 0
```
