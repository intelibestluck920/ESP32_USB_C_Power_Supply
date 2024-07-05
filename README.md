# ESP32 USB-C Power Supply

The idea for this ESP32 usb-c power supply project came to me when I discovered that components exist that communicate to parts inside usb-c wall chargers. These parts send out a request to the charger asking it to deliver specific voltage and current values if possible. Small chargers cannot deliver as much power as the larger ones. The small navigation button allows the user to select values with the top button as a power switch.

Hardware design instead of software is my strength so Larry Bank was kind enough to write the software. I've changed a few things around and damaged it so it is still work in progress.


To upload an Arduino sketch to the board it is connected to a pc using a USB-C cable but the output is only ever +5V. When the board is plugged into a dedicated usb-c charger like the 60 watt apple one that I use, multiple voltages and current options are available. Text on the back of your charger will let you know what values are available.

![wall_charger](https://user-images.githubusercontent.com/4991664/126163268-4a2f0e71-c4ee-4a5f-9668-6173583e491f.png)
![usbc](https://user-images.githubusercontent.com/4991664/126781378-7d5c2aa3-93dc-4e28-bfae-e14218958875.jpg)

A +5V LDO with a maximum input of 36V provides power to the CP2104N USB-C interface chip. Current consumption is so low for this part that and LDO will not get warm.

![5v](https://user-images.githubusercontent.com/4991664/126161071-a9722e82-cba1-44db-887f-395315d07b23.png)

Because the ESP32 current draw a few hundred milliamps, an earlier revision using an LCD was too hot when +15v and +20V was selected. (power=voltage x current) A small switching buck power supply with a maximum input of +40V now runs cool.

![3_3v](https://user-images.githubusercontent.com/4991664/126161122-873ebbfb-ac19-448a-b2a5-fcb4fcdd7969.png)

Measuring current draw at every voltage would be ideal so I've chosen the INA199 because at this time it is the only component that I can find in stock. Right now it's performance not good so I will try and find something better for the next revision.





