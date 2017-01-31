---
layout: page
title: Projects
permalink: /projects/
---

### iCub 

![The iCub robot]({{ site.url }}/images/icub_pris.jpg)
The iCub is a 53DOF open-source humanoid robot. Since 2007 I've completed the design and testing of several of its parts. Among these, the upper-body, the legs, the six-axis force-torque sensors, the covers and the head. Since 2010 I have taken the role of hardware lead of the project.

More details about the robot can be found on the project website [www.icub.org](www.icub.org).

***

### R1

![The R1 robot]({{ site.url }}/images/r1_pris.jpg)
The R1 represents an attempt to bring the iCub technology closer to real world applications, and was specially focused on making the robot system affordable.

The key ingredients to achieve this goal were the extensive use of engineering plastics, parallel kinematics, and of a design for manufacturing approach.

An introductory video about the robot can be found [here](https://www.youtube.com/watch?v=TBphNGW6m4o).

***
### Minor software projects
#### Symbolic spatial vector algebra 
During my PhD I struggled with writing the equations describing the dynamics of simple robot manipulators, and often whished this annoying step could be at least partially automated.
A simple solution I concieved was to translate Roy Featherstone's SVA Matlab library to the [Maxima](http://maxima.sourceforge.net/) Computer Algebra System (CAS).
Maxima's symbolic computations capabilities allow to generate the needed equatons.
A very rough implementation is available in my GitHub sandbox repo.
In my spare time I'm trying to complete a similar porting to Sympy.