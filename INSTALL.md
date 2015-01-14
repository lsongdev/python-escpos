# Install ESCPOS

## Install dependencies

### Fedora
Fortunately everything is on Fedora repositories.

	yum install python-imaging pyserial pyusb python-qrcode

### Ubuntu

Ultimately, this instructions also apply to `Raspbian`, in case you are interested to install 
	`python-escpos` on your `Raspberry` with `Raspbian`.

Install the packages available on distro repositories.

	sudo apt-get install python-imaging python-serial

The packages which are not available at Ubuntu repositories need to be installed manually.

#### pyusb

  sudo pip install pyusb

#### python-qrcode

This is the python module to generate QR Codes

Checkout the latest code from github
Build and install it
	
	git clone https://github.com/lincolnloop/python-qrcode
	cd python-qrcode
	python setup.py build
	sudo python setup.py install

## System preparation
Get the Product ID and Vendor ID from the `lsusb` command

	lsusb
	> Bus 002 Device 001: ID 1a2b:1a2b Device name

Create a udev rule to let users belonging to dialout group use the printer. You can create the file `/etc/udev/rules.d/99-escpos.rules` and add the following:
 
	SUBSYSTEM=="usb", ATTRS{idVendor}=="1a2b", ATTRS{idProduct}=="1a2b", MODE="0664", GROUP="dialout"

Replace `idVendor` and `idProduct` hex numbers with the ones that you got from the previous step. Note that you can either, add yourself to "dialout" group, or use another group you already belongs instead "dialout" and set it in the `GROUP` parameter in the above rule.
Restart `udev` .
	
	sudo service udev restart

### Install

Checkout the code or download the latest compressed file of choice and decompress it
Change directory to python-escpos and install the package

	git clone https://github.com/song940/python-escpos.git
	cd python-escpos
	python setup.py build
	sudo python setup.py install

Enjoy !!!

And please, don't forget to ALWAYS add `Epson.cut()` at the end of your printing :)

Manuel F Martinez <manpaz@bashlinux.com>
