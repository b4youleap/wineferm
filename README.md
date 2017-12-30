# Wine Fermentation Chamber Project
This project turns a seldom used kegerator into a wine fermentation chamber! I will progressively improve this project from a minimum viable product (MVP) stage through to something hopefully fairly elegant and resilient.

### Motivation
I needed a controlled environment for the fermentation process. Living in Arizona doesn't always enable maintaining temperatures consistently for 2+ months. The wine kit instructions (for the Malbec I'm making now) say it is critical to maintain temperatures between 22-24 degrees Centigrade (72-75 degree Fahrenheit).

### Approach
Initial approach: Poll a temperature sensor once per minute and send an off or on signal to the remote outlet switch to either start up the kegerator or shut it down. 

### Assumptions
* Close enough is good enough: The instructions (for the Malbec) specify a temperature range of 22 - 24 degrees Celsius, and I assume the kegerator can maintain that enough of the time with the exceptions being during cooling cycles. The placement of the temperature sensor in the vertical middle in combination with the polling frequency will result in some over-cooling of the liquid but will not be detrimental to the fermentation process.
* The remote outlet switch will supply clean power (as clean as it gets from Arizona Public Service anyway) and not negatively impact the kegerator. Or to put it another way, the switching process will not introduce any unwanted power conditions to the kegerator such as phase interruptions or brownout conditions.

## Hardware
* Wine Kit: I'm using a Malbec kit from [winexpert.com](https://winexpert.com))
* Working kegerator - I have a Vissani from [Home Depot](https://www.homedepot.com/catalog/pdfImages/89/894db3fc-a2a8-4a2d-a149-49658eb58ddd.pdf)
* Winemaking equipment (bucket, carboy, thief, etc)
* Raspberry Pi
* 2-DHT11 sensors
* 433Mhz transmitter
* Etekcity ZAP 5LX Remote outlet switches

## References / Useful Links
* My brewing supply store: [What Ales Ya](http://whatalesya.com)
* Inspiration for remote control: [Tim Leland](https://timleland.com/wireless-power-outlets/)
* Raspberry Pi Zero W pinouts: [sparkfun](https://cdn.sparkfun.com/assets/learn_tutorials/6/7/6/PiZero_1.pdf)
* Sensor and electronics supplier: [adafruit](https://www.adafruit.com/)
* Data collection: [io.adafruit.com](https://io.adafruit.com/)

## Installation and Setup
Documentation and pictures coming soon.

## Initial Testing
Testing is an important part of every project, as had I not tested, I would not have known that I was NOT reading the sensor inside my infinite loop! I would have easily destroyed 6L of promising wine and wasted money. 
Note: You won't see any code testing here until later in the project, as I started writing this after my hacking started. I do think I will be adding additional sensors in the chamber (external to the fermenter) as well as a sensor for inside the fermenter. I may also be adding an external display (a paperwhite one would work wonderfully for power consumption!) and should also consider adding functionality to log the fermentation stage activities. So as I hack along there will be software tests (I'm still trying to adapt to test driven development) and those will be included as I go.

#### Temperature Fluctuation Tests
As the interior environment stabilizes and the primary fermenter (bucket) gets within range I expect longer periods of time at stable temperatures.
1. My first test was with a cup of boiling water and it made me realize that I end up with about a 4 degree overcooling. I set my cutoff at 22 and temps hit a low of 18 from the cooling cycle. The kegerator kicked on for 3 minutes before shutting off so I will adjust the code to look for < 24 so I can be closer to the range. 
My next test is to fill the primary fermenter with water to 6 liters, and place it in the kegerator with the lid and airlock as I will at the end of the first stage of production.  I suspect the difference of mass between a cup of water and 6 liters of water will give me different results but I will post them tomorrow (12/31)
