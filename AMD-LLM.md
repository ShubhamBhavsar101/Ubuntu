
# Driver Setup for AMD Graphics card on Linux

Reference - [Running LLMs Locally on AMD GPUs with Ollama](https://www.amd.com/en/developer/resources/technical-articles/running-llms-locally-on-amd-gpus-with-ollama.html)

## #Installing Rocm 
```bash
sudo apt update
wget https://repo.radeon.com/amdgpu-install/6.3.4/ubuntu/noble/amdgpu-install_6.3.60304-1_all.deb
sudo apt install ./amdgpu-install_6.3.60304-1_all.deb -y
```

```bash
amdgpu-install -y --usecase=graphics,rocm
```

### Add user to render and video groups
```bash
groups
```
```bash
sudo usermod -a -G render,video $LOGNAME
```

### Reboot
```bash
sudo reboot
```
---
### Ollama Optimisation
Reference - [Performance Optimisation Guide for AMD Unsupported GPU](https://www.conroyp.com/articles/running-ollama-ubuntu-unsupported-amd-gpu-performance-guide)  

Edit the Ollama service file
```bash
sudo vi /etc/systemd/system/ollama.service
```
Swap the Environment variable
```bash
Environment="HSA_OVERRIDE_GFX_VERSION=10.3.0"
```
Restart ollama
```bash
sudo systemctl daemon-reload && sudo systemctl restart ollama.service
```
Run Ollama model and check GPU usage in radeontop
```bash
sudo apt install radeontop
radeontop
```
If this does not work, try exporting HSA_OVERRIDE_GFX_VERSION=10.3.0 in .bashrc file
```bash
export HSA_OVERRIDE_GFX_VERSION="10.3.0"
```
---
### Use OpenWebUI
```bash
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```
