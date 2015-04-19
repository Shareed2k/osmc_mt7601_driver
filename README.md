# OSMC
## mt7601 driver, kernel 3.18.10-1-osmc

**This is how I built and installed it.** 

Install compiler and make tools.
Do this from a root terminal or add sudo infront of commands

	sudo apt-get update
	sudo apt-get upgrade
	sudo apt-get install gcc make build-essential

Get the driver source. from [porjo git repository](https://github.com/porjo/mt7601 "") with patch for stability and performance on recent kernel versions


    git clone https://github.com/porjo/mt7601.git
    cd mt7601/
    
Get kernel sources - needed to build the driver


you can download compiled driver for kernel 3.18.10 here




