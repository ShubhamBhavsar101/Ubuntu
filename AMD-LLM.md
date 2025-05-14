# Driver Setup for AMD Graphics card on Linux

Reference - [Running LLMs Locally on AMD GPUs with Ollama](https://www.amd.com/en/developer/resources/technical-articles/running-llms-locally-on-amd-gpus-with-ollama.html)

## Installing Rocm 
```bash
sudo apt update
wget https://repo.radeon.com/amdgpu-install/6.3.4/ubuntu/noble/amdgpu-install_6.3.60304-1_all.deb
sudo apt install ./amdgpu-install_6.3.60304-1_all.deb -y
```

```bash
amdgpu-install -y --usecase=graphics,rocm
```

```bash
sudo reboot
```
