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
#### 6.1 Docker MoveIt2 설치
```
wget https://raw.githubusercontent.com/ros-planning/moveit2_tutorials/main/.docker/docker-compose.yml
DOCKER_IMAGE=rolling-tutorial docker compose run --rm --name moveit2_container gpu
```
```
# If you wish to enter the container through another terminal, use
docker exec -it moveit2_container /bin/bash
```




# Errors
1. sudo apt update
```
W: https://nvidia.github.io/libnvidia-container/stable/ubuntu18.04/amd64/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
```




