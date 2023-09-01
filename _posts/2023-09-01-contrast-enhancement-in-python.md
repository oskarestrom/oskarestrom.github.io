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

## Tutorial - Contrast Enhancement for Images in Python

To follow this tutorial in python, you need to install the following packages:
```
- pip install numpy >= 1.19, < 2
- pip install matplotlib >= 3.5.2, < 4
- pip install scikit-image > 0.19.2, < 1
- pip install tifffile > 2021.7.2
```

```python
import os
import numpy as np
import matplotlib.pyplot as plt
from skimage import exposure
import tifffile

#Set the path to the tif file
base_path = r'C:\Users\os4875st\Dropbox\PhD Tegenfeldt\.py\waves projects_shared\mp4_video_generation'
file_path = os.path.join(base_path,r'raw.tif')# Org path : E:\DNADLD_2022\T4_2022-06-15_2,3nguL\5mbar\100x_5mbar_out_013.nd2

#Read tif file

img = tifffile.imread(file_path)

#Show image
fig, ax = plt.subplots(figsize=(5,5))
ax.axis('off')
ax.imshow(img, cmap='gray') 
plt.title('Raw image')
plt.show()
```
<img src="/assets/img/image-optimization/raw_img.png" width="150">
```python
#Histogram
fontsize = 15
fig, ax = plt.subplots(figsize=(5,2))
I = img.ravel()
I = I[I != 0] 
plt.hist(I,bins=256, color='k', range=(0,1.5*2**16))
plt.title(f'Histogram\nRaw Image', fontsize=fontsize)
plt.xlabel('pixel value')
plt.ylabel('count')  
plt.show()
```
<img src="/assets/img/image-optimization/raw_histogram.png" width="150">

```python
#Select the percentile values to use for the limits
min = 10 #
max = 99 #99.9
min_val = np.percentile(img,min) #Returns the 10-th percentile of the array elements.
max_val = np.percentile(img,max) #Returns the 99-th percentile of the array elements.

#Show limits on the raw image histogram
fontsize = 15
fig, ax = plt.subplots(figsize=(5,2))
I = img.ravel()
I = I[I != 0] 
plt.hist(I,bins=256, color='k', range=(0,1.5*2**16))
plt.title(f'Histogram\nRaw Image', fontsize=fontsize)
plt.xlabel('pixel value')
plt.ylabel('count')  
plt.axvline(min_val, color='r', linestyle='dashed', linewidth=1, label=f'{min}th percentile')
plt.axvline(max_val, color='b', linestyle='dashed', linewidth=1, label=f'{max}th percentile')
plt.legend()
plt.show()
```
<img src="/assets/img/image-optimization/raw_histogram_with_lines.png" width="500">

```python
img_perc = exposure.rescale_intensity(img.copy(), in_range=(min_val, max_val), out_range='uint8')

#Show image
fig, ax = plt.subplots(figsize=(5,5))
ax.axis('off')
ax.imshow(img_perc, cmap='gray') 
plt.title('Contrast-enhanced image')
plt.show()
```
<img src="/assets/img/image-optimization/2_contrast_image.png" width="150">

```python
# Histogram
fontsize = 15
fig, ax = plt.subplots(figsize=(5,2))
I = img_perc.ravel()
I = I[I != 0] 
plt.hist(I,bins=256, color='k', range=(0,255))
plt.title(f'Histogram\nContrast-enhanced image', fontsize=fontsize)
plt.xlabel('pixel value')
plt.ylabel('count')  
plt.show()
```

<img src="/assets/img/image-optimization/2_contrast_histogram.png" width="150">

```python
#Select the pixel values to use for the limits
min_val = 20000
max_val = 30000

#Show limits on the raw image histogram
fontsize = 15
fig, ax = plt.subplots(figsize=(5,2))
I = img.ravel()
I = I[I != 0] 
plt.hist(I,bins=256, color='k', range=(0,1.5*2**16))
plt.title(f'Histogram\nRaw Image', fontsize=fontsize)
plt.xlabel('pixel value')
plt.ylabel('count')  
plt.axvline(min_val, color='r', linestyle='dashed', linewidth=1, label=f'{min_val}, min limit')
plt.axvline(max_val, color='b', linestyle='dashed', linewidth=1, label=f'{max_val}, max limit')
plt.legend()
plt.show()
```
<img src="/assets/img/image-optimization/2_contrast_histogram_lines.png" width="500">

```python
img_lims = exposure.rescale_intensity(img.copy(), in_range=(min_val, max_val), out_range='uint8')

#Show image
fig, ax = plt.subplots(figsize=(5,5))
ax.axis('off')
ax.imshow(img_lims, cmap='gray') 
plt.title('Contrast-enhanced image 2')
plt.show()
```

<img src="/assets/img/image-optimization/3_contrast_image.png" width="150">

```python
#Histogram
fontsize = 15
fig, ax = plt.subplots(figsize=(5,2))
I = img_lims.ravel()
I = I[I != 0] 
plt.hist(I,bins=256, color='k', range=(0,255))
plt.title(f'Histogram\nContrast-enhanced image 2', fontsize=fontsize)
plt.xlabel('pixel value')
plt.ylabel('count')  
plt.show()
```
<img src="/assets/img/image-optimization/3_contrast_histogram.png" width="500">
