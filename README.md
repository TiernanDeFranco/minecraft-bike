# ⛏️ Playing Minecraft with a Bike 🚲
Originally coded 3/28/2021 at age 16, I used the Titan Two hardware to run GPC code which converted gyro movement of bike wheel and button inputs on handlebars, also used reWASD and a third joycon for steering.

Showcased in the video below, the actual coding portion is small and the video is mainly me actually playing Minecraft with the bike controller, and the beginning is construction a wooden mount to hold my non-stationary bike to make it stationary. But from ~2:40-5:00 I explain how I actally coded it.


But the main process involves writing GPC code which takes in inputs from the Nintendo Joycons and maps the buttons to the inventory, jump, break/place functions of the game, as well as calculating movement from the gyroscopic movement of a second joycon attached to the back wheel. The process to do this was relativley simple once I figured it out
(I guess most things are simpler after you solve them right?) But what I did was, in testing I would look at the  X-Acceleration reading (since each orientation had a distinct value) and recorded what the values were when the joycon was above the center of the wheel, and then what it was when below the center of the wheel.

[Watch the Video](https://youtu.be/JSyzb4syyXo?t=2m40s)


What I did was when there was a reading on the bottom, add 1 to a variable called bottom, then, I tested if the reading was at the top, and if bottom was ALSO greater than top, (so meaning it was at the bottom (bottom = 1), and is now at the top (top = 0) add 1 to top.

I also had a running timer which made sure that if it had been more than 1 second since bottom changed, at the time of top changing, set them both back to 0 and reset the timer.

This meant that the only way for bottom and top to reach 3 or higher (the threshold I set to allow the output of a keypress of W (forward movement), was if the bike wheel was moving fast enough for the threshold to be met before the timer was up. If you kept this constant speed, the timer resetting the top and bottom values doesn't affect you since, almost
immediatley, the values would reach the threshold again.


