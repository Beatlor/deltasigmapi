Delta Sigma Pi Version 2
=======
Demo code for the Delta Sigma Pi version 2 board from http://www.abelectronics.co.uk

Delta Sigma Pi files for leveraging your Delta Sigma device on your Raspberry Pi

## Getting Started
Update system and install python, git and the smbus functionality
```
sudo apt-get update && apt-get upgrade
sudo apt-get install python git i2c-tools python-smbus
```
Edit your /etc/modules file adding 
```
sudo nano /etc/modules
```
Add
```
i2c-bcm2708 
i2c-dev
```

Edit /etc/modprobe.d/raspi-blacklist.conf
```
sudo nano /etc/modprobe.d/raspi-blacklist.conf
```
comment out

```
blacklist spi-bcm2708
blacklist i2c-bcm2708
```

it should now read

```
#blacklist spi-bcm2708
#blacklist i2c-bcm2708
```
Now lets test connectivity

```
modprobe i2c-dev
i2cdetect -y 1
```

you should see some numbers somewhere, it will look something like this
```     
0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- --
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
60: -- -- -- -- -- -- -- -- 68 69 -- -- -- -- -- --
70: -- -- -- -- -- -- -- --
```

Get the python scripts
```
git clone git://github.com/abelectronicsuk/deltasigmapi.git
cd deltasigmapi
```

Get the reading from the board
```
sudo python deltasigmapismbus.py
```
=======
Code demos are available in Python 2.7 / 2.8
Old quick2wire demos have been removed as the quick2wire lib appears to be no longer maintained. 

Requries Python 2.7
Requires SMBus 

install SMBus with:
	sudo apt-get install python-smbus

dspilogger.py - Samples at 18bit rate and saves to a text file with timestamp

dspi12.py - Samples at 12bit rate and outputs to console/terminal
dspi16.py - Samples at 16bit rate and outputs to console/terminal
dspi18.py - Samples at 18bit rate and outputs to console/terminal