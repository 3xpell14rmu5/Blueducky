# BlueDucky


CVE-2023-45866 - BlueDucky Implementation (Using DuckyScript)

Unauthenticated Peering Leading to Code Execution (Using HID Keyboard)

## Installation and Usage 

### Setup Instructions for Debian-based 

```bash
# update apt
sudo apt-get update
sudo apt-get -y upgrade

# install dependencies from apt
sudo apt install -y bluez-tools bluez-hcidump libbluetooth-dev \
sudo apt install -y git gcc python3-pip python3-setuptools \
sudo apt install -y python3-pydbus

# install pybluez from source
git clone https://github.com/pybluez/pybluez.git
cd pybluez
sudo python3 setup.py install

# build bdaddr from the bluez source
cd ~/
git clone --depth=1 https://github.com/bluez/bluez.git
gcc -o bdaddr ~/bluez/tools/bdaddr.c ~/bluez/src/oui.c -I ~/bluez -lbluetooth
sudo cp bdaddr /usr/local/bin/
```
### Setup Instructions for Arch-based 

```bash
# update pacman & packages
sudo pacman -Syyu

# install dependencies
# since arch doesn't separate lib packages: libbluetooth-dev included in bluez package
sudo pacman -S bluez-tools bluez-utils bluez-deprecated-tools \
               python-setuptools python-pydbus python-dbus
               git gcc python-pip \

# install pybluez from source
git clone https://github.com/pybluez/pybluez.git
cd pybluez
sudo python3 setup.py install

# build bdaddr from the bluez source
cd ~/
git clone --depth=1 https://github.com/bluez/bluez.git
gcc -o bdaddr ~/bluez/tools/bdaddr.c ~/bluez/src/oui.c -I ~/bluez -lbluetooth
sudo cp bdaddr /usr/local/bin/
```

## Running BlueDucky
```bash
git clone https://github.com/pentestfunctions/BlueDucky.git
cd BlueDucky
pip3 install -r requirements.txt
sudo hciconfig hci0 up
python3 BlueDucky.py
```








