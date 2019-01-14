# SCNLine

Functions and classes for creating thick line geometries in a application using SceneKit.

[![Swift 4.2](https://img.shields.io/badge/Swift-4.2-orange.svg?style=flat)](https://swift.org/)

## Introduction

SCNLine is a class for drawing lines of a given thickness in 3D space.
In most situations in 3D projects the typically used method would use [GL_LINES](https://www.glprogramming.com/red/chapter02.html#name14); which can be exercised in SceneKit with [this primitive type](https://developer.apple.com/documentation/scenekit/scngeometryprimitivetype/line). However [glLineWidth](https://developer.apple.com/documentation/opengles/1617268-gllinewidth?language=occ) is now depricated, which is initially why I made this class.

For more information on drawing primitive types in OpenGL or otherwise, please refer to [this document](http://15462.courses.cs.cmu.edu/spring2018content/lectures/00_opengl/00_opengl_slides.pdf), or if you want to see how it's applied in SceneKit, check out my [first Medium article about building primitive geometries](https://link.medium.com/umwbtn8afT).

Please feel free to use and contribute this library however you like.
I only ask that you let me know when you're doing so; that way I can see some cool uses of it!

## Example

It's as easy as this to a line geometry:

```
let lineGeometry = SCNGeometry.line(points: [
	SCNVector3(0,-1,0),
	SCNVector3(0,-1,-1),
	SCNVector3(1,-1,-1)
], radius: 0.1)
```

This will draw a line of radius 10cm from below the origin, forwards and then to the right in an ARKit setup.
The y value is set to -1 just as an example that assumes the origin of your scene graph is about 1m above the ground.

Other parameters that can be passed into SCNGeometry.path:

| name          | description                                                                     | default            | example                         |
|---------------|---------------------------------------------------------------------------------|--------------------|---------------------------------|
| points        | Array of SCNVector3 points to make up the line                                  | no default         | [SCNVector3(0,-1,0),  SCNVector3(0,-1,-1),  SCNVector3(1,-1,-1)] |
| radius        | Radius of the line in meters                                                    | no default         | 0.1                             |
| edges         | The number of vertices used around the edge of the tube shaped line to be exteneded throughout the geometry.    | 12, minimum is 3                 | 16                              |
| maxTurning    | Maximum number of points to make up the curved look when the line is turning to a new direction.    | 4                  | 16                      |


<!-- While in the examples below it shows that this can be used for drawing apps I would not recommend this class for that in its current state, because the current class regathers vertices from the very beginning of the line right to the end, which is very inefficient as most will remain the same. -->

<!-- Here's some basic examples of what you can do with this Pod: -->

![Line Example 1](https://github.com/maxxfrazer/SceneKit-SCNLine/blob/master/media/line-drawing-1.gif)
<!-- ![Line Example 2](https://github.com/maxxfrazer/SceneKit-SCNLine/blob/master/media/line-example-2.gif) -->
<!-- ![Line Example 3](https://github.com/maxxfrazer/SceneKit-SCNLine/blob/master/media/line-example-3.gif) -->
