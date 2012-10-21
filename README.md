## Abyss

A classic fall game (remember that TI-83 game?) using WebGL. The player controls the falling object with their webcam by facial detection.

I started with the facial detection because I wasn't sure it could be done. I'm using WebRTC to pipe the webcam data to a <video> tag, and got lucky finding a pretty good JavaScript library to analyze the data. This gives me x, y, width, and height coordinates for the detected face, and I do some quick math to determine which way the player is leaning.

The two things that tripped me up this weekend were terrain generation and collision detection. I ended up storing all of the platforms in an object, indexed by the level they were on. This way, I could only perform collision detection on the immediate vicinity of the player, and rip passed platforms out of memory (and not render them). The original collision detection algorithm was pretty chunky, and after some console.log debugging I determined that the facial recognition was taking up too much CPU time per frame. If I come back to this project, I'll probably split the facial recognition into a Web Worker.

Disclaimer: this code is super shitty

![](http://i.imgur.com/E8RS3.png)
![](http://i.imgur.com/BvczF.png)
![](http://i.imgur.com/GNDQr.png)
![](http://i.imgur.com/PF5tm.png)
