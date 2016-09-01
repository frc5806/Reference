# Tutorials

An introduction to the programming and electronics departement of team 5806. 

# Table of Contents

* [Tool Primar](#tool-primar)
* [Practice Problems](#practice-problems)
* [Style Guide](#style-guide)

# Tool Primar

## Git

### GUI git

### Command line git

http://gitimmersion.com/index.html

## Eclipse

## WPILib

## Control Theory

### PID Loops

### Sensory Fusion

## Common Sensors

### Distance Sensors

### USB Camera

### IMU

### Encoders

# Practice Problems

To familiarize FRC 5806 programmers with robotics programming we've drafted this set of problems relating to robot control. These questions begin general and simple, and evolve to become specific and complex. On later questions it may be helpful to work with a group. Additionally, try to see if certain problems are more your niche then others; you may find that you're best suited towards data structures, sensor processing, or computer vision.

## General Problems

### Decimal to Binary

Write a program that accepts a base ten (non-fractional) number at the command line and outputs the binary representation of that number

### Integer to English

Write a program that takes an integer and displays the English name of that value.

You should support both positive and negative numbers, in the range supported by a 32-bit integer (approximately -2 billion to 2 billion).

### Recursive Factorial

Write a function that correctly computes the factorial of a number recursively.

## Object Oriented Problems

### Shape

Define a Shape object, where the object is any two dimensional figure, and has the following characteristics: a name, a perimeter, and a surface area.

### Circle

Define a subclass of your Shape class and call it Circle. It should retain and accurately output the values of the aforementioned characteristics of a Shape.

### Triangle

Define a subclass of your Shape class and call it Triangle. This time, the name of the triangle should take into account if it is equilateral (all 3 sides are the same length), isoceles (only 2 sides are the same length), or scalene (no 2 sides are the same).

## Robotics Problems

Note: a lot of these problems require writing "dummy functions" to act as a simulation environment.  You may not even be able to fully test your code.  This is a valuable skill for robotics programming, as you often have limited access to the robot for testing and need to write code off board.  More advanced dummy functions can help get around this by creating a more accurate simulation environment.

### Odometry

You are given dummy functions `void setLeftMotor(int power)` and `void setRightMotor(int power)`, where power is -100 to 100 with 0 being brake.  Write a program that drives in a circle.

Now write a program that drives in a square, assuming that while turning at full power the robot takes 0.4 seconds to turn 90 degrees.

Now here comes the tricky part: write a program that drives the robot in a sine wave.  To be more clear, the robot follows an arbitrarily scaled version of the parametric equation `y = sin(t)`, `x = 0`.  This can be seen in the below gif, where the robot position is represented by the circle.  Write a program that makes the robot move in this manner.

![siny robot](http://i.giphy.com/sajxSgoRSfh60.gif)


### Gyroscope

Imagine you have a sensor that gives you your current rotational velocity.   Write a `while (true)` that turns a specific angle by getting rotational velocity in degrees/sec from a dummy function `float getGyro()`.  You can adjust your robot turning velocity with the dummy function `void turn(int power)`, power being an integer from -100 to 100 (0 being brake).

Now try using this sensor to keep track of robot orientation from 0-360, starting at an orientation of 0.

### Sensor Mapping

Imagine you have a constantly rotating distance sensor strapped to the top of your robot.  The sensor can read a distance value (like an ultrasonic sensor), in addition to the angle that it is currently at (0-360, clockwise where 0 is pointing forwards).  Your task is to form a 2d image of nearby obstacles using this sensor.  You are operating in a `while (true)` loop, and can call dummy functions `float getDistance()` and `float getAngle()`.  Over time build a 2D boolean array representing your image.

The previous paragraph assumes that the sensor reads in a direct line.  However, most real distance sensors have something called a "beam width."  For example, imagine you have an ultrasonic sensor with a pencil directly in front of it.  If you rotate it a little bit so that the sensor is not pointing directly at the pencil, it might still read a short distance as if the pencil weren't there.  Alternatively if the sensor were pointing directly at the pencil it might not see it at all.  Basically, the concept of a beam angle introduces error into the equation: the bane of a robotics programmer.  All sensor readings will have associated error, something we'll have to deal with extensively.  For now, define an arbitrary beam angle variable and try to compensate for it in your program.

If you're really insane, there's yet another degree of complexity we can add to this fun problem.  Currently you are mapping discrete points rather than lines.  If the robot is trapped in a circular room but has only taken 4 sensor readings, it only knows that there are 4 single-pixel obstacles around itself.   To compensate for this we must maintain yet another 2D image, where a predicted image is formed by connecting the dots on the first image.   Try different methods of isolating discrete obstacles, for example defining a threshold pixel distance where dots should or should not be connected.

### Kinematics and Control

Kiwi drive is a drivetrain with three omniwheels arranged at the edges of a robot in an equilateral triangle, as such:

![Kiwi drive diagram](http://i.stack.imgur.com/x6u31.png)

Write a function that maps a 3D joystick input of X velocity, Y veloctity, and rotational velocity scaled from -100 to 100 to three motor values scaled -100 to 100.   This question requires physics background, in particular vectors and torque.

If you were succesful, try it the other way around; from given motor inputs A, B, and C update the position (x,y,theta) of a simulated robot.

## Electrical Problems

### Devices

Different electrical devices consume different amounts of power at different currents and voltages.  A battery has a voltage and an arbitrary capacity in amp-hours.  Create a `Device` class that represents an electrical device, and a `Battery` class that represents a battery.  `Device` should store its current, voltage, and power with accessor methods for each, while `Battery` should have a voltage and charge, each too with accessor methods.

### Power Consumption

Next, write a `void addDevice(Device device, double hours)` method in the `Battery` class that attatches a device to the battery for a certain amount of time.  Obviously this should decrement the battery charge, but not necesarily linearly: pay attention to devices and batteries of different voltages.  For example, a 5 Amp draw for an hour at 5 volts will decrement charge less than a 5 amp draw for an hour at 12 volts.  This simulation assumes that devices of different voltages will have a 100% efficient voltage regulator between them.

### Efficiency

Finally, write a `void addDevice(Device device, double hours, double efficiency)` method in the `Battery` class that accounts for inefficient voltage regulation.  Efficiency is a double ranging from 0-1, and should be overridden as 1 if the device and battery voltage are identical (as no voltage regulator is required).

## Computer Vision Problems

### Tracking a ball

Write a program using OpenCV that tracks the position of a ball in 2D space.  If you're feeling adventurous, try doing it in 3D space.  If you're feeling super duper adventurous, try tracking two identical balls at the same time while keeping track of which is which.

### Shape identification

Write a program that can identify the shape and color of regular polygons from a webcam feed, and track them in 2D space.

### Object Learning

Write a program that can take a picture of an object, have a user select the object from the picture and track the object in 2D space from a continuous webcam input.

# Style Guide

Below is the general style guide for programming on FRC team 5806.  As we are one collaborative team, our code must mesh as if it were written by one person.  For this reason (and some others), it is crucial that all programmers follow the guidelines below.  In addition to this general description, there are also language specific guides in the repo.

## Naming

Classes names are begin with a capital letter. There are no spaces or underlines between words, and each successive word begins with a capital letter (e.g. `NeuralNetwork`). Variables and functions begin with a lower case letter, there are no spaces or underlines between words, and each word after the first begins with a capital letter. Constants are an exeption to this rule. Constants are fully capitalized, and there are underscores between words.

An example of proper naming:

```java
public class ExampleClass {
	public final float EXAMPLE_CONSTANT = 3.14159;
	private double exampleMemberVariable;
	public void exampleMethod(int exampleVariable) {}
}
``` 

##General Syntax Rules

The following rules apply to most languages.

#### Rule #1: Curly brace placement

The following is right:

```java
if (5 == 5) {
	/// do stuff
}
```

The following is acceptable for short, single-line blocks:
```java
if (5 == 5)
	myVarable += 5;
```

The following is wrong:

```java
if (5 == 5)
{
	/// do stuff
}
```

Get over it.

#### Rule #2: Tabs, not spaces

Some people indent each block of code with 4 spaces, some with 2. We do neither. We indent with tabs.

#### Rule #3: Line length

This rule is a little more nuanced.  Code should be concise and readable, but this doesn't mean to throw everything on one line.  80 characters per line is the soft limit, while 100 characters per line is the hard limit. This can be achieved using a number of strategies; in particular, do not be afraid to break up long declarations or booleans into lines:

```cpp

/// this
int ohno = ((25*14)/22)*(3904-234+423)+((223*13254)/232)*(3953204-2334+4223)

/// should be this
int ohno = ((25*14)/22)*(3904-234+423)
		  +((223*13254)/232)*(3953204-2334+4223)
```

As most languages ignore whitespace in most situations, this is a good strategy for making code more readable.

#### Rule #4: Control structures

As part of making code concise and grouping blocks together, related code blocks should be grouped together as much as possible.  Example:

```cpp
if (...) {
	/// do stuff
} else if (...) {
	/// do stuff
} else {
	/// do more stuff
}
```

This should also be followed (in most cases) with try-catch statements and do-while loops. 

## Version Control

#### Rule #1: Commit contents

Imagine you've been working on the drive code and the autonomous code, and want to commit your changes.  These are __separate__ commits.

#### Rule #2: Commit Messages

`asdf` is a bad name for a commit.  We've all done it before, but we don't do it here.  The title should be at least two words, and if that's not totally self explanatory you should probably put in a description. 

#### Rule #3: Branching and Pushing

If you and another team member are working on a piece of code in two separate directions, you each need a branch.  If you're working on it in the same direction, a branch probably isn't necessary (but be wary of merge conflicts).  In cases of robot code, never push untested/unworking code to the main branch, as somebody probably *will end up running it*.

## Documentation and Comments

Code is rarely ever truly "self documenting."  This is just something we tell ourselves at night to help us sleep.  Thus, every class should have a comment describing it immediately beforehand.  In Java, this should be directly on top of the class declaration:

```java
/* Describes a cat-tank hybrid.
 *
 * CatTank objects should only be
 * created when absolutely necessary.
 */
public class CatTank {
	// Describes the number of
	// bullets in the CatTank
	private int bullets;
	
	// Constructs a CatTank
	public CatTank(int bullets) {
	
	}
}
```

As you can see in this example, not only is the class documented but also the constructor, the methods, and the variables. 

If you'd like to make a comment that isn't documentation, such as a note to a teammate or a clarification on something messy, three slashes should be used rather than two (or in Python, two hashes instead of one). This helps distinguish documentation for somebody just browsing the code, and makes the file easier to parse for automatic documentation generators such as doxygen and cldoc.  Additionally, comments should have a space between the forward
slashes and the comment message. 
