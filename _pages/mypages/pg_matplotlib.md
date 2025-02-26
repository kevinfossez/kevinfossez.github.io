---
layout: archive
permalink: misc/matplotlib/
title: How-to matplotlib
description: Last update on March 12, 2021
---


## Setting text on the figure

```python
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
```

## Colors

```python
# tableau 20
colors_t20 = [(31, 119, 180), (174, 199, 232), (255, 127, 14), (255, 187, 120), (44, 160, 44), (152, 223, 138), (214, 39, 40), (255, 152, 150), (148, 103, 189), (197, 176, 213), 
              (140, 86, 75), (196, 156, 148), (227, 119, 194), (247, 182, 210), (127, 127, 127), (199, 199, 199), (188, 189, 34), (219, 219, 141), (23, 190, 207), (158, 218, 229)]

# tableau 10 colorblind
colors_t10cb = [(0, 107, 164), ( 255, 128, 14), (171, 171, 171), (89, 89, 89), (95, 158, 209), (200, 82, 0), (137, 137, 137), (162, 200, 236), (255, 188, 121), (207, 207, 207)]

# tableau 10: full, medium, light
# 0:blue, 1:orange, 2:green, 3:red, 4:purple, 5:brown, 6:pink, 7:gray, 8: yellow/green, 9:light blue
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

## Setting figure size and dpi

```python
# The column width in PRC is about 6 cm, and the recommended dpi is 1200
fig = plt.figure (figsize = (6,4), dpi=1200)
```

## Setting grid for one or multiple plots

```python
# 3 lines * 2 columns grid
gs = GridSpec(3, 2)
gs.update(wspace=0.1, hspace=0.2)

# select the whole figure (multiple plots)
ax = fig.add_subplot (gs[:,:])

# select one subplot
ax0 = fig.add_subplot(gs[0])

# select a row or line of subplots
ax1 = fig.add_subplot(gs[1,:])
```

## Remove axes and ticks

```python
ax.spines['top'].set_color('none')
ax.spines['bottom'].set_color('none')
ax.spines['left'].set_color('none')
ax.spines['right'].set_color('none')

ax.tick_params(labelcolor='w', top='off', bottom='off', left='off', right='off')
ax.tick_params(top='off', bottom='off', right='off')
ax.tick_params(axis='x', colors='white')
ax.tick_params(axis='y', colors='black')
```

## Set labels

```python
ax0.set_xlabel (r"$ r \, (\text{fm}) $" , fontsize=20)
ax0.set_ylabel (r"$ E \, (\mathrm{MeV}) $" , fontsize=20)
ax0.xaxis.set_label_position('top') 
ax0.yaxis.labelpad = 12
```

```python
ax0.set_xlim([0.0,3.0])
ax0.set_ylim([0.0,3.0])
ax0.invert_xaxis()
```

## Set ticks and ticklabels

```python
ax0.tick_params(axis='x', labelsize=25)
ax0.set_xticks ([0.0, 1.0, 2.0])
ax0.set_xticklabels ([r"$a$", r"${ \sfrac{1}{2} }$", r"${ {10}^{\text{-}10} }$", r"$c$F"])
```

# Legend

```python
# automatic
ax0.legend(loc='upper right', ncol=1, numpoints=1, frameon=False, columnspacing=0.8, handletextpad=0.3, fontsize=10)

# by hand
lg0 = mpatches.Patch(color="black", label="Exp")
lg1 = mpatches.Patch(color="blue", label="Model A")
lg2 = mpatches.Patch(color="red", label="Model B")
ax0.legend(handles=[lg0,lg1,lg2], loc='upper right', ncol=1, numpoints=1, frameon=False, columnspacing=0.8, handletextpad=0.3, fontsize=10)
```


## vlines and hlines

```python
ax0.axhline (y=0.0 , linewidth=1.0 , color='black' , linestyle='dotted')
ax0.vlines(13.5, -20.0, -13.0, colors="black", linestyles=":", label='')
```

## Arrows

```python
ax0.arrow(xmin, ymin, 0, ymax-ymin, fc='k', ec='k', lw=1.5, 
        head_width=0.1, head_length=0.1, overhang=0.3, 
```

## Annotations

```python
# At the very end, just before saving the figure
matplotlib.rc ('text', usetex=True)
ax0.annotate(r"$2^+$", xy=(17.0,4.0), color='black', ha="left", va="center", fontsize=10)
```

## Save figure
```python
fig.savefig('plot.pdf', bbox_inches='tight', transparent=True)
```

