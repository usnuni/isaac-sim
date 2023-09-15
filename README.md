# isaac-sim

## 환경 설정

### 1 NVIDIA-SMI, Driver Version 535.54.03 / CUDA Version: 12.2
#### 1.1 Nvidia driver (version: 535-server)
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update  
sudo apt-get install nvidia-driver-535-server  
sudo reboot  
nvidia-smi  
```
#### 1.2 CUDA toolkit
- E: Unable to locate package nvidia-docker2 (아래 코드로 해결)
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt update
sudo apt -y install cuda

# install packages
sudo apt install nvidia-docker2
sudo apt install nvidia-container-toolkit
```

### 2 Anaconda python ver=3.10
<pre>
<code>
sudo apt install curl bzip2 -y  
curl --output anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2023.03-0-Linux-x86_64.sh  
sha256sum anaconda.sh  
bash anaconda.sh  
</code>
</pre>

### 3 Isaac Sim 2022.2.1 [link](https://www.nvidia.com/en-us/omniverse/download/#ov-download)
- E: AppImages require FUSE to run.
```
apt install fuse libfuse2
```

### 4 ROS2 humble [link](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html)
- have to run this code every time start ROS
```
source /opt/ros/humble/setup.bash
```

### 5 Docker [link](https://docs.docker.com/engine/install/ubuntu)
#### 5.1 Nvidia drivers for Docker
```
sudo apt install nvidia-container-toolkit
```
#### 5.2 Docker compose [link](https://docs.docker.com/compose/install/linux/#install-using-the-repository)
```
sudo apt install docker-compose-plugin
# verify
docker compose version
> Docker Compose version v2.21.0
```

### 6 Moveit
#### 6.1 Docker MoveIt2 설치 [link](https://moveit.picknik.ai/main/doc/how_to_guides/how_to_setup_docker_containers_in_ubuntu.html)
```
wget https://raw.githubusercontent.com/ros-planning/moveit2_tutorials/main/.docker/docker-compose.yml
DOCKER_IMAGE=rolling-tutorial docker compose run --rm --name moveit2_container gpu
```
- E: Failed to initialize NVML: Driver/library version mismatch > reboot


- enter the container through another terminal
```
docker exec -it moveit2_container /bin/bash
```

##### 6.1.1 moveit tutorial [link](https://github.com/ros-planning/moveit2_tutorials)

[getting started](https://moveit.picknik.ai/main/doc/tutorials/getting_started/getting_started.html)
```
source /opt/ros/humble/setup.bash
# same as link
```



# Errors
1. sudo apt update
```
W: https://nvidia.github.io/libnvidia-container/stable/ubuntu18.04/amd64/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
```

2. colcon build --mixin release
```
ModuleNotFoundError: No module named 'catkin_pkg'
CMake Error at /opt/ros/humble/share/ament_cmake_core/cmake/core/ament_package_xml.cmake:95 (message):
  execute_process(/home/ari/anaconda3/bin/python3.10
  /opt/ros/humble/share/ament_cmake_core/cmake/core/package_xml_2_cmake.py
  /home/ari/ws_moveit/src/moveit2/moveit_common/package.xml
  /home/ari/ws_moveit/build/moveit_common/ament_cmake_core/package.cmake)
  returned error code 1
Call Stack (most recent call first):
  /opt/ros/humble/share/ament_cmake_core/cmake/core/ament_package_xml.cmake:49 (_ament_package_xml)
  /opt/ros/humble/share/ament_lint_auto/cmake/ament_lint_auto_find_test_dependencies.cmake:31 (ament_package_xml)
  CMakeLists.txt:8 (ament_lint_auto_find_test_dependencies)
```
```
conda install -c auto catkin_pkg <failed
```
```
sudo cp -r /home/ari/anaconda3/envs/isaac/lib/python2.7/site-packages/catkin_pkg /opt/ros/humble/lib/python3.10/site-packages/ < failed
```

