---
layout: post
title: "In search of the nicest colormap"
subtitle: "Pretty, colorful, useful, versatile, perceptually uniform, ..."
date: 2021-07-03 09:24:00 +0200
tags: [Random thoughts]
background: '/img/posts/marc-schulte-KJCyvlA_aAQ-unsplash.jpg'
published: true
use_math: true
---

<!-- https://unsplash.com/photos/KJCyvlA_aAQ -->
<!-- https://unsplash.com/photos/mz471WAXhCU -->

I've always been quite fond of the colors used in the spectral frequency display of [Adobe Audition](https://www.adobe.com/se/products/audition.html). It looks quite pretty and the colors are also very helpful in discerning small differences in intensity. 

<img class="img-fluid" src="/img/posts/audition.jpg" alt="Screenshot">

Recently, I came across a fascinating presentation about the work behind some new colormaps for [Matplotlib](https://matplotlib.org/). They set out to develop some colormaps that are colorful, pretty, sequential, perceptually uniform, black-and-white compatible and accessible to colorblind viewers. The video also includes a fascinating crash course in color theory. Highly recommended.

<!-- https://www.w3schools.com/howto/howto_css_responsive_iframes.asp -->
<div style="position:relative;overflow:hidden;width:100%;padding-top:56.25%;">
<iframe style="position:absolute;top:0;left:0;bottom:0;right:0;width:100%;height:100%;" src="https://www.youtube.com/embed/xAoljeRJ3lU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

The colormaps magma, inferno, plasma and viridis and the tools [colorspacious](https://pypi.org/project/colorspacious/) and [viscm](https://pypi.org/project/viscm/) that they developed are described [here](https://bids.github.io/colormap/) and [here](https://github.com/bids/colormap). These colormaps, now included beside many others in [Matplotlib](https://matplotlib.org/stable/tutorials/colors/colormaps.html), are visualized below.

```
python -m viscm view magma --save magma.png --quit --uniform-space buggy-CAM02-UCS
```
<img class="img-fluid" src="/img/posts/magma.png" alt="Screenshot">

```
python -m viscm view inferno --save inferno.png --quit --uniform-space buggy-CAM02-UCS
```
<img class="img-fluid" src="/img/posts/inferno.png" alt="Screenshot">

```
python -m viscm view plasma --save plasma.png --quit --uniform-space buggy-CAM02-UCS
```
<img class="img-fluid" src="/img/posts/plasma.png" alt="Screenshot">

```
python -m viscm view viridis --save viridis.png --quit --uniform-space buggy-CAM02-UCS
```
<img class="img-fluid" src="/img/posts/viridis.png" alt="Screenshot">

I also found some quite pretty colormaps in the [cmocean](https://matplotlib.org/cmocean/) package, such as [thermal](https://matplotlib.org/cmocean/#thermal) and [ice](https://matplotlib.org/cmocean/#ice).

```python
from viscm import viscm
import cmocean
viscm(cmocean.cm.thermal)
```
<img class="img-fluid" src="/img/posts/thermal.png" alt="Screenshot">

```python
from viscm import viscm
import cmocean
viscm(cmocean.cm.ice)
```
<img class="img-fluid" src="/img/posts/ice.png" alt="Screenshot">

Returning to the colors used in the spectral frequency display of Adobe Audition, I wanted to evaluate this colormap in the same tool as above. So I made a sine wave at 1125 Hz so that it would align nicely with one of the center frequencies of the FFT. I then applied an exponential decay from 0 dBFS to -150 dBFS to capture the full range of the colormap. A screenshot of a zoom-in of this frequency looks like this.

<img class="img-fluid" src="/img/posts/audition-crop.jpg" alt="Screenshot">

Running viscm on one of the horizontal lines in the middle of this yields the following.

<img class="img-fluid" src="/img/posts/audition-viscm.png" alt="Screenshot">

Perhaps this colormap is pretty, but maybe not really as good as I thought it was. I did use an older version of Adobe Audition so perhaps newer versions use a more perceptually uniform colormap.

I also own a copy of [iZotope RX 7](https://www.izotope.com/en/products/rx.html) and applying a similar analysis on the colormap used in this software yields the following.

<img class="img-fluid" src="/img/posts/rx7-viscm.png" alt="Screenshot">

A colormap that looks similar to the one in Adobe Audition, but a little different and I guess a little better, is the one used at [https://src.infinitewave.ca/](https://src.infinitewave.ca/). (This site I highly recommend for their many comparisons of sample rate converters.)

<img class="img-fluid" src="/img/posts/src.infinitewave.ca.png" alt="Screenshot">

Finally, another colormap similar to both the one in Adobe Audition and the one used at [https://src.infinitewave.ca/](https://src.infinitewave.ca/) is the main one used by [SoX - Sound eXchange](http://sox.sourceforge.net/). It is described in the [source code](https://sourceforge.net/p/sox/code/ci/master/tree/src/spectrogram.c#l648) as well as below.

<!-- https://benlansdell.github.io/computing/mathjax/, but needed to swap single with double dollar signs in the header, as double double dollar signs did not work well. -->
<!-- https://www.onemathematicalcat.org/MathJaxDocumentation/TeXSyntax.htm -->
<!-- http://docs.mathjax.org/en/latest/index.html -->
<!-- https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference -->
$
R = 
\cases{
0  & \text{if } \quad 0.00 \le x \lt 0.13 \cr
\sin \left( { {x - 0.13} \over 0.60 }{ \pi \over 2 } \right)  & \text{if } \quad 0.13 \le x \lt 0.73 \cr
1 & \text{if } \quad 0.73 \le x \le 1.00
}
$

$
G = 
\cases{
0  & \text{if } \quad 0.00 \le x \lt 0.60 \cr
\sin \left( { {x - 0.60} \over 0.31 }{ \pi \over 2 } \right)  & \text{if } \quad 0.60 \le x \lt 0.91 \cr
1 & \text{if } \quad 0.91 \le x \le 1.00
}
$

$
B = 
\cases{
{1 \over 2} \sin \left( { x \over 0.60 } \pi \right) \ \ &  \text{if } \quad 0.00 \le x \lt 0.60 \cr
0 & \text{if } \quad 0.60 \le x \lt 0.78 \cr
{x - 0.78} \over 0.22 & \text{if } \quad 0.78 \le x \le 1.00
}
$

where $R$, $G$ and $B$ are the intensities of the colors red, green and blue and $0 \le x \le 1$ is the position on the colormap.

<img class="img-fluid" src="/img/posts/sox.png" alt="Screenshot">

In finding the right colormap to use for a project, there is also the option of designing your own brand new colormap. This can be done though viscm like this, which opens up a user friendly editor.
```
python -m viscm edit
```
<img class="img-fluid" src="/img/posts/viscm-editor.png" alt="Screenshot">

The search continues... :telescope: :smiley:
