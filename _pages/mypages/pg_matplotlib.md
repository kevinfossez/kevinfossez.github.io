---
layout: archive
permalink: misc/matplotlib/
title: How-to matplotlib
description: Last update on March 12, 2021
---


## header

```python
#!/usr/bin/python

import matplotlib
import matplotlib.style
import matplotlib as mpl


mpl.rcParams.update({
    "text.usetex": True,
    "text.latex.preamble": r"\usepackage{amsmath}", 
    "font.size": 20, 
    "font.family": "serif", 
    "font.serif": "Computer Modern Roman", 
    "xtick.labelsize": 16, 
    "ytick.labelsize": 16, 
    "legend.fontsize": 20, 
    "axes.labelsize": 20, 
    "font.weight": 1000})

from matplotlib.pyplot import figure , axes , plot , xlabel , ylabel , title , grid , savefig , show
import numpy as np
from pylab import *

import matplotlib.pyplot as plt
from matplotlib.pyplot import axhline

from matplotlib.gridspec import GridSpec
import matplotlib.gridspec as gridspec

import matplotlib.patches as mpatches
```

## colors

```python
# tableau 20
colors_t20 = [(31, 119, 180), (174, 199, 232), (255, 127, 14), (255, 187, 120), (44, 160, 44), (152, 223, 138), (214, 39, 40), (255, 152, 150), (148, 103, 189), (197, 176, 213), 
              (140, 86, 75), (196, 156, 148), (227, 119, 194), (247, 182, 210), (127, 127, 127), (199, 199, 199), (188, 189, 34), (219, 219, 141), (23, 190, 207), (158, 218, 229)]

# tableau 10 colorblind
colors_t10cb = [(0, 107, 164), ( 255, 128, 14), (171, 171, 171), (89, 89, 89), (95, 158, 209), (200, 82, 0), (137, 137, 137), (162, 200, 236), (255, 188, 121), (207, 207, 207)]

# tableau 10: full, medium, light
# 0:bleu, 1:orange, 2:vert, 3:rouge, 4:violet, 5:brown, 6:rose, 7:gris, 8: jaune/vert, 9:bleu ciel
colors_t10 = [(31, 119, 180), (255, 127, 14), (44, 160, 44), (214, 39, 40), (148, 103, 189), (140, 86, 75), (227, 119, 194), (127, 127, 127), (188, 189, 34), (23, 190, 207)]
colors_t10l = [(174, 199, 232), (255, 187, 120), (152, 223, 138), (255, 152, 150), (197, 176, 213), (196, 156, 148), (247, 182, 210), (199, 199, 199), (219, 219, 141), (158, 218, 229)]
colors_t10m = [(114, 158, 206), (255, 158, 74), (103, 191, 92), (237, 102, 93), (173, 139, 201), (168, 120, 110), (237, 151, 202), (162, 162, 162), (205, 204, 93), (109, 204, 218)]


def get_colors_rgb(colors):
    for i in range(len(colors)):
        r, g, b = colors[i]    
        colors[i] = (r/255., g/255., b/255.) 
    return colors

def get_color_shade_rgb(color, nshades):
    nshades = nshades
    r, g, b = color    
    colors=[0]*nshades
    for i in range(nshades):
        factor=(1.0*(i+1))/nshades
        colors[i] = (factor*r, factor*g, factor*b) 

    #colors.reverse ()
    return colors

def get_color_tints_rgb(color, ntints):
    ntints = ntints
    r, g, b = color    
    colors=[0]*ntints
    for i in range(ntints):
        factor=(1.0*(i+1))/ntints
        colors[i] = (r + factor*(255.0-r*255.0)/255.0, g + factor*(255.0-g*255.0)/255.0, b + factor*(255.0-b*255.0)/255.0) 

    return colors
```
