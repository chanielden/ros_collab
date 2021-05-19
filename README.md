# Fetch Docker

### Prerequisites

* Install Docker - https://docs.docker.com/engine/install/ubuntu/
* Optional: Install Nvidia Docker to access gpu inside docker - https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker 

### Installation
1. Pull image from Dockerhub
   ```sh
   sudo docker pull chanielden/ros-melodic-openpose
   ```
   This docker has cuda 10.0 and cuDNN 7.5 installed.
   
2. Clone this repo
   ```sh
   git clone https://github.com/chanielden/ros_gesture.git
   cd ros_gesture
   ```
   
### Running the docker
  start.sh script contains the command to run the docker. First cd to the openpose_docker directory and run:
   ```sh
      sudo ./start.sh
   ```

### Setting up Openpose
1. Clone the Openpose repo
   ```sh
   git clone https://github.com/CMU-Perceptual-Computing-Lab/openpose
   cd openpose/
   git submodule update --init --recursive --remote
   git checkout tags/v1.7.0
   ```
2. Ensure cmake-gui is newer than version 3.12

3. Cmake configuration
   ```sh
   mkdir build/
   cd build/
   cmake-gui ..
   ```
   Click configure. Select Unix Makefiles, you should see 'configuring done'. 
   Ensure BUILD_PYTHON is selected and the python paths are linked to py2.7.
   Then click Generate.

4. Compilation
   ```sh
   make -j`nproc`
   make install
   ```

5. Test that the installation works
   Return to the openpose main directory and run the test command with hand detection.
   ```sh
   cd ..
   ./build/examples/openpose/openpose.bin --hand
   ```

### Setting up catkin packages

1. Enter the catkin_ws/src directory
   ```sh
   cd /home/root/catkin_ws/src
   git clone https://github.com/code-iai/iai_kinect2.git
   git clone https://github.com/ravijo/ros_openpose.git
   ```

2. Enable python scripts
   ```sh
   roscd ros_openpose/scripts
   chmod +x *.py
   ```

