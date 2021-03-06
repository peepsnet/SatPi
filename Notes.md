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
## Get your lat/long
https://www.latlong.net/

## Edit with your values
Note: West is Negetive here
```
nano ~/.wxtoimgrc
```
```
Latitude: 26.129299
Longitude: -80.359912
Altitude: 4
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
## Run Predict and edit Ground Station [G]
Note: West is POSITIVE here!
```
predict
```

## Update Predict TLEs
Although not needed I did it anyway so I could use the GUI.
https://celestrak.com/NORAD/elements/
```
wget https://celestrak.com/NORAD/elements/noaa.txt -O predict.tle
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
##  Install Apache + MySQL + PHP7.4 (LAMP Server)
```
sudo apt install apache2 -y
sudo apt install php7.3 libapache2-mod-php7.3 php7.3-mysql php7.3-cli php7.3-common -y
sudo apt install mariadb-server php-mysql -y
```
## Restart Apache2
```
sudo service apache2 restart

```


## Other Comamnds I ran
```
sudo systemctl enable ssh
sudo systemctl start ssh
passwd
sudo passwd
sudo nano /etc/ssh/sshd_config
** add PermitRootLogin yes
/etc/init.d/ssh restart
sudo apt install phpmyadmin -y
webmin for Debian: http://www.webmin.com/deb.html


echo "Installation de Kalibrate"
sudo apt install build-essential libtool automake autoconf librtlsdr-dev libfftw3-dev
git clone https://github.com/steve-m/kalibrate-rtl
cd kalibrate-rtl
./bootstrap && CXXFLAGS='-W -Wall -O3'
./configure
```
### I modified /usr/local/lib/pkgconfig/librtlsdr.pc to the following to find the missing references:
```
prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
includedir=${prefix}/include
```
```
./bootstrap && CXXFLAGS='-W -Wall -O3'
./configure
make
sudo make install
```

### Installed a Directry Lister from https://www.directorylister.com/

```
cd /var/www/html/wx
wget https://github.com/DirectoryLister/DirectoryLister/releases/download/3.0.5/DirectoryLister-3.0.5.zip
unzip DirectoryLister-3.0.5.zip
sudo apt install php7.3-xml
```
### Installed Image Galery https://files.photo.gallery/
```
sudo apt -y install php7.3-gd php-mbstring
cd /var/www/html/wx/image
wget https://cdn.jsdelivr.net/npm/files.photo.gallery/index.php
mkdir /var/www/html/wx/image/_files
mkdir /var/www/html/wx/image/_files/cache
/var/www/html/wx/image/_files/cache/files
sudo chown -R www-data:www-data /var/www/html/wx/image/_files
sudo service apache2 restart
```

## Other notes
* Raspberry pi buster lite*
* wxtoinmg https://wxtoimgrestored.xyz/
* rtl_sdr https://github.com/rtlsdrblog/rtl-sdr
* predict https://github.com/kd2bd/predict
* sox apt install sox
 *at
* bc
* and others




Isntall notes from 
* https://github.com/alonsovargas3/wx-ground-station
* https://github.com/reynico/raspberry-noaa
* https://gist.github.com/iNem0o/6346423
* https://github.com/steve-m/kalibrate-rtl/wiki/How-to-install
* https://github.com/steve-m/kalibrate-rtl/issues/19

Other info
* https://github.com/martinber/noaa-apt
* https://github.com/opensatelliteproject/OpenSatelliteProject
* http://kmkeen.com/rtl-demod-guide/2013-01-02-17-54-37-499.html
* https://www.unix.com/man-page/debian/1/predict/
* http://alloutput.com/amateur-radio/wxsat-reception/
* https://unix.stackexchange.com/questions/21089/how-to-use-command-line-to-change-volume
* 
