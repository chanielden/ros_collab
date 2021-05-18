# Fetch Docker

### Prerequisites

* Install Docker - https://docs.docker.com/engine/install/ubuntu/
* Optional: Install Nvidia Docker to access gpu inside docker - https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker 

### Installation
1. Pull image from Dockerhub
   ```sh
   sudo docker pull chanielden/ros-melodic-openpose
   ```
   
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
   ```
2. Ensure cmake-gui is newer than version 3.12

3. Cmake configuration
   ```sh
   mkdir build/
   cd build/
   cmake-gui ..
   ```
   Click configure. Select Unix Makefiles, you should see 'configuring done'. Then click Generate.

4. Compilation
   ```sh
   make -j`nproc`
   ```

5. Test that the installation works
   Return to the openpose main directory and run the test command with hand detection.
   ```sh
   cd ..
   ./build/examples/openpose/openpose.bin --hand
   ```



