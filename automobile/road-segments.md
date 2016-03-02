## Road segments

The first part of this section will present the various PROTOs of road segments
and intersections, that can be used to build the road network.

### Road

The `Road` PROTO is the most generic one. It can be used for a large variety of
purpose.

%figure "Generic segment of road"

![road.png](images/road.png)

%end

```
Road {
      SFVec3f    translation               0 0 0
      SFRotation rotation                  0 1 0 0
      SFFloat    width                     7
      SFInt32    numberOfLanes             2
      MFBool     dashedLine                TRUE
      SFFloat    roadBorderHeight          0.15
      MFFloat    roadBorderWidth           [ 0.8 ]
      SFBool     road                      TRUE
      SFBool     rightBorder               TRUE
      SFBool     leftBorder                TRUE
      SFBool     bottom                    FALSE
      SFBool     rightSide                 TRUE
      SFBool     leftSide                  TRUE
      MFVec3f    wayPoints                 [ 0 0 0, 0 0 1 ]
      MFFloat    roadTilt                  [ 0, 0]
      MFFloat    startingAngle             [ ]
      MFFloat    endingAngle               [ ]
      SFInt32    splineSubdivision         4
      MFString   texture                   "textures/road.jpg"
      SFFloat    textureScale              2
      MFString   pavementTexture           "textures/pavement.jpg"
      SFBool     locked                    TRUE
      SFBool     roadBoundingObject        FALSE
      SFBool     rightBorderBoundingObject FALSE
      SFBool     leftBorderBoundingObject  FALSE
      SFString   contactMaterial           "default"
  }
```

#### Road field Summary

- `width`: Defines the total with of the road (excluding sidewalk).
- `numberOfLanes`: Defines the number of lanes (used for the texture mapping).
- `dashedLine`: Defines for each line separating two lanes if it should be
continuous or dashed.
- `roadBorderHeight`: Defines the height of the sidewalk.
- `roadBorderWidth`: Defines the width of the sidewalk associated to each
way-point (if there is less value than way-points, the last value is used for
the last remaining way-points).
- `road`: Defines if the road should be present or not (useful in case you only
need the sidewalk).
- `rightBorder`: Defines if the road should have a right sidewalk.
- `leftBorder`: Defines if the road should have a left sidewalk.
- `bottom`: Defines if the road bottom should be displayed (useful in case of
bridge).
- `rightSide`: This field is used for the texture mapping. It defines if the side
of the texture should be used for the right side of the road (useful to disable
in case road assembly).
- `leftSide`: This field is used for the texture mapping. It defines if the side
of the texture should be used for the left side of the road (useful to disable
in case road assembly).
- `wayPoints`: Defines the path of the road.
- `roadTilt`: Defines the tilting angle corresponding to each way-point (if there
is less value than way-points, 0 is used for the last remaining way-points).
- `startingAngle`: Defines the angle of the road at the first way-point.
- `endingAngle`: Defines the angle of the road at the last way-point.
- `splineSubdivision`: Defines the degree of interpolation using B-Splines (if the
value is lower than 0, the interpolation is disabled).
- `texture`: Defines the texture to be used for the road.
- `textureScale`: Defines the length (in meter) of the road texture.
- `pavementTexture`: Defines the texture to be used for the sidewalk.
- `roadBoundingObject`: Defines if the road should have a bounding object.
- `rightBorderBoundingObject`: Defines if the right sidewalk should have a
bounding object.
- `leftBorderBoundingObject`: Defines if the left sidewalk should have a bounding
object.

### StraightRoadSegment

The `StraightRoadSegment` PROTO is the most simple one. It can only be used to
create a straight road.

%figure "Straight segment of road"

![straight.png](images/straight.png)

%end

```
StraightRoadSegment {
      SFVec3f    translation               0 0 0
      SFRotation rotation                  0 1 0 0
      SFFloat    width                     7
      SFInt32    numberOfLanes             2
      MFBool     dashedLine                TRUE
      SFFloat    roadBorderHeight          0.15
      SFFloat    startingRoadBorderWidth   0.8
      SFFloat    endingRoadBorderWidth     0.8
      SFBool     rightBorder               TRUE
      SFBool     leftBorder                TRUE
      SFBool     bottom                    FALSE
      SFBool     rightSide                 TRUE
      SFBool     leftSide                  TRUE
      SFFloat    length                    10
      SFFloat    startingRoadTilt          0
      SFFloat    endingRoadTilt            0
      MFString   texture                   "textures/road.jpg"
      SFFloat    textureScale              2
      MFString   pavementTexture           "textures/pavement.jpg"
      SFBool     locked                    TRUE
      SFBool     roadBoundingObject        FALSE
      SFBool     rightBorderBoundingObject FALSE
      SFBool     leftBorderBoundingObject  FALSE
      SFString   contactMaterial           "default"
  }
```

#### StraightRoadSegment Field Summary

Most of the fields are similar to the one of the [Road](#road) PROTO. Therefore,
only the specific ones will be explained.

- `startingRoadBorderWidth and endingRoadBorderWidth`: Instead of defining the
width of the border for each way-points, you can only specify it for the
beginning and end of the road.
- `startingRoadTilt and endingRoadTilt`: Instead of defining the tilting angle of
the road for each way-points, you can only specify it for the beginning and end
of the road.
- `length`: Defines the length of the road.

### CurvedRoadSegment

The `CurvedRoadSegment` PROTO is very simple too. It can only be used to create
a regularly curved road.

%figure "Curved segment of road"

![Curved.png](images/Curved.png)

%end

```
CurvedRoadSegment {
      SFVec3f    translation               0 0 0
      SFRotation rotation                  0 1 0 0
      SFFloat    width                     7
      SFInt32    numberOfLanes             2
      MFBool     dashedLine                TRUE
      SFFloat    roadBorderHeight          0.15
      MFFloat    roadBorderWidth           [ 0.8 ]
      SFBool     rightBorder               TRUE
      SFBool     leftBorder                TRUE
      SFBool     bottom                    FALSE
      SFFloat    curvatureRadius           10
      SFFloat    totalAngle                1.5708
      SFInt32    subdivision               8
      SFFloat    tilt                      0
      MFString   texture                   "textures/road.jpg"
      SFFloat    textureScale              2
      MFString   pavementTexture           "textures/pavement.jpg"
      SFBool     locked                    TRUE
      SFBool     roadBoundingObject        FALSE
      SFBool     rightBorderBoundingObject FALSE
      SFBool     leftBorderBoundingObject  FALSE
      SFString   contactMaterial           "default"
  }
```

#### CurvedRoadSegment Field Summary

Most of the fields are similar to the one of the [Road](#road) PROTO. Therefore,
only the specific ones will be explained.

- `curvatureRadius`: Defines the curvature radius of the center of the road.
- `totalAngle`: Defines the angle covered by the road.
- `subdivision`: Defines the subdivision of the arc.
- `tilt`: Defines the maximum tilting angle at the middle of the segment.

### HelicoidalRoadSegment

The `HelicoidalRoadSegment` PROTO represents an helicoidal road. It is mainly
meant to showcase how the [Road](#road) PROTO can be inherited to create complex
road structure in the third dimension. It can for example be used to model a
garage input ramp.

%figure "Helicoidal segment of road"

![Helocoidal.png](images/Helocoidal.png)

%end

```
Helicoidal {
      SFVec3f    translation               0 0 0
      SFRotation rotation                  0 1 0 0
      SFFloat    width                     7
      SFInt32    numberOfLanes             2
      MFBool     dashedLine                TRUE
      SFFloat    roadBorderHeight          0.15
      SFFloat    roadBorderWidth           0.8
      SFBool     rightBorder               TRUE
      SFBool     leftBorder                TRUE
      SFBool     bottom                    FALSE
      SFBool     rightSide                 TRUE
      SFBool     leftSide                  TRUE
      SFFloat    height                    20
      SFFloat    radius                    15
      SFFloat    heigthStep                5
      SFFloat    subdivision               64
      MFString   texture                   "textures/road.jpg"
      SFFloat    textureScale              2
      MFString   pavementTexture           "textures/pavement.jpg"
      SFBool     locked                    TRUE
      SFBool     roadBoundingObject        FALSE
      SFBool     rightBorderBoundingObject FALSE
      SFBool     leftBorderBoundingObject  FALSE
      SFString   contactMaterial           "default"
  }
```

#### Helicoidal Field Summary

Most of the fields are similar to the one of the [Road](#road) PROTO. Therefore,
only the specific ones will be explained.

- `height`: Defines the total height covered by the road.
- `radius`: Defines the radius of the center of the road.
- `heigthStep`: Defines the step for the road to make one complete round.
- `subdivision`: Defines the subdivision of the helicoid.

### Roundabout

The `Roundabout` PROTO represents a roundabout intersection.

%figure "Roundabout intersection"

![roudabout.png](images/roudabout.png)

%end

```
Roundabout {
      SFVec3f    translation              0 0 0
      SFRotation rotation                 0 1 0 0
      SFInt32    subdivision              16
      SFInt32    numberOfLanes            2
      SFBool     bottom                   FALSE
      SFBool     border                   TRUE
      SFFloat    borderWidth              0.8
      SFFloat    borderHeight             0.2
      SFFloat    innerRadius              4
      SFFloat    outerRadius              8
      SFBool     center                   TRUE
      SFVec2f    centerTextureScale       4 4
      SFInt32    roadNumber               4
      SFFloat    startRoadsLenght         5
      SFFloat    startRoadsWith           7
      SFInt32    startRoadsNumberOfLanes  2
      MFBool     startRoadsDashedLine     FALSE
      SFFloat    startRoadsSignsLength    0.6
      SFBool     roadBoundingObject       FALSE
      SFBool     borderBoundingObject     FALSE
      SFBool     centerBoundingObject     FALSE
      SFString   contactMaterial          "default"
      SFBool     locked                   TRUE
      MFString   centerTexture            "textures/grass.png"
      MFString   texture                  "textures/road_no_border_line.jpg"
      SFFloat    textureScale             2
      MFString   junctionTexture          "textures/asphalt.jpg"
      MFString   startRoadsTexture        "textures/road.jpg"
      MFString   inputTexture             "textures/intersection_input.jpg"
      MFString   outputTexture            "textures/intersection_output.jpg"
  }
```

#### Roundabout Field Summary

Most of the fields are similar to the one of the [Road](#road) PROTO. Therefore,
only the specific ones will be explained.

- `subdivision`: Defines the subdivision of the circle.
- `innerRadius`: Defines the inner radius of the roundabout.
- `outerRadius`: Defines the outer radius of the roundabout.
- `center`: Defines if the roundabout should have a central part.
- `centerTexture`: Defines the texture to be used for the central part.
- `centerTextureScale`: Defines the scale of the texture used for the central
part.
- `centerBoundingObject`: Defines if the central part should have a bounding
object.
- `roadNumber`: Defines the number of roads entering/leaving the roundabout.
- `startRoads...`: Defines the properties of the roads entering/leaving the
roundabout.
- `inputTexture`: Defines the sign between the input lanes and the roundabout.
- `outputTexture`: Defines the sign between the output lanes and the roundabout.

### RoadIntersection

The `RoadIntersection` PROTO represents a perpendicular intersection.

%figure "Perpendicular intersection"

![Intersection.png](images/Intersection.png)

%end

```
RoadIntersection {
      SFVec3f    translation                    0 0 0
      SFRotation rotation                       0 1 0 0
      SFInt32    roadNumber                     4
      SFFloat    roadsWith                      7
      SFBool     startRoads                     TRUE
      SFFloat    startRoadsLenght               5
      SFInt32    startRoadsNumberOfLanes        2
      MFBool     startRoadsDashedLine           FALSE
      SFFloat    startRoadsSignsLength          0.6
      SFBool     startRoadBorder                TRUE
      SFFloat    startRoadBorderHeight          0.15
      SFFloat    startRoadBorderWidth           0.8
      SFBool     startRoadBorderboundingObject  FALSE
      SFBool     boundingObject                 FALSE
      SFString   contactMaterial                "default"
      SFBool     bottom                         FALSE
      SFBool     locked                         TRUE
      MFString   texture                        "textures/asphalt.jpg"
      MFString   inputTexture                   "textures/intersection_input.jpg"
      MFString   outputTexture                  "textures/intersection_output.jpg"
      MFString   startRoadsTexture              "textures/road.jpg"
  }
```

### LaneSeparation

The `LaneSeparation` PROTO represents a road spliting into two.

%figure "Lane separation"

![LaneSeparation.png](images/LaneSeparation.png)

%end

```
LaneSeparation {
      SFVec3f    translation                 0 0 0
      SFRotation rotation                    0 1 0 0
      SFFloat    width                       14
      SFFloat    length                      5
      SFInt32    numberOfLanes               4
      SFInt32    numberOfleavingLanes        2
      SFBool     newLaneLeft                 TRUE
      MFBool     dashedLine                  TRUE
      SFFloat    roadBorderHeight            0.15
      SFFloat    roadBorderWidth             0.8
      SFBool     rightBorder                 TRUE
      SFBool     leftBorder                  TRUE
      SFBool     centralBorder               TRUE
      SFBool     bottom                      FALSE
      MFString   texture                     "textures/road.jpg"
      SFFloat    textureScale                2
      MFString   pavementTexture             "textures/pavement.jpg"
      SFBool     locked                      TRUE
      SFBool     roadBoundingObject          FALSE
      SFBool     rightBorderBoundingObject   FALSE
      SFBool     leftBorderBoundingObject    FALSE
      SFBool     centralBorderBoundingObject FALSE
      SFString   contactMaterial             "default"
  }
```

#### LaneSeparation Field Summary

Most of the fields are similar to the one of the [Road](#road) PROTO. Therefore,
only the specific ones will be explained.

- `numberOfleavingLanes`: Defines the number of lanes leaving the main road.
- `newLaneLeft`: Defines if the lanes leaving the main road goes to the left or
right.
- `centralBorder`: Defines if the central sidewalk should be present.
- `centralBorderBoundingObject`: Defines if the central sidewalk should have a
bounding object.

### AddLaneRoadSegment

The `AddLaneRoadSegment` PROTO can be used to add (or remove) one lane to the
road.

%figure "Addition of one lane"

![AddLane.png](images/AddLane.png)

%end

```
AddLaneRoadSegment {
      SFVec3f    translation               0 0 0
      SFRotation rotation                  0 1 0 0
      SFFloat    width                     7
      SFFloat    length                    20
      SFInt32    numberOfLanes             2
      SFBool     newLaneLeft               TRUE
      MFBool     dashedLine                TRUE
      SFFloat    roadBorderHeight          0.15
      SFFloat    roadBorderWidth           0.8
      SFBool     rightBorder               TRUE
      SFBool     leftBorder                TRUE
      SFBool     bottom                    FALSE
      MFString   texture                   "textures/road.jpg"
      SFFloat    textureScale              2
      MFString   newLanetexture            "textures/road_no_border_line.jpg"
      MFString   pavementTexture           "textures/pavement.jpg"
      SFBool     locked                    TRUE
      SFBool     roadBoundingObject        FALSE
      SFBool     rightBorderBoundingObject FALSE
      SFBool     leftBorderBoundingObject  FALSE
      SFString   contactMaterial           "default"
  }
```

#### AddLaneRoadSegment Field Summary

Most of the fields are similar to the one of the [Road](#road) PROTO. Therefore,
only the specific ones will be explained.

- `length`: Defines in how many meter the new lane is created.
- `newLaneLeft`: Defines if the new lane should be created on the right or left
side of the road.
- `newLanetexture`: Defines the texture to be used for the new lane.

### AddLanesRoadSegment

The `AddLanesRoadSegment` PROTO is very similar to the
[AddLaneRoadSegment](#addlaneroadsegment) PROTO except that it allows to add
several lanes to the road.

%figure "Addition of several lanes"

![AddLanes.png](images/AddLanes.png)

%end

```
AddLanesRoadSegment {
      SFVec3f    translation               0 0 0
      SFRotation rotation                  0 1 0 0
      SFFloat    width                     7
      SFFloat    length                    20
      SFInt32    numberOfLanes             2
      SFInt32    numberOfnewLanes          2
      SFBool     newLaneLeft               TRUE
      MFBool     dashedLine                TRUE
      SFFloat    roadBorderHeight          0.15
      SFFloat    roadBorderWidth           0.8
      SFBool     rightBorder               TRUE
      SFBool     leftBorder                TRUE
      SFBool     bottom                    FALSE
      MFString   texture                   "textures/road.jpg"
      SFFloat    textureScale              2
      MFString   newLanetexture            "textures/road_no_border_line.jpg"
      MFString   pavementTexture           "textures/pavement.jpg"
      SFBool     locked                    TRUE
      SFBool     roadBoundingObject        FALSE
      SFBool     rightBorderBoundingObject FALSE
      SFBool     leftBorderBoundingObject  FALSE
      SFString   contactMaterial           "default"
  }
```

#### AddLanesRoadSegment Field Summary

Most of the fields are similar to the one of the `Road` PROTO. Therefore, only
the specific ones will be explained.

- `numberOfnewLanes`: Defines the number of new lanes to be added to the road.
