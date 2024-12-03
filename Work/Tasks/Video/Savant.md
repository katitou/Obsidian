нужно установить savant. в документации написано we provide the instruction on how to configure Ubuntu 22.04 runtime. If you use another operation system, adapt the instructions to your OS. мне нужно установить на linux manajaro gnome, можешь помочь исправить команды?

Update Packages and Install Basic Tools
sudo apt-get update
sudo apt-get install -y git git-lfs curl -y

Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

Install Nvidia Drivers
sudo apt install --no-install-recommends nvidia-driver-535
sudo reboot

Install Nvidia Container Toolkit
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

sudo apt-get update
sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker