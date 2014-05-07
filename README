ESCPOS
======

## Description

Python ESC/POS is a library which lets the user have access to all those printers handled by ESC/POS commands, as defined by Epson, from a Python application.

The standard usage is send raw text to the printer, but in also helps the user to enhance the experience with those printers by facilitating the bar code printing in many different standards,as well as manipulating images so they can be printed as brand logo or any other usage images migh have.

Text can be justified and fonts can be changed by size, type and weight.

Also, this module handles some hardware functionalities like, cut paper, cash drawer kicking, printer reset, carriage return and others concerned to the carriage alignment.

## Dependencies

In order to start getting access to your printer, you must ensure
you have previously installed the following python modules:

  * pyusb (python-usb)
  * PIL (Python Image Library)



------------------------------------------------------------------
## Define your printer

### USB printer

Before start creating your Python ESC/POS printer instance, you must see at your system for the printer parameters. This is done with the 'lsusb' command.

First run the command to look for the "Vendor ID" and "Product ID", then write down the values, these values are displayed just before the name of the device with the following format:

	xxxx:xxxx

Example:

	# lsusb
	Bus 002 Device 001: ID 04b8:0202 Epson ...

Write down the the values in question, then issue the following command so you can get the 	"Interface" number and "End Point"

	# lsusb -vvv -d xxxx:xxxx | grep iInterface
    	iInterface              0
	# lsusb -vvv -d xxxx:xxxx | grep bEndpointAddress | grep OUT
      	bEndpointAddress     0x01  EP 1 OUT
      	
The first command will yields the "Interface" number that must be handy to have and the second yields the "Output Endpoint" address.

#### USB Printer initialization

	Epson = printer.Usb(0x04b8,0x0202)

#### USB Printer initialization - custom

By default the "Interface" number is "0" and the "Output Endpoint" address is "0x01", if you 
have other values then you can define with your instance. So, assuming that we have another printer where in_ep is on 0x81 and out_ep=0x02, then the printer definition should looks like:

	Generic = printer.Usb(0x1a2b,0x1a2b,0,0x81,0x02)
	
### Network printer

You only need the IP of your printer, either because it is getting its IP by DHCP or you set it manually. Network Printer initialization

	Epson = printer.Network("192.168.1.99")
	
### Serial printer

Must of the default values set by the DIP switches for the serial printers, have been set as default on the serial printer class, so the only thing you need to know is which serial port the printer is hooked up. Serial printer initialization

	Epson = printer.Serial("/dev/tty0")

## Define your instance

The following example demonstrate how to initialize the Epson TM-TI88IV on USB interface

	from escpos import *
	""" Seiko Epson Corp. Receipt Printer M129 Definitions (EPSON TM-T88IV) """
	Epson = printer.Usb(0x04b8,0x0202)	
	# Print text
	Epson.text("Hello World\n")	
	# Print image
	Epson.image("logo.gif")	
	# Print QR Code
	Epson.qr("You can readme from your smartphone")
	# Print barcode
	Epson.barcode('1324354657687','EAN13',64,2,'','')
	# Cut paper
	Epson.cut()

## Links

Please visit project homepage at: <http://repo.bashlinux.com/projects/escpos.html>

Manuel F Martinez <manpaz@bashlinux.com>

