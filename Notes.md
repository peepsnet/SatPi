# Materals 
RPI3/4

SDR

Antenna

## Install steps

Install Raspian Lite
add ssh
add wpa_supplicant.conf
boot

ssh in

```
sudo apt-get update -y && sudo apt-get upgrade -y
sudo reboot
```

ssh in

## Install apt packages
```
sudo apt install -y git predict ntp cmake libusb-1.0 sox at bc libxft2 wxtoimg
```

## Run and agree to terms
```
wxtomig
```

## Edit with your values
Note: West is Negetive here
```
nano ~/.wxtoimgrc
```
```
Latitude: 26.07
Longitude: -80.21
Altitude: 15
```

## Fix Predict startup
For me this failed to run and was stuck in a loop
Here is the workaround I posted to the Repository: https://github.com/kd2bd/predict/issues/8
```
mkdir ~/.predict
cd ~/.predict
wget https://raw.githubusercontent.com/kd2bd/predict/master/default/predict.db
wget https://raw.githubusercontent.com/kd2bd/predict/master/default/predict.tle
wget https://raw.githubusercontent.com/kd2bd/predict/master/default/predict.qth
```

## Run Predict and edit Ground Station
Note: West is POSITIVE here!
```
predict
```

## Install this git
```
cd ~/
git clone https://github.com/peepsnet/SatPi.git
```

## install rtl-srd
```
cd ~
git clone https://github.com/keenerd/rtl-sdr.git
cd rtl-sdr/
mkdir build
cd build
cmake ../ -DINSTALL_UDEV_RULES=ON
make
sudo make install
sudo ldconfig
cd ~
sudo cp ./rtl-sdr/rtl-sdr.rules /etc/udev/rules.d/
sudo reboot
```
## If wxtoimg fails to install with apt
```
sudo apt install ~/SatPi/software/wxtoimg-armhf-2.11.2-beta.deb
```



## Other Comamnds I ran
sudo systemctl enable ssh
sudo systemctl start ssh
passwd
sudo passwd
sudo nano /etc/ssh/sshd_config
** add PermitRootLogin yes
/etc/init.d/ssh restart


## Other notes
Raspberry pi buster lite*
wxtoinmg https://wxtoimgrestored.xyz/
rtl_sdr https://github.com/rtlsdrblog/rtl-sdr
predict https://github.com/kd2bd/predict
sox apt install sox
at
bc
and others




Isntall notes from 
https://github.com/alonsovargas3/wx-ground-station
https://github.com/reynico/raspberry-noaa

Other info
https://github.com/martinber/noaa-apt
https://github.com/opensatelliteproject/OpenSatelliteProject
