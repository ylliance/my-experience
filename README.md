# Asterisk/FreePBX
# Development
## Python
### Create virtual working environment
- In ubuntu:
```
python -m venv ttt --clear
source ttt/bin/activate
python3 -m pip install --upgrade pip
pip list
pip install torch
```
- On windows:
```
mkdir d:/test
cd test
python -m venv test 
cd test
Scripts\activate.bat
pip list
```
### How to download current python packages
```
pip freeze > requirements.txt
pip download -r requirements.txt
```
# Tools
## npm is not working in Windows after installed nodejs
<img src="images/npm-not-working-in-windows.png" alt="drawing" width="800px"/>

In powershell, I entered this:
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
# Linux
## When Ubuntu VPS
### How to access VPS by web http
- Install & Start cockpit
```
apt update
apt upgrade
apt install cockpit -y
systemctl enable --now cockpit
systemctl start cockpit
```
- Set firewall
```
ufw allow 9090/tcp
ufw allow 9090/udp
ufw reload
```

### How to manage virtual machines
```
apt install -y libvirt-daemon-system libvirt-clients qemu-kvm virt-manager bridge-utils cockpit-machines
```

### Port forwarding(How to ssh-connect to VPS's VM)
- VPS's IP: 65.21.136.38
- VPS's VM's IP: 192.168.122.122
- In VPS:
```shell
iptables -t nat -I PREROUTING -p tcp --dport 2222 -j DNAT --to-destination 192.168.122.122:22
iptables -I FORWARD -p tcp -d 192.168.122.122 --dport 22 -j ACCEPT
systemctl restart ufw
```
- To ssh-connect to VM
```
ssh -p 2222 root@65.21.136.38
```
# Artificial Intelligence
