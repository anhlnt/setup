# Ubuntu 22.04

## Preparation
```bash
sudo apt update
sudo apt upgrade
```

## Install CUDA and Nvidia driver
https://developer.nvidia.com/cuda-downloads 
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
eval "$(pyenv virtualenv-init --path)"' >> ~/.zshrc
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

## Install Chrome
```bash
cd ~/Downloads/
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```
