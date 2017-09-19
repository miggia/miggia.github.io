---
layout: post
title: "A comparison of spherical bearing for compact applications"
date: "2017-08-05"
category: Mechanics
keywords: [Ball joints]
use_mathjax: false
---

A few days ago I was searching for compact spherical ball bearings for a parallel joint I and my colleagues are designing. We specifically needed something compact with a high range of motion. After a bit of searching I realized that there are not many commercial components that satisfy these requirements.

## swing angle definition

As can be seen in the figure below the maximum swing angle (indicated as $\theta$ in the image) is the maximum angle the inner sphere of the bearing can perform, before the shaft that goes through it collides with the outer bearing part.
<div align="center"><img src='{{ site.url }}/asset-bank/ball-joint.svg' height='300pt'/></div>

## standard spherical rod ends

Standard spherical rod end bearings have limited swing angles, generally in the 8° to 16° range. By carefully browsing through catalogues one can however find models with a slightly higher permissible swing angles. For example the `CM-4` general purpose rod-end by [Aurora](aurora-web) allows for a generous 27° angular displacement.  

## igus igubal

A interesting option are igus spherical bearings of the [igubal series](igubal-web).
Some of these come in shapes and sizes which allow significant maximum swing angles.

<div align="center"><img src='{{ site.url }}/asset-bank/igubal_b_50_7.jpg' height='280pt'/></div>


## Spherical rolling joints

Finally an option worth citing are the so-called ["spherical rolling joints"](srj-web) by Hephaist.

<div align="center"><img src='{{ site.url }}/asset-bank/SRJoint.jpg' height='280pt'/></div>


These components are the best option in terms of friction, but their maximum permissible swing angle is anyway limited to 30°, and they tend to be significantly more costly than previous options.

## Comparison table

Follows a table that compares small commercial spherical bearings by the most important parameters for our application.

| Cod.        | angle | outer diam. [mm] | Max. load [N] | type                             | Manufacturer |
| ---         | ---   | ---              | ---           | ---                              | ---          |
|`WGRM-05`    | 25°   | 12.8             | 100           | ![]({{ site.url }}/asset-bank/igus_igubal_wgrm_thumb.jpg)  | igus         |
|`WGRM-05 LC` | 25°   | 12.8             | 100           | ![]({{ site.url }}/asset-bank/igus_igubal_wgrm.jpg)        | igus         |
|`KBRM-02`    | 30°   | 9                | 50            | ![]({{ site.url }}/asset-bank/igus_igubal_KBM_Bild.jpg)    | igus         |
|`KBRM-03`    | 30°   | 13               | 100           | ![]({{ site.url }}/asset-bank/igus_igubal_KBM_Bild.jpg)    | igus         |
|`KBRM-06 CL` | 40°   | 20               | 150           | ![]({{ site.url }}/asset-bank/igus_igubal_KBM_CL_Bild.jpg) | igus         |
|`CM-4`       | 27°   | 19               |  10           | ![]({{ site.url }}/asset-bank/aurora_cm-bearing.jpg)       | Aurora       |
|`SRJ004C`    | 15°   | 19               |  100          | ![]({{ site.url }}/asset-bank/SRJ004.jpg)                  | Hephaist     |
|`SRJ006C`    | 30°   | 25               |  280          | ![]({{ site.url }}/asset-bank/SRJ006.jpg)                  | Hephaist     |


## References
[aurora-web]: "http://www.aurorabearing.com/pdf/aurora-bearing-610-catalog.pdf"
[igubal-web]: "http://www.igus.eu/igubal"
[srj-web]: "http://www.myostat.ca/SRJoint#"

- [igubal bushings website][igubal-web]
- [Hephaist spherical rolling joints website][srj-web]
- [Aurora spherical rod end bushings][aurora-web]
