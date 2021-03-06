## K-Team's Khepera II

%robot khepera2 images/robots/khepera2/model.png

The "Khepera II" robot is a two-wheeled robot produced by [K-Team](https://www.k-team.com/mobile-robotics-products/old-products/khepera-ii).
It is mounted by multiple sensors including 8 distance sensors.

### Khepera2 PROTO

Derived from [Robot](../reference/robot.md).

```
Khepera2 {
  SFVec3f    translation     0 0 0
  SFRotation rotation        0 1 0 0
  SFString   name            "Khepera II"
  SFString   controller      "braitenberg"
  SFString   controllerArgs  ""
  SFString   customData      ""
  SFBool     synchronization TRUE
  MFNode     extensionSlot   []
}
```

> **File location**: "WEBOTS\_HOME/projects/robots/k-team/khepera2/protos/Khepera2.proto"

#### Khepera2 Field Summary

- `extensionSlot`: Extends the robot with new nodes in the extension slot.

### Samples

You will find the following sample in this folder: "WEBOTS\_HOME/projects/robots/k-team/khepera2/worlds":

#### khepera2.wbt

![khepera2.wbt.png](images/robots/khepera2/khepera2.wbt.png) In this example, you can see a Khepera II robot moving inside an arena while avoiding the walls.
