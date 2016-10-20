# Practice Problems

To familiarize FRC 5806 programmers with robotics programming we've drafted this set of programming problems. These questions begin general and simple, and evolve to become specific and complex. 

On later questions it may be helpful to work with a group. Additionally, try to see if certain problems are more your niche then others; you may find that you're best suited towards data structures, sensor processing, or computer vision.  In order to be on FRC 5806 P&E, you must complete all of the General and Object Oriented problems, at least one problem each from Robotics, Electrical, and Computer Vision, and all of the problems one of the aformentioned categories (to form a specialty).

## General Problems

### Decimal to Binary

Write a program that accepts a base ten (non-fractional) number at the command line and outputs the binary representation of that number.

### Recursive Factorial

Write a function that correctly computes the factorial of a number recursively.

### Selection Sort

Implement selection sort in Java and use it to sort this list: [48, -1, 2, 5, 1, 6, 6, 8, 10, 100, 77].

## Object Oriented Problems

### Shape

Define a Shape object, where the object is any two dimensional figure, and has the following characteristics: a name, a perimeter, and an area.

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


### Gyro

Imagine you have a sensor that gives you your current rotational velocity.   Write a `while (true)` that turns a specific angle by getting rotational velocity in degrees/sec from a dummy function `float getGyro()`.  You can adjust your robot turning velocity with the dummy function `void turn(int power)`, power being an integer from -100 to 100 (0 being brake).

Now try using this sensor to keep track of robot orientation from 0-360, starting at an orientation of 0.

### Kinematics

Differential drive (or tank drive) is a drivetrain with two wheels arranged at the edges of a robot, as such:

![Differential drive robot](http://img.deusm.com/eetimes/2014/01/1320544/rex-robot-brain-02.jpg)

Write a function that maps the tangent velocity of each wheel to the consequential translational and rotational velocity of the robot, given distance between the two wheels as `l`.  This question requires physics background, in particular vectors and torque.

## Electrical Problems

### Devices

Different electrical devices consume different amounts of power at different currents and voltages.  A battery has a voltage and an arbitrary capacity in amp-hours.  Create a `Device` class that represents an electrical device, and a `Battery` class that represents a battery.  `Device` should store its current, voltage, and power with accessor methods for each, while `Battery` should have a voltage and charge, each too with accessor methods.

### Power Consumption

Next, write a `void addDevice(Device device, double hours)` method in the `Battery` class that attatches a device to the battery for a certain amount of time.  Obviously this should decrement the battery charge, but not necesarily linearly: pay attention to devices and batteries of different voltages.  For example, a 5 Amp draw for an hour at 5 volts will decrement charge less than a 5 amp draw for an hour at 12 volts.  This simulation assumes that devices of different voltages will have a 100% efficient voltage regulator between them.

### Efficiency

Finally, write a `void addDevice(Device device, double hours, double efficiency)` method in the `Battery` class that accounts for inefficient voltage regulation.  Efficiency is a double ranging from 0-1, and should be overridden as 1 if the device and battery voltage are identical (as no voltage regulator is required).

### Soldering and Hands-On Test

Speak to Michael or Josh if you plan to do this question.  It'll likely involve a project with soldering and hands-on electrical work. 

## Computer Vision Problems

Feel free to find code examples on line. Much of what these problems are testing is your ability to install software, familiarize yourself with a library, and follow online tutorials. 

### Tracking a ball

Write a program using OpenCV that tracks the position of a ball in 2D space.  If you're feeling adventurous, try doing it in 3D space.  If you're feeling super duper adventurous, try tracking two identical balls at the same time while keeping track of which is which.

### Shape identification

Write a program that can identify the shape and color of regular polygons from a webcam feed, and track them in 2D space.

### Object Learning

Write a program that can take a picture of an object, have a user select the object from the picture and track the object in 2D space from a continuous webcam input.
