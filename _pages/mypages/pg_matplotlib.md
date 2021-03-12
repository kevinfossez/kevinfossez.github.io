---
layout: archive
permalink: /misc/matplotlib/
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


