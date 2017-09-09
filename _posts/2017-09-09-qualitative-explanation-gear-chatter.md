---
layout: post
title: "A qualitative description of gear chatter phenomena"
date: "2017-09-09"
categories: [Mechanics]
use_mathjax: false
---

When I and my colleagues faced the issue of gear chatter while designing the joints of the R1 robot we searched the web for references on the matter and surprisingly, found little material on the topic.
This post presents a qualitative description of gear chatter phenomena, and a few illustrations, to help delineate the issue.

## Conditions for chatter

Gear chatter typically occurs in high-friction transmissions yielding under load.
Two of the most representative examples of these are lead-screw transmissions and worm-gear transmissions.

<div align="center"><img src='{{ site.url }}asset-bank/chatter-diagram.svg' height='200pt'/></div>

Another requirement for gear chatter to occur is that the transmission must have a certain degree of backlash.
Finally a third characteristic that helps the onset of chatter is a marked difference of stiffness between the materials constituting the transmission elements coming into contact.

## Description of the phenomenon

The following figure represents the phenomenon of chatter with reference to a worm-gear transmission.

1. The worm initiates the movement. Because of gear backlash, gear inertia and gear stiction the motion of the gear does not follow immediately.
1. The worm comes into contact again with the worm gear, breaking away contact stiction and starting the gear's motion.
1. The gear then begins to move and accelerates, helped by the external load, until it impacts the worm on its lower side effectively switching the side of the tooth involved in the load transfer.
1. This blocks the gear with stiction generally greater than the starting one, which limits the gear motion while the worm is free to move ahead of the gear; upon contact with the lower side of the gear tooth the gear motion starts again.
1. The gear then accelerates once again, and once again it hits the worm switching contact.

<div align="center"><img src='{{ site.url }}asset-bank/chatter-sequence.svg' height='1000pt'/></div>

This contact switching cycle generates vibrations that generally self amplify over time.

This behaviour results in position, velocity and torque traces like the ones represented below that were acquired during the up-down motion of a worm-gear joint.

<div align="center"><img src='{{ site.url }}asset-bank/chatter-plot.svg' height='400pt'/></div>

### Comments

I believe this description could be improved. If you have suggestions or comments on how to do this please [contact me]({{ site.url }}/about/).
