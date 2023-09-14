# isaac-sim

## 환경 설정

### NVIDIA-SMI, Driver Version 535.54.03 / CUDA Version: 12.2
####Nvidia driver (version: 535-server)
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update  
sudo apt-get install nvidia-driver-535-server  
sudo reboot  
nvidia-smi  
```
#### CUDA toolkit
- E: Unable to locate package nvidia-docker2 (아래 코드로 해결)
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt update
sudo apt -y install cuda
# install nvidia-docker2
sudo apt install nvidia-docker2
```
### Anaconda python ver=3.10
<pre>
<code>
sudo apt install curl bzip2 -y  
curl --output anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2023.03-0-Linux-x86_64.sh  
sha256sum anaconda.sh  
bash anaconda.sh  
</code>
</pre>
### Isaac Sim 2022.2.1
<https://www.nvidia.com/en-us/omniverse/download/#ov-download>
- E: AppImages require FUSE to run.
```
apt install fuse libfuse2
```
### Docker
#### Nvidia drivers for Docker

### Moveit
#### Docker MoveIt2 설치
