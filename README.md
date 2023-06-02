<!-- badges: start -->

[![R-CMD-check](https://github.com/mpio-be/colorZapper/workflows/R-CMD-check/badge.svg)](https://github.com/mpio-be/colorZapper/actions)


<!-- badges: end -->



colorZapper
===========
Extract colour from user defined areas.

```R
remotes::install_github("kmira25/colorZapper")
```

```R
require(colorZapper)
# path to image directory
dir = system.file(package = "colorZapper", "sample")
# open/create a colorZapper file
cz_file = tempfile(fileext = '.sqlite')
CZopen(path = cz_file)
# associate files with the opened file
CZaddFiles(dir)
```

Interactively define points or polygons
```R

# define 1 point per image
CZdefine(points = 1)

# check status
CZshowStatus()

# over-write points defined for Falco_peregrinus (id = 2)
CZdefine(points = 1, what  = 2)
CZshowStatus()
# define points using marks
# 2 points per mark = 4 points per image
# 'what' is set so only particular images are going to be loaded
CZdefine(points = 1, marks = c("wing", "tail") , what = 4)
CZshowStatus()

#define polygons: 1 polygon per mark
# see help(locator) for info on how to draw on an R graphic. 
CZdefine(polygons = 1, marks = c("wing", "tail"), what = 3 )
```

Extract RGB values from Regions of Interest
```R
CZextractROI()

# fetch data
d = CZdata(what = 'ROI')

```

Extract RGB values from the entire image (batch mode).
```R
CZextractALL()
d = CZdata(what = 'ALL')
```

### Points to remember:
* CZ works better outside Rstudio so just run it from a plain R console. 
* Data are saved to a database file on your disk so you can stop and resume your work any time. 













