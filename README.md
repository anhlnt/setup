# Ubuntu 22.04

## Preparation
```bash
sudo apt update
sudo apt upgrade
```

## Install CUDA and Nvidia driver
https://developer.nvidia.com/cuda-toolkit-archive

CUDA version: 11.7.1
```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.7.1/local_installers/cuda-repo-ubuntu2204-11-7-local_11.7.1-515.65.01-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2204-11-7-local_11.7.1-515.65.01-1_amd64.deb
sudo cp /var/cuda-repo-ubuntu2204-11-7-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda
```

## Install cuDNN
[Log in](https://developer.nvidia.com/cudnn) and download cuDNN packages.

Example
```bash
sudo apt-get install libcudnn8-samples=8.6.0.163-1+cuda11.8 
sudo cp /var/cudnn-local-repo-ubuntu2204-8.6.0.163/cudnn-local-FAED14DD-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get install libcudnn8=8.6.0.163-1+cuda11.8 
sudo apt-get install libcudnn8-dev=8.6.0.163-1+cuda11.8 
sudo apt-get install libcudnn8-samples=8.6.0.163-1+cuda11.8 
```
https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html

Test

```bash
sudo apt-get -y install libfreeimage3 libfreeimage-dev
cd /usr/src/cudnn_samples_v8/mnistCUDNN
sudo make
./mnistCUDNN
```

## Install git, cmake, curl, vim
```bash
sudo apt -y update
sudo apt -y install git cmake cmake-curses-gui cmake-gui curl vim
```

## Install python
```bash
sudo apt -y update
sudo apt -y install python-is-python3 python3-dev python-dev-is-python3 python3-pip python3-setuptools python3-venv build-essential
```

## Install pyenv, pyenv-virtualenv
```bash
sudo apt update
sudo apt -y install --no-install-recommends make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

curl https://pyenv.run | bash
echo 'export PYENV_ROOT="$HOME/.pyenv"
command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
source ~/.zshrc
```

## Install python via pyenv
```bash
pyenv install 3.9.15
pyenv global 3.9.15
```

## Install tensorflow, pytorch
```bash
pip install tensorflow
pip install torch torchvision torchaudio
```

## Setting SSH
```bash
sudo apt -y update
sudo apt -y install openssh-server
```
https://www.kkaneko.jp/tools/server/pubkey.html

## Install Docker
```bash
sudo apt-get update
sudo apt-get -y install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
https://docs.docker.com/engine/install/ubuntu/#install-docker-engine

### Run the Docker daemon as a non-root user
```bash
sudo usermod -aG docker $USER
sudo reboot
```

## Install Chrome
```bash
cd ~/Downloads/
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Uninstall 
### CUDA uninstall
```bash
sudo apt-get --purge remove nvidia*
sudo apt-get --purge remove cuda*
sudo apt-get --purge remove cudnn*
sudo apt-get --purge remove libnvidia*
sudo apt-get --purge remove libcuda*
sudo apt-get --purge remove libcudnn*
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
sudo rm -rf /usr/local/cuda*
```
