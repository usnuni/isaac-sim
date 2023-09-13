# isaac-sim

## 환경 설정

### NVIDIA-SMI, Driver Version 535.54.03 / CUDA Version: 12.2

```
sudo add-apt-repository ppa:graphics-drivers/ppa  sudo apt update  
sudo apt-get install nvidia-driver-버전(535-server)  
sudo reboot  
nvidia-smi  
```

### Anaconda python ver=3.10

```
sudo apt install curl bzip2 -y  
curl --output anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2023.03-0-Linux-x86_64.sh  
sha256sum anaconda.sh  
bash anaconda.sh  
```

### Isaac Sim 2022.2.1
<https://www.nvidia.com/en-us/omniverse/download/#ov-download>

- Error: AppImages require FUSE to run.
```
apt install fuse libfuse2
```

