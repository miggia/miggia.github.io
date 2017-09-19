---
layout: post
title: "Observations on using to OnShape after a Creo Parametric experience"
date: "2017-09-19"
category: CAD
keywords: [Creo Parametric, OnShape]
use_mathjax: false
---

A couple of years ago my friend [Traveler](https://www.linkedin.com/in/travelerhauptman/) of [MechAdept](http://www.mechadept.com/) suggested I should try out a new web-based parametric CAD system that had just been released: that CAD was [OnShape](https://www.onshape.com/).
In the past weeks I finally managed to set aside some time to tinker with it: here are my first impressions on using it after almost 10 years of Creo Parametric.


## Key functionalities

Some of the features that I consider most important in Creo Parametric are those related to top-down design and the way to capture model intent.
In my experience with Creo Parametric I found the following list of features to be the most important and critical for effective CAD use:
* the definition of reference frames with the coordinate frames feature,
* the definition of part parameters to be later referenced in design
* the addition of custom part properties to be exploited whe generating a bill of materials (BOM)

I thus set out to find the equivalent functionalities within the OnShape environment.

OnShape has also interesting top-down design capabilities but these require a better, more detailed description that probably deserve a specific post.


### Reference frames

Reference frames have an equivalent in [OnShape's mate connectors][onshape-mate-connector]. The mate connector feature allows to snap "reference frames" on relevant part geometries thus facilitating the creation of assemblies with kinematic constraints. Unfortunately OnShape currently misses the capability of computing the transformation matrix between mate references, which makes it inconvenient for analyzing multi-body robotic systems.

<div align="center"><img src='creo-onshape-csys.svg'/></div>

### Part variables

Part parameters and variable can be added via the ["part variable" functionality][onshape-part-variables].
I find OnShape superior to Creo Parametric in this functionality because these meta-data are shown directly in the model tree, thus making it more explicit for people viewing models that design intent was added to the part.

<div align="center"><img src='creo-onshape-parameters.svg'></div>


### Bill of materials

Creo Parametric allows the creation of custom part parameters that can easily be exported in the BOM. This functionality is also available in OnShape but not as part of the free subscription program. The functionality is activated within the [openBoM app][openbom-website] and (see this [video][onshape-custom-properties-video]). Differently from Creo Parametric OnShape integrates database functionalities and therefore has a slightly different way of assigning parameters to parts and assemblies. At a first glance OnShape's philosophy looks better integrated and more coherent overall.

<div align="center"><img src='creo-onshape-bom.svg'/></div>

### Part Studios

In Creo Parametric there is a one-to-one mapping between parts and files: every part has corresponds a `.prt` part file.

OnShape took the concept of part modeling a bit further with the Part Studio environment, that allows to create multiple parts within a single part document.

<div align="center"><img src='creo-onshape-part-studio.svg'/></div>
The advantage of this is that it becomes very quick to refer to geometries present in a given Part Studio, and to add design intent to multiple parts without needing to introduce complex dependencies.
This approach greatly accelerates the creation of parts which mate together.

However another consequence of this is that Part Studios effectively become "mini-assemblies" and that the distinction between parts and assemblies suddenly blurs. It thus becomes ambiguous for the designer when to choose to use part studios or when to use assemblies.

Finally a nice feature of OnShape is that in Part Studio mode, colours are automatically assigned to the parts which results in a save of time, and designs that are more "readable".


## Final comments

My personal impression on Creo Parametric vs. OnShape is that Creo Parametric is still slightly better than OnShape for large, complex projects.
OnShape has a few minor flaws, but introduced interesting modeling features (such as Part Studios), and an integrated versioning system.
It is an exiting time: as more and more people start to use OnShape I imagine most of its minor flaws will be fixed making it an extremely effective tool for solid modeling.


## References

[onshape-part-variables]: https://cad.onshape.com/help/Content/variable.htm
[onshape-mate-connector]: https://cad.onshape.com/help/Content/mateconnector.htm
[onshape-custom-properties-video]: https://www.onshape.com/videos/managing-custom-properties-06-27-17
[openbom-website]: http://www.openbom.com/
[onshape-bom-with-opnebom]: https://www.onshape.com/cad-blog/creating-a-bill-of-materials-using-openbom

- [OnShape part variables][onshape-part-variables]
- [OnShape mate connectors][onshape-mate-connector]
- [openBoM website][openbom-website]
- [Creating a BOM in OnShape with openBoM][onshape-bom-with-opnebom]
- [Adding custom properties to parts][onshape-custom-properties-video]
