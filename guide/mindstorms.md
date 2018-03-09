## Lego's Mindstorms

%figure "Mindstorms model in Webots"

![model.png](images/robots/mindstorms/model.png)

%end

Robot models based on [Lego's Mindstorms](https://www.lego.com/en-us/mindstorms) can be created in Webots.

### Samples

You will find the following sample in this folder: "WEBOTS\_HOME/projects/robots/lego/mindstorms/worlds".

#### rover.wbt

![rover.wbt.png](images/robots/mindstorms/rover.wbt.png) In this example you can see the Mindstorms Rover robot following a black line drawn on the ground.
In the middle of this line there is an obstacle which the robot navigates around after detecting a collision with it.
The robot will then recover its path.
As this robot is a *Mindstorms* robot, its world file and its controller are in the "mindstorms" directory.
This example is written both in Java and C, as a reference for translating Webots code from one language to another.
The source code for this controller is in the "Rover" directory.