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
- 1 X Wemos D1 Mini ESP8266 Wifi board
- 1 X Hammond 1591MSBK case
- 1 X Normally open push button switch
- 1 X LED and appropriate resistor
- 1 X 18650 battery
- 1 X 18650 battery holder

If you want the Wemos D1 Mini removable:

- 1 X 2 hole short strip protoboard
- 2 X female headers for protoboard
- 2 x male headers for Wemos D1 Mini board
