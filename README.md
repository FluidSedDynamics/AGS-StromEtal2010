# AGS-StromEtal2010
**Overview:** This repository contains an ImageJ macro with sample images that can be used to get familiar with the processing procedures outlined in Strom et al. (2010)

## Why use image processing to size river gravel?

Studies in the fluvial environment often require characterization of the bed material grain-size distribution for purposes such as obtaining roughness length-scale estimates, sediment transport calculations, geomorphic/aquatic habitat classification, and general monitoring. Surface layer sediments in gravel bed rivers are often characterized with pebble counts which require an operator to select and physically measure the axes of the individual grains or characterize them with a sizing template. In recent years, image analysis procedures have been used to automatically extract grain-size information from digital images of sediment beds. This method has the advantage of significantly reducing field time for sampling, sampling the bed sediments non-intrusively, and obtaining samples over a smaller sampling footprint to keep from blending spatial heterogeneity; the major drawback to the method is that it can only measure the size of the particles as-they-lie in the image. Our research focuses on 1) optimizing standard image processing procedures to best measure the particles as-they-lie in the image, and 2) comparing grain size distributions obtained with different pebble count methods and the automated image processing method.
![Gravel bed][image-1]{:style="float: right;margin-right: 7px;margin-top: 7px;"}

## The ImageJ macro

### Overview

`AIGS_ImageJ_macro.txt` is an ImageJ macro that steps through the image processing functions outlined in Strom et al. (2001). The macro starts with a cropped RGB image and returns the measured particles sizes in pixels along with an image showing the identified particles. The macro is designed to apply identical image processing functions to all images located in a source directory.

The macro assumes that everything in the image should be measured and treated as a particle. Therefore, if there are unwanted objects in the original image (such as scales, boot toes, vegetation, etc.), these should be cropped out of the image before running the macro. The macro will ask for the radius (in pixels) for the median filter and the size of the rolling-ball radius in pixels for the background subtraction function. It is advised that a representative image be used first to identify good filter and rolling-ball radius sizes. This will be a function of the number of pixels in the smallest particle you wish to identify. Default values for these two parameters are set to 5 and 15 respectively for the median and rolling-ball radii based on the experiments of Strom et al. (2010); 5 and 15 pixels were approximately 0.25 and 0.75 times the d5 of the material in Strom et al. (2010). However, these values are not generalized values and it is recommended that the operator find values which work best for properly identifying grains in their particular application.

### Step-by-step instructions for use

1. Group all cropped images that you would like to process with the same median filter and rolling-ball radius together in a single folder.
2. Create an output folder to store the results.
3. From within ImageJ run the macro following these steps
	- open the macro using command-o
	-  run the macro using command-r
	- select the source directory within the popup dialog
	- select the output directory within the popup dialog
	- enter the radius for the median filter (default is 5 pixels)
	- enter the radius for the rolling-ball in the background subtraction function (default is 15 pixels)

The macro will then perform the series of operations on all images stored in the source directory and will store text files of particle size information (in pixels) in the destination directory along with images of the identified particles. The data from each image can then be translated from pixels to some physical length using the know pixel-to-physical length ratio. The data can then used to compute various grain size information. Note that numerical sieving of the output yields areal, frequency-by-number grain-size distributions.

The steps followed in the macro are based on those outlined and used in: Strom, K. B., Kuhns, R. D., & Lucas, H. J. (2010). Comparison of Automated Image-Based Grain Sizing to Standard Pebble-Count Methods. Journal of Hydraulic Engineering, 136(8), 461-473.

[image-1]:	https://github.com/FluidSedDynamics/AGS-StromEtal2010/blob/master/GravelBedSample.jpg
