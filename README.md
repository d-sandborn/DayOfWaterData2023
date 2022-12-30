#Day of *Water* Data 2023

*Resources for participants in the University of Minnesota Day of Data 2023.*
*Created by Daniel E. Sandborn.*

> This matrial accompanies a talk delivered by the author at the UMN Day of Data event in January 2023.  To run the code detailed below, you have at least two options: 1. Cut-and-paste code snippets into a Python terminal of choice.  This may take the form of Spyder, Jupyter, IDLE, etc. 2. Download and run the Jupyter Notebook available (here)[link].

##Introduction to Lake and Ocean Observation Systems

Observers of lakes and oceans have a choice of many instruments and strategies, including moored instruments (buoys), research cruises, drifting buoys, autonomous profilers, and more.  Different phenomena exist on different scales, with temporal variability between seconds and millennia, and spatial variability between millimeters and thousands of kilometers.  

To observe a process, you have to match your observation strategy to phenomena of interest.

```python
# We begin by importing packages we'll need
import pandas as pd  # for matrix manipulation
import numpy as np  # general-use numerical functions
from erddapy import ERDDAP  # for accessing buoy data directly
import geopandas as gp  # mapping toolkit
from PIL import Image, ImageDraw  # image I/O functions
import matplotlib.pyplot as plt  # highly-flexible graphing package
from scipy import optimize  # curve-fitting toolkit

# Import variability plot; Bushinsky et al. 2019
varplot = Image.open('ObsVarPlot.JPG')
# Print variability plot
fig, ax = plt.subplots(figsize=(20, 16))
ax.imshow(varplot)
plt.axis('off')

```
![Observation Variability Plot, Bushinsky et al. 2019](ObsVarPlot.jpg "Observation Variability Plot, Bushinsky et al. 2019")

Plotting spatial variability on one axis and temporal variability on 
the other illustrates the overlap among various ocean phenomena and observation techniques.  

##Climate, Weather, and the Laurentian Great Lakes

The Laurentian Great Lakes contain ##% of the Earth's surface freshwater despite 
occupying only ##% of the Earth's surface.  

They influence regional climate and weather over a large portion of North America, as 
evidenced by, for example, cooler temperatures near the lakes in summer, and 
lake effect snowfall in early winter.  

Recent research has highlighted the ways in which we are modifying the physical, 
chemical, and biological states of the Great Lakes.  

**Our lakes are getting warmer** (Austin and Coleman, 2008)

**Our lakes are experiencing unprecedented harmful algal blooms** (Sterner et al. 2020)

**Our lakes (especially the more poorly-buffered lakes like Superior) may be acidifying** (Sandborn and Minor, 2022; after Phillips et al. 2015)

This research, as well as management and policy decisions that can help mitigate
harmful changes, rely upon observations spanning minutes to centuries, and creeks 
to continents. 