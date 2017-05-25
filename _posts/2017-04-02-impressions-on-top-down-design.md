---
layout: post
title: "Impressions on Top-Down CAD design"
date: 2017-04-02
---

The R1 project involved an extensive use of top-down design.
In top-down design important geometric information is captured in a "source model" (a.k.a. "skeleton model" or "master model") and is then propagated to lower level assemblies and parts by proper referencing. This design approach is also referred to as "master model", or "in-context" depending on the CAD environment of choice. After using it day-to-day for more than one year I gathered some observations that I'm sharing hereafter.

## Is it really useful? Does it pay off?

The biggest advantage of the top-down approach is that a given design can be controlled from a single location. Instead of needing to open and modify several files to perform a design update, all (or at least most) geometries can be modified from a single file. This possibility brings great advantages, but there are potential drawbacks. The natural question that arises then becomes: "are the benefits worth the hassle?". In this post I'll try to answer this question.

## a few things that can go wrong

It is possible that not all members of a design team have a thorough understanding of the top-down design methodology.
This heterogeneity of preparation is often a source of problems.What is likely to happen is that designers that are not used to the top-down approach continue to rely on the standard bottom-up way of doing things.
This leads to designs where part of the assembly are modeled top-down and other parts are not. If this model is then handed out to a third party things get very confusing because different parts of the system are done in different ways.

Another issue in top-down design is that it introduces relations that are not immediately visible to the designer, specially when considering low-level assemblies. References within Creo Parametric are visible through through `Copy Geometry` features that are generally placed at the top of the model tree. These however are often embedded at the part level and not directly visible when opening an assembly. What often happens is that when you open a given assembly and need to modify parts you are likely to do this with the standard bottom-up approach, and only later realize that top-down design intent was embedded in the models. This again leads to model done with mixed approaches (part top-down and part bottom-up). Overcoming this requires a change of mindset, to "think top-down", to always assume top-down design intent is embedded in the models and to look for it and understand it before doing modifications.

Finally building the geometry driving model (i.e. the skeleton model) gets extremely tricky, as the complexity of a given assembly increases. Indeed it rather easy to make small referencing errors that lead to unexpected model behaviours or model failures when geometries are changed and updated (see below on how to avoid this). This problem is not initially visible and becomes more and more critical as the complexity of models increases. The case of multi-limb, multi-DOF articulated robots, naturally lends itself to cause this class of issues.

## Other reccomandations

### use CSYSs, avoid planes and sketches

When creating references it is tempting to use features such datum planes, sketches, and axes. Planes, and sketches however are "brittle" when it comes to 3D rotations. What happens often is that when a plane is rotated of over 180° plane normals flip thus corrupting many of the dependent features. Sketches are even worse because when jotting them down it is extremely easy to introduce constraints which will not allow a proper regeneration of the sketch, once this is moved and rotated.

Contrarily datum points are more robust. Coordinate systems are, in my opinion, the best option, as both position and orientation are properly defined.

### train and inform your team

It is of the utmost importance that all people working on an assembly done in top-down are properly informed on where design intent is captured and how it is propagated to lower level assemblies.

Needless to say this gets particularly difficult if part of the design is out-sourced to third parties, where you have lower degree of control.

### don't overdo it

Although you could ideally capture all design intent in skeleton models I actually do not think this is reasonable.
The more top-down you use, the more effort will be required to create models and to maintain cross-model relationships consistent. In this case the suggestion is to start small by adding only the most important geometric features, and to increase complexity gradually. A good starting point is to limit yourself to representing only the kinematics of your design in the skeleton model.

## When is it worth it?

After using top-down design for a while I have mixed feelings about it. In our last project my impression is that required more work than it saved. Nevertheless we gained some valuable insights in the process and I expect next time things will be smoother.

I think that top down design is particularly useful in two specific situations:

1. Exploring motions of a complex mechanisms
2. Exploring different design approaches at the conceptual design stage

In these cases having top-down in your model really saves a lot of time. If you find yourself in these situations I recommend you seriously consider going top-down. Designing a robotic system with more than 4DOF or a parallel mechanism are two examples where this option would be advantageous.

A further advantage for robotics projects is that having top-down kinematics modeled with reference frames is beneficial for simulation purposes. In this case checking simulations and the consistency between the CAD model and a simulation model within a different simulation environment becomes easier.

To sum up I'd recommend the use of top-down design, specially for complex, multi-DOF rigid-body systems, and specifically to represent the systems' kinematics. 

## What's your take?

Have you been using top-down design? How did you find it? What do you think about it?
I'd be curious to know your point of view; feel free to [contact me]({{ site.url }}/about/) and share your experience.
