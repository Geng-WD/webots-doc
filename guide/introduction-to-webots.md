## Introduction to Webots

### What is Webots?

Webots is a professional mobile robot simulation software package. It offers a
rapid prototyping environment, that allows the user to create 3D virtual worlds
with physics properties such as mass, joints, friction coefficients, etc. The
user can add simple passive objects or active objects called mobile robots.
These robots can have different locomotion schemes (wheeled robots, legged
robots, or flying robots). Moreover, they may be equipped with a number of
sensor and actuator devices, such as distance sensors, drive wheels, cameras,
motors, touch sensors, emitters, receivers, etc. Finally, the user can program
each robot individually to exhibit the desired behavior. Webots contains a large
number of robot models and controller program examples to help users get
started.

Webots also contains a number of interfaces to real mobile robots, so that once
your simulated robot behaves as expected, you can transfer its control program
to a real robot like e-puck, DARwIn-OP, Nao, etc. Adding new interfaces is
possible through the related sytem.

### What can I do with Webots?

Webots is well suited for research and educational projects related to mobile
robotics. Many mobile robotics projects have relied on Webots for years in the
following areas:

### What do I need to know to use Webots?

You will need a minimal amount of technical knowledge to develop your own
simulations:

### Webots simulation

A Webots simulation is composed of following items:

### What is a world?

A world, in Webots, is a 3D description of the properties of robots and of their
environment. It contains a description of every object: position, orientation,
geometry, appearance (like color or brightness), physical properties, type of
object, etc. Worlds are organized as hierarchical structures where objects can
contain other objects (like in VRML97). For example, a robot can contain two
wheels, a distance sensor and a joint which itself contains a camera, etc. A
world file doesn't contain the controller code of the robots; it only specifies
the name of the controller that is required for each robot. Worlds are saved in
".wbt" files. The ".wbt" files are stored in the "worlds" subdirectory of each
Webots project.

### What is a controller?

A controller is a computer program that controls a robot specified in a world
file. Controllers can be written in any of the programming languages supported
by Webots: C, C++, Java, Python or `MATLAB`. When a simulation starts, Webots
launches the specified controllers, each as a separate process, and it
associates the controller processes with the simulated robots. Note that several
robots can use the same controller code, however a distinct process will be
launched for each robot.

Some programming languages need to be compiled (C and C++) other languages need
to be interpreted (Python and `MATLAB`) and some need to be both compiled and
interpreted (Java). For example, C and C++ controllers are compiled to platform-
dependent binary executables (for example ".exe" under Windows). Python and
`MATLAB` controllers are interpreted by the corresponding run-time systems
(which must be installed). Java controller need to be compiled to byte code
(".class" files or ".jar") and then interpreted by a Java Virtual Machine.

The source files and binary files of each controller are stored together in a
controller directory. A controller directory is placed in the "controllers"
subdirectory of each Webots project.

### What is a Supervisor?

The Supervisor is a privileged type of Robot that can execute operations that
can normally only be carried out by a human operator and not by a real robot.
The Supervisor is normally associated with a controller program that can also be
written in any of the above mentioned programming languages. However in contrast
with a regular Robot controller, the Supervisor controller will have access to
privileged operations. The privileged operations include simulation control, for
example, moving the robots to a random position, making a video capture of the
simulation, etc.
