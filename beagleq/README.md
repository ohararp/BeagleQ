Introduction
------------
This is the beagleq client.

Install
-------
    cd /usr/share/bone101/
    git clone git://github.com/HouseOfBeck/BeagleQ

Wifi Setup  - Static IP
-----------------------
Detect USB Wifi adaptor

    iwconfig

Open the VI edit to update the network interface

    vi /etc/network/interfaces

Edit file to reflect the changes below

    auto wlan0
    iface wlan0 inet static
    address 192.168.1.166
    netmask 255.255.255.0
    gateway 192.168.1.1
      wpa-ssid "YOUR_SSID_HERE"
      wpa-psk  "YOUR_PASS_HERE"

Restart Network Interface
    
    /etc/init.d/networking restart

BeagleQ Setup
-------------

Edit beagle.js to reflect the same static IP that you set in the Wifi Setup

    vi beagleq/js/beagleq.js 
  
Scroll to Line ~86 and Update

    var host = '192.168.1.166';
    
Python - Start Server
---------------------

    python ./beagleq-server
    

View Live Html Page:
--------------------
From your host computer go to the Static IP address you set:

    http://your.beagle.address/beagleq/

If everything is working correctly you will see a connect message in the status pane.
Then temperatures will start appearing in the temperature pane and the gauges will 
indicate the temps. On the "chart" tab a plot will begin to appear.

The "test" tab is my play area. It will eventually go away.

The "about" tab will have the correct information for your beaglebone. The cape
eeprom data is static and not yet dynamic. It's on my list to fix.

Anyone with web frontend development skills is encouraged to help out.
In particular, I want to eliminate the google gauges in favor of something
like Highcharts so that the it can run without an internet connection.

Also, I need to add more tabs to tune the PID and manage output files.
