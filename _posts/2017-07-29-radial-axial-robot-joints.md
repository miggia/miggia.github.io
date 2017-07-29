---
layout: post
title: "Robot joints: the difference between 'radial' and 'axial' layouts"
date: 2017-07-29
---

Let us define loosely "radial" joints as joints where the rotation axis is oriented transversely to the main direction defined by the robot link. Conversely let us call "axial" joints the ones whose rotation axis is approximately aligned with the principal link direction. When designing a robot with rotational joints there are marked differences that arise from the particular joint layout and kinematics that are selected.



A schematic representation of these two types of joints is shown hereafter.

<div align="center"><img src='{{ site.url }}/asset-bank/rad_vs_ax.svg' height='300pt'/></div>

This difference in orientation reflects into very relevant differences in terms of joint embodiment.
Although the considerations reported here are rather general, I'm writing these while thinking of electrically actuated robots.

## Bearing layout

The most important difference between radial and axial joints is the way tilting moments (or transverse moment loads) are supported.
<div align="center"><img src='{{ site.url }}/asset-bank/rad_vs_ax_2.svg' height='300pt'/></div>
In radial joints two separate support areas are generally available; hence two angular, or radial ball bearings can be used.
In the case of axial joints the main joint bearing is placed in the proximity of the joint output, and is required to withstand radial loads as well as tilting moment loads.
<div align="center"><img src ='{{ site.url }}/asset-bank/rad_vs_ax_2_eq.svg' height='300pt'/></div>
This, in turn, requires stiffer and generally bigger bearings.
Crossed-roller bearings are a common choice; other solutions include four-points-of-contact bearings, and mated angular ball bearings.

## Linear actuation

Another marked difference relates to linear actuation.
In radial joints rotational motion can be transmitted from a linear actuator with a crank-based mechanism.
<div align="center"><img src='{{ site.url }}/asset-bank/crank-mechanism.svg' height='200pt'/></div>
The situation is more complex in the case of axial joints, for which no simple and practical solution has yet been developed.

An [interesting patent from Boston Dynamics](US2014123789A1) (see figure below) shows how a linear actuator can be exploited to generate rotational motion.
<div align="center"><img src='{{ site.url }}/asset-bank/US2014123789A1.PNG' height='300pt'/></div>
This design however requires a double helical cam based transmission that seems rather bulky, and difficult to manufacture making it probably not very practical.

## "Axial-only" configurations

A significant advantage of axial joints is that they are more "modular" in nature.
Once the basic module has been developed and tested, it can be replicated and combined in series to obtain a multi-DOF system.

Indeed both this approach was the one followed by researchers at DLR for the development of the [LWR-III](hirzinger_02) and by the mechatronics group at DFKI Bremen that developed the [SpaceClimber](spaceclimber-web) robot.

A cross-section of the LWR-III joint and how it is employed to obtain the structure of the DLR LWR-III robot are shown hereafter.

<div align="center"><img src='{{ site.url }}/asset-bank/dlr-lwr-iii-joint.jpg' height='350pt'/></div>
<div align="center"><img src='{{ site.url }}/asset-bank/dlr-lwr-iii-modularity-2.jpg' height='250pt'><	img src='{{ site.url }}/asset-bank/dlr-lwr-iii-modularity.jpg' height='250pt'></div>

## Cable routing

In multi-DOF robots electrical cables (communication and/or power) need to be routed to all joints and actuators. Cables thus have a connection on both links of a joint. The way cables are routed in the joint region highlights another important difference between axial and radial joints.

In axial joints the preferred option is to route cables close to the joint axis thus minimizing the length of cable slack. This choice requires a "hollow shaft" joint design.

In the case of radial joints cables are routed on the lateral sides of the joint close to the joint axis.

# References

[US2014123789A1]: https://worldwide.espacenet.com/publicationDetails/biblio?FT=D&date=20140508&DB=EPODOC&locale=en_EP&CC=US&NR=2014123789A1&KC=A1&ND=5
[spaceclimber-web]: http://robotik.dfki-bremen.de/en/research/robot-systems/spaceclimber.html
[schafer_08]: elib.dlr.de/55362/1/i-sairas2008_Schäfer.pdf
[hirzinger_02]: http://ieeexplore.ieee.org/document/1014788/

- [Actuator (US 2014/123789 A1)][US2014123789A1]
- [SpaceClimber web page][spaceclimber-web]
- [DLR's torque-controlled light weight robot III-are we reaching the technological limits now?][hirzinger_02]
- [Light-Weight Mechatronics and Sensorics for Robotic Exploration: a DLR Perspective][schafer_08]
