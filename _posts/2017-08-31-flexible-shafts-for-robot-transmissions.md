---
layout: post
title: "A review of flexible-shaft transmissions in robotics"
date: "2017-08-31"
categories: [Robotics, Mechanical Design, Review, Flexible Shaft]
use_math: true 
---

I and my colleagues recently tried to file a patent for a 2DOF robot joint actuated by flexible shafts, that was developed as part of the R1 project.
Upon review, we were informed by the European Patent Office that previous art is available describing embodiments similar to ours and that the patent is unlikely to be granted.
The review came with a list of technical documents describing relevant implementations of robot systems with flexible shaft transmissions that I thought would be useful sharing, because not easily obtained.

## why use flexible shafts?

Flexible shafts are devices for transmitting rotary motion between two bodies. Flexible shafts consist of multi-layer wound steel coils, that can be bent according to need.

<div align="center"><img src='{{ site.url }}asset-bank/flex-shaft-set-photo.jpg'/></div>

Flexible shafts are often protected with a non-rotating outer casing that generally comprises ball bearings to keep the shaft terminals in place during rotation.
Flexible shafts have very good mechanical efficiencies (up to 90%), that however decreases when they are bent, and rather good torsional stiffnesses. Furthermore, they can rotate at considerable angular velocities, up to 50000rpm.

Flexible shafts find applications for substituting complex drive units such as angle gearboxes, universal joints, etc., especially when the bodies connected move relatively in space.
Their use allows considerable design freedom and reduces the requirements for tight part tolerances.

These advantages altogether make them an appealing solution for mechanical transmission in mechatronic systems for connecting electric motors to their driven gearboxes (as represented in the following image).

<div align="center"><img src='{{ site.url }}asset-bank/flex-shaft-diagram.svg'/></div>


Indeed, this application has been considered and they have sometimes implemented in robotic system: the present article presents a review of the most important works on this topic so far.

## Device, JP S6112692

A very interesting implementation of this concept is presented in a [Japanese patent][JP S6112692] document dating back to 1986.
The document images clearly show a 3DOF robot driven with worm-gear speed reducers with flexible shaft housed inside the robot outer shell.

<div align="center"><img src='{{ site.url }}asset-bank/JP-S6112692_01.PNG' height='250pt'/></div>
<div align="center"><img src='{{ site.url }}asset-bank/JP-S6112692_02.PNG' height='250pt'/><img src='{{ site.url }}asset-bank/JP-S6112692_03.PNG' height='250pt'/></div>

Unfortunately given the lack of automatic translation tools and my ignorance of Japanese it is impossible to extract further information from this document.

## Wrist of robot, JP S58102694 A

A second early 1983 [Japanese patent][JP S58102694 A] by Nissan Motor Corp. shows a cross-section of a 3DOF robot end-effector, driven with flexible shafts. Also, in this case, the flexible shafts run inside the robot shells.

<div align="center"><img src='{{ site.url }}asset-bank/JP-S58102694-A.PNG' height='400pt'/></div>

In this case, the actuators drive the robot joints directly, and no speed reducers are represented on the joints.
The document nevertheless shows that large portions of internal volume must be kept free to allow the motion of the flexible shafts as the joints of the robot rotate.

## Robot wrist and spray applicator, US 5887800 A

A more recent [patent][US 5887800 A] by Stan McClosky for Fanuc Robotics presents a solution to the volume occupancy problem.

In this embodiment, the motors driving the robot's wrist are installed at the robot's base (Fig.1).
Fig.2 shows a detail of the wrist with a hollow-shaft concentric geared transmission system.
The three flexible shafts enter the wrist transmission at fixed entry-points, where they engage geared shafts that convey the motion to the three wrist DOF. This mechanism also allows introducing a speed reduction between 14:1 and 12:1.
In this specific embodiment, the flexible shafts entry-points remain constant, rigidly fixed to the link before the wrist articulation.
This, in turn, does not entail the introduction of an internal free-volume to allow the flex-shafts sweep during motion.

<div align="center"><img src='{{ site.url }}asset-bank/US-5887800-A_01.PNG' height='400pt'/></div>
<div align="center"><img src='{{ site.url }}asset-bank/US-5887800-A_02.PNG' height='400pt'/></div>

## Link actuation devices, EP 2998081 A1

The device described in the [EP 2998081 A1 patent][EP 2998081 A1] by Sone Keisuke, Isobe Hiroshi and Nishio Yukihiro provides yet another example of the use of flexible shaft transmissions.
The patent presents a fast-moving 2DOF joint that resembles Mark Rosheim's [OmniWrist III][OmniWrist III] in its design.

<div align="center"><img src='{{ site.url }}asset-bank/EP-2998081-A1_01.PNG' height='250pt'/></div>

A flexible-shaft transmission runs through the joint for actuating distal DOF as shown in the following image.

<div align="center"><img src='{{ site.url }}asset-bank/EP-2998081-A1_02.PNG' height='250pt'/></div>

Interestingly the article also provides a mathematical formulation for describing the curve done by the internal flexible-shaft.
Indeed the authors argue that in the plane orthogonal to the joint's axis of rotation the curve traced by the flexible-shaft is a circular arc.

<div align="center"><img src='{{ site.url }}asset-bank/EP-2998081-A1_03.PNG' height='350pt'/></div>

With reference to the diagram above, the following equations hold:

$$H = \dfrac{1}{2}D$$

$$S = 2 \cdot \left(D+H \right)$$

The distance of the center of the

$$ R = R_1 + R_2 = \dfrac{D}{\sin \theta} + \dfrac{H}{\tan \theta} = D \cdot \left(\dfrac{1}{\sin\theta} + \dfrac{1}{2 \cdot \tan\theta} \right)$$

The formula allows the calculation of the minimum radius of curvature $R_{min}$ given the maximum joint swivel angle $\theta_{max}$.

$$ R_{min} = D \cdot \left(\dfrac{1}{\sin\theta_{max}} + \dfrac{1}{2 \cdot \tan\theta_{max}} \right)$$


## Driving mechanism for robot hand, JP 2010069580

Another example of the use of flexible-shaft transmissions in robotics is constituted by the 2010 [Japanese patent JP 2010069580][JP 2010069580] developed by Takayama Yuki and Kanbe Masayuki for Kawasaki Heavy Industries.

<div align="center"><img src='{{ site.url }}asset-bank/JP-2010069580.PNG' height='500pt'/></div>

The document presents a robotic joint with a strain wave (a.k.a. Harmonic Drive) speed reducer driven remotely by a motor connected to it via a flexible-shaft.
More in detail Figure 3 and figure 5 show two slightly different variants of this design: in the first case the axis of the flex-shaft and of the strain wave speed reducer coincide, whereas in the second case they are placed at a 90° angle thanks to a bevel gear pair.

## Medical instrument, DE 102013204984 A1

The use of flex-shafts has also been considered for medical applications as described in the 2012 [German patent DE 102013204984 A1][DE 102013204984 A1] by Stephan Prestel.
The patent describes a compact pivoting end-effector and jaw, driven by a worm-gear reducer connected to its driving motor by means of a flexible-shaft.

<div align="center"><img src='{{ site.url }}asset-bank/DE-10203204084-A1_01.PNG' height='250pt'/><img src='{{ site.url }}asset-bank/DE-10203204084-A1_02.PNG' height='250pt'/></div>
<div align="center"><img src='{{ site.url }}asset-bank/DE-10203204084-A1_03.PNG' height='500pt'/></div>

## Wabian robot upgrade by Kishi et al.

It is finally worth mentioning that more recently flex-shaft transmissions have also been employed on humanoid robots.
Kishi et al. have recently published an [article][kishi_16] on the modification of the Wabian humanoid arms aimed at increasing their maximum allowable velocity.
In this embodiment the flex-shafts are not housed within the robot's torso and run externally as represented in the following photographs.

<div align="center"><img src='{{ site.url }}asset-bank/kishi_16_01.jpg' height='300pt'/><img src='{{ site.url }}asset-bank/kishi_16_02.jpg' height='300pt'/></div>

A digram of the layout is presented below. It is worth noting that for the sake of simplicity the authors chose to connect the flexible-shaft directly to the Harmonic Drive input axis, without adding a 90° angle with, for example a bevel gear pair, even if that would have resulted in a more compact design.

<div align="center"><img src='{{ site.url }}asset-bank/kishi_16_03.PNG' height='200pt'/></div>


# References

[DE 102013204984 A1]: https://worldwide.espacenet.com/publicationDetails/biblio?FT=D&date=20131010&DB=EPODOC&locale=en_EP&CC=DE&NR=102013204984A1&KC=A1&ND=4
[EP 2998081 A1]: https://worldwide.espacenet.com/publicationDetails/biblio?FT=D&date=20160323&DB=EPODOC&locale=en_EP&CC=EP&NR=2998081A1&KC=A1&ND=4
[JP S6112692]: https://worldwide.espacenet.com/publicationDetails/biblio?FT=D&date=19860124&DB=EPODOC&locale=en_EP&CC=JP&NR=S6112692U&KC=U&ND=4
[JP S58102694 A]: https://worldwide.espacenet.com/publicationDetails/biblio?FT=D&date=19830618&DB=EPODOC&locale=en_EP&CC=JP&NR=S58102694A&KC=A&ND=4
[US 5887800 A]: https://worldwide.espacenet.com/publicationDetails/biblio?FT=D&date=19990330&DB=EPODOC&locale=en_EP&CC=US&NR=5887800A&KC=A&ND=4
[JP 2010069580]: https://worldwide.espacenet.com/publicationDetails/biblio?FT=D&date=20100402&DB=EPODOC&locale=en_EP&CC=JP&NR=2010069580A&KC=A&ND=4
[kishi_16]: http://ieeexplore.ieee.org/document/7409982/
[OmniWrist III]: https://www.anthrobot.com/omni_III/

- [Medical instrument, DE 102013204984 A1][DE 102013204984 A1]
- [Link actuation devices, EP 2998081 A1][EP 2998081 A1]
- [Device, JP S6112692][JP S6112692]
- [Wrist of robot, JP S58102694 A][JP S58102694 A]
- [Robot wrist and spray applicator, US 5887800 A][US 5887800 A]
- [Driving mechanism for robot hand, JP 2010069580][JP 2010069580]
- [Development of a Humorous Humanoid Robot Capable of Quick-and-Wide Arm Motion][kishi_16]
- [OmniWrist III web page][OmniWrist III]
