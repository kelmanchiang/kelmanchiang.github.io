---
layout: post
title: Multi-scale Hexagons
---

[https://github.com/kelmanchiang/multiscale-hexagons](https://github.com/kelmanchiang/multiscale-hexagons)

#### Challenge
Frustrated at existing open source solutions ([Uber's H3](https://uber.github.io/h3/#/), [Google's S2](http://s2geometry.io/)), I decided to code out my own Python script to generate multi-scale, tessellating hexagons. 

I needed a simple shapefile of hexagons, that tesselate neatly along its vertices/edges, and in multiple sizes so that my scale of analyses could be drilled up or down as required.

In my case, I wanted them in shapefiles so that I could load it into Tableau, QGIS and PostGIS databases as a base spatial dataset further analyses with other datasets.

#### Method
When I was writing the code, I didn't foresee myself having to run this code frequently, and likely only needing to produce them for small areas, like cities. I chose a projected coordinate system, as I needed the units of the hexagon sizes to be understandable by the end user, and went for a UTM-based one so that it can be replicable worldwide.

#### Results
<img src="assets/multiscale_hexagons.png" alt="Much Blue" width="80%" align="middle"/>

#### Limitations
Due to the choice of the projection coordinate system, distortion would occur if UTM zones are crossed. Larger hexagon sizes would suffer greater distortion.
