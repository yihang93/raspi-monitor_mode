# raspi-monitor_mode
This contains a text file that descibes the instructions for setting monitor mode on raspi3 b+ with TL-WN722N v3 WIFI adapter

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

1.Downloads the raspian system image from official website.
https://www.raspberrypi.org/downloads/raspbian/
The downloaded file name is like 2018-06-27-raspbian-stretch.zip

2.Use SD Card formatter to format the SD card and use the image burning tools like etcher to write it into the SD card.

3.Plug in the SD card to raspberry pi and switch on the pi. You will be asked for update && upgrade the system. Or you could
    
    ~$sudo apt-get update
    ~$sudo apt-get upgrade

4.Open the raspberry pi menu on left-top and open the SSH & VNC service in raspberry pi configuration.
Now you could use the SSH or VNC to get remote access to raspberry. Plug in the WIFI adapter. Then
    
    ~$sudo reboot

5.Install the dependencies below. And follow the steps.
    
    ~$sudo apt-get install bc git raspberrypi-kernel-headers aircrack-ng
    ~$sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/build
    ~$git clone https://github.com/quickreflex/rtl8188eus.git
    ~$cd rtl8188eus/
    ~$sudo ARCH=arm make
    ~$sudo make install
    ~$sudo reboot

6.Now you could use
    
    ~$iw list
    
You could see one of the phys has the mode of monitor mode. To use the monitor mode:
    
    ~$sudo airodump-ng wlan0 //the adapter that has the monitor mode
