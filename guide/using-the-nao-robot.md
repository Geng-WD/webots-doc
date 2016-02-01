## Using the Nao robot

### Introduction

The Nao robot is a humanoid robot developed by `Aldebaran Robotics`. This
section explains how to use Nao robot simulated in Webots together with the
Choregraphe program of `Aldebaran Robotics`. Currently Webots supports the Nao
v3.3, v4.0 and v5.0 versions, with and without their articulated fingers
(respectively with 25 and 21 degrees of freedom) for the first two.

The Webots installation includes several world files with Nao robots. You will
find some in this folder:
"WEBOTS_MODULES_PATH/projects/robots/aldebaran/worlds". The "nao.wbt" and
"nao_indoors.wbt" are meant to be used with Choregraphe (see below). The
"nao_demo.wbt" is a demonstration of a very simple controller that uses Webots C
API instead of Choregraphe. The "nao_matlab.wbt" world is an example of
programming Webots using the Matlab API. The "nao_robocup.wbt" world is an
example of how to use the NAOqi API inside Webots. It is the same API that is
used in Choregraphe, meaning that you can program Nao inside Webots without
using Choregraphe if you want to. In this world, Nao tries to shoot the ball in
the goal. You can find another NAOqi example in the
"WEBOTS_MODULES_PATH/projects/contests/nao_challenge/2013-2014/worlds" folder.
The "challenge.wbt" file in this folder is a solution to the NAO Challenge
contest (edition 2013-2014).

In addition Nao robots are also used in the world files of the `Robotstadium`
contest. These files are located in this folder:
"WEBOTS_MODULES_PATH/projects/contests/robotstadium/worlds".

### Using Webots with Choregraphe

These instructions have been tested with Webots 8.0.0 and Choregraphe 2.1.1.10.
Please note that Webots must not be launched as root when using any world
containing naoqisim, otherwise Choregraphe won't be able to send instructions to
the robot in Webots.

Start Webots and open this world file:
"WEBOTS_MODULES_PATH/projects/robots/aldebaran/worlds/nao.wbt" You should see a
red Nao in an empty environment. If the simulation is paused, then please start
it by pushing the `Real-time` button in Webots.

The camera images in Webots (small purple viewports) should reflect what the
robot sees.

Several lines of text information corresponding to the output of NAOqi should be
printed to Webots console.

Now you can start Choregraphe with the --no-naoqi option. Please make sure the
Choregraphe version matches the NAOqi version printed in Webots console. In
Choregraphe choose the menu `Connection > Connect to...`. Then in the list,
select the NAOqi that was started by Webots, on you local machine, it will have
the port number 9559, unless you change it. Note that the NAOqi will not appear
in the list if the simulation was not started in Webots. If the simulation was
started but the robot still doesn't appear in the list, force the IP and port to
127.0.0.1 and 9559 in Choregraphe and then press connect.

At this point a Nao model matching the Webots model should appear in
Choregraphe. Now, in Choregraphe toggle the "Wake up" button, which is a little
sun in the rop right of the window. Nao is currently in the "Stand Zero" pose,
you can change its starting pose using the posture library in Choregraphe.

Then double-click on any of the Nao parts in Choregraphe: a small window with
control sliders appears. Now, move any of the sliders: the motor movement in
Choregraphe should be reflected in the Webots simulation. If you open the Video
monitor in Choregraphe you should see the picture of the Nao camera simulated by
Webots.

### Nao models

You can switch between the Nao model thanks to the following Nao PROTO fields:

### Using motion boxes

Now we can test some of the motion boxes of Choregraphe. A simple example is a
sit down -> stand up motion. In Choregraphe, select the "Sit Down" and "Stand
Up" boxes from `Box libraries > default`. Drag and drop them in central view.
Then connect the global "onStart" input to the "Sit Down" box's "onStart" input,
and the output of this box to the "Stand Up" box's "onStart" input. Now make
sure the simulation is running, and, push the `Play` button in Choregraphe. This
will make the robot sit down, and then stand up once he is done sitting down.

### Using the cameras

Webots simulates Nao's top and bottom cameras. Using Aldebaran's Choregraphe or
the Monitor programs, it is possible to switch between these cameras. In
Choregraphe, use the "Select Camera" box in `Box Library > Vision`. The
simulated camera image can be viewed in Choregraphe: `View > Video monitor`. The
resolution of the image capture can be changed in Webots using the `cameraWidth`
and `cameraHeight` fields of the robot. Note that the simulation speed decreases
as the resolution increases. It is possible to hide the camera viewports (purple
frame) in Webots, by setting the `cameraPixelSize` field to 0. It is also
possible to completely switch off the simulation of the cameras by adding the
"-nocam" option before the NAOqi port number in the `controllerArgs` field, e.g.
"-nocam 9559".

### Using Several Nao robots

It is possible to have several Nao robots in your simulation, however each Nao
robot must use a different NAOqi port. Here how to copy a Nao and assign the
NAOqi port number:

Repeat the above procedure for each additional robot that you need. Remember
that every robot must have a different port number specified in
`controllerArgs`.

### Getting the right speed for realistic simulation

Choregraphe uses exclusively real-time and so the robot's motions are meant to
be carried out in real-time. The Webots simulator uses a virtual time base that
can be faster or slower than real-time, depending on the CPU and GPU power of
the host computer. If the CPU and GPU are powerful enough, Webots can keep up
with real-time, in this case the speed indicator in Webots shows approximately
1.0x, otherwise the speed indicator goes below 1.0x. Choregraphe motions will
play accurately only if Webots simulation speed is around 1.0x. When Webots
simulation speed drifts away from 1.0x, the physics simulation gets wrong
(unnatural) and thus Choregraphe motions don't work as expected any more. For
example if Webots indicates 0.5x, this means that it is only able to simulate at
half real-time the motion provided by Choregraphe: the physics simulation is too
slow. Therefore it is important to keep the simulation speed as much as possible
close to 1.0x. There are currently no means of synchronizing Webots and
Choregraphe, but this problem will be addressed in a future release. It is often
possible to prevent the simulation speed from going below 1.0x, by keeping the
CPU and GPU load as low as possible. There are several ways to do that, here are
the most effective ones:

### Known Problems

If for some unexpected reason Webots crashes, it is possible that the `hal` or
`naoqi-bin` processes remain active in memory. In this case we recommend you to
terminate these processes manually before restarting Webots.

On Windows, use the Task Manager (the Task Manager can be started by pressing
Ctrl-Alt-Delete): In the Task Manager select the `Processes` tab, then select
each `hal.exe` and `naoqi-bin.exe` line and push the "End Process" button for
each one.

On Linux, you can use the `killall` or the `pkill` commands, e.g.: `$ killall
hal naoqi-bin`
