# OSMC
## mt7601 driver, kernel 3.18.10-1-osmc

**This is how I built and installed it.** 

Install compiler and make tools.
Do this from a root terminal or add sudo infront of commands

	sudo apt-get update
	sudo apt-get upgrade
	sudo apt-get install gcc make build-essential
	
Get kernel headers,
after install you can find it in /usr/src/rbp2-headers-3.18.10-1-osmc

	dpkg -i rbp2-headers-3.18.10-1-osmc_1_armhf.deb

Get the driver source. from [porjo git repository](https://github.com/porjo/mt7601 "") with patch for stability and performance on recent kernel versions


    git clone https://github.com/porjo/mt7601.git
    
Get kernel sources - needed to build the driver

	tar -xvjpf rbp2-source-3.18.10-1-osmc.tar.bz2
	sudo ln -s /home/osmc/rbp2-source-3.18.10-1-osmc/ /lib/modules/3.18.10-1-osmc/build
	
Prepare the kernel/module sources so the driver can build with them.

	cd rbp2-source-3.18.10-1-osmc/
	sudo make mrproper
	cat /boot/config-3.18.10-1-osmc > .config
	cp .config .config.org
	sudo make modules_prepare
	cp /usr/src/rbp2-headers-3.18.10-1-osmc/Module.symvers ./

Build the driver. You will see a lot of warnings just ignore them.	

	cd mt7601-master/src
	sudo make

Install the driver. You should read the 
	
	README_STA_usb
	
in the MODULE folder for config info in the RT2870STA.dat.

	mkdir -p /etc/Wireless/RT2870STA
	sudo cp RT2870STA.dat /etc/Wireless/RT2870STA
	sudo cp os/linux/mt7601Usta.ko /lib/modules/3.18.10-1-osmc/kernel/drivers/net/wireless/
	
Now reboot with the dongle inserted in a USB port.
If you do an ifconfig -a you should see ra0 as a network device.
Now you have the driver you need to config the wireless networking


you can download compiled driver for kernel 3.18.10 here




