---
title: Contrast-enhancement in Python
date: 2023-09-01 10:00:00 +0200
categories: [Research]
tags: [coding, python, image processing]     # TAG names should always be lowercase
---
# Image Quality
How can we, working in Python, improve the visual quality of microscopy images in our scientific papers?

In MATLAB, there are [lots of tools](https://www.mathworks.com/help/images/contrast-adjustment.html) to do this very easily.
I have not found any analogous libraries in Python. What I have been using is [exposure.rescale_intensity function](https://scikit-image.org/docs/stable/api/skimage.exposure.html#skimage.exposure.rescale_intensity) of the library [sci-kit image](https://scikit-image.org/). skimage.exposure.rescale_intensity rescales the input image and thus changes the values of the python array. This is unlike the MATLAB functions that just changes the visual presentation when displaying the image arrays. The actual array values are preserved. However, I have found that the exposure.rescale_intensity works as well as the MATLAB ones when you have adjusted yourself to the new mode of operation.

Let us show this function is action.