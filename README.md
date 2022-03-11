# MomButton
A super simple emergency alert button for my mom to press if she falls, etc. ESP8266 Wemos D1 Mini + Wifi + IFTTT to send SMS messages

So my mom, like all moms, is getting on in years and her leg joints ain't what they used to be. She's had a couple falls where, thankfully nothing was broken and was only bruised, her knees and hips won't let her get up from the floor.  She's a boomer and so doesn't always have her phone with her and may not be within reach of a phone to call someone. After one fall where she was able to lasso a cordless phone off a desk with a random cord and call me to come pick her up off the floor, I had the thought of making some safety buttons that would text a number (or several numbers) of neighbors, myself, whomever, that she needed help with a single button press. 

Could be easily used for work alone situations (basement workshop or garage, etc) or other times where a simple push button alert needs to be sent.  Doesn't have to use SMS text messages.  Since it's IFTTT, any webhook action (email, tweet, etc) could be implemented easily.

Design goals were:
- Low power usage so battery life would be long
- Cheap enough to make up a bunch to spread around the house at floor level
- Small enough to tuck into corners and under cupboards out of the way unless you're on the floor
- Minimum of parts necessary
- Wifi Based
- No paid subscriptions needed
- Room for expansion and improvement


Parts List:
- 	~~1 X Wemos D1 Mini ESP8266 Wifi board
- 1 X Wemos D1 Mini PRO ESP8266 Wifi board (See Below note #1)
- 1 X Hammond 1591MSBK case
- 1 X Normally open push button switch
- 1 X LED and appropriate resistor
- 1 X 18650 battery
- 1 X 18650 battery holder
- Assorted Wire

If you want the Wemos D1 Mini removable:

- 1 X 2 hole short strip protoboard
- 2 X female headers for protoboard
- 2 x male headers for Wemos D1 Mini board


Notes:

- #1: Originally was using the Wemos D1 Mini but had no end of problems with standby current draw.  Turns out that the Mini has a standby of about 20ma in deep sleep, so it would suck a 18650 battery dry in a few days which was not optimal.  The Wemos D1 Mini **PRO** however is capable of much lower standby current in deep sleep (<1ma) and a much more appropriate battery life
- #2: My original design used a momentary switch to wake up the board which would then connect to wifi and execute the IFTTT webhook then go back to sleep.  Basically everything I want to do is done at boot on the board and then it goes to deep sleep till it's reset.  Turns out I'm an idiot.  There's no actual reason to keep the board powered in deep sleep all the time after it's executed or even before.  I could simply have it disconnected from power and use a locking on/off switch or a toggle switch to power the board up to start the alerts.  Since it's a safety device, this means battery life is nearly infinite and the added bonus of being able to modify the code to loop through a bunch of alert types until power was cut or even do things like sound a buzzer alert or something else battery intensive since we can be assured of power being available.
- #3: Moving the reset input from D0 to ground cut the deepsleep current from 15ma to <1ma.  Turns out that keeping the pin forcably low takes power and since we are resetting the board rather than waking it up, we can save power by just pulling RST straight to ground rather than a LOW GPIO pin.

To-Do features

- Battery level monitor (Via external LED display or sent with a message)
- LED indicator of webhook request recieved (reply 200)
- Add multiple recipients and alert methods to ensure someone responds quickly (neighbors, etc)
- Configuration via serial or web page instead of compiling in credentials 

Credits

- Heavily based on this tutorial: https://www.makeuseof.com/tag/wifi-connected-button-esp8266-tutorial/ by Ian Buckley
- Ian's full original code is available here: https://pastebin.com/mHr7yNYG
