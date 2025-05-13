# Ubuntu

### Add a Figlet
```bash
sudo apt install figlet
sudo apt install ruby-full -y
sudo apt install lolcat
sudo apt install vim
```
Add to ~/.bashrc
```bash
figlet SHUBH | lolcat --seed 105
```

### Get IP address visibile to outside world
```bash
curl ifconfig.me
```

### Kubectl-ai  
- Gemini 2.5 Pro Experimental
```bash
kubectl-ai --model gemini-2.5-pro-exp-03-25
```
- Gemini-2.5-flash-preview
```bash
kubectl-ai --model gemini-2.5-flash-preview-04-17
```
### Remove/Disable Swap
```bash
swapon --show
sudo swapoff /swap.img
sudo vi /etc/fstab
# comment the swap file line
```
