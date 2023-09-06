---
title: My Python Packages - an Overview
date: 2023-09-06 15:00:00 +0200
categories: [Research]
tags: [coding, python, image processing]     # TAG names should always be lowercase
---

Here is a list of all python packages I have made.

## Automatic Calculation of Ionic Strength and pH of Tris-EDTA solutions.
That is, you choose which concentrations of TE (and BME) you want to calculate the ionic strength and pH of. The script will create a csv file for you with the output.

[https://github.com/oskarestrom/ionic_strength_calc_of_tris_edta_sol](https://github.com/oskarestrom/ionic_strength_calc_of_tris_edta_sol)

## Easy loading and metadata extraction of nd2-files
It is very difficult to work with nd2-files with python. The normal packages (numpy, opencv, pillow etc...) cannot handle nd2. Therefore I made a package that can easily load nd2-files and extract their metadata into objects and spreadsheets.

[https://github.com/oskarestrom/nd2handling](https://github.com/oskarestrom/nd2handling)

## Generation of publication-ready videos
It is very difficult to convert a numpy array to a playable video file. To my knowledge, there are no libraries that can do this easily. I therefore made one. This package can also add scalebars, timestamps and text on-top of the videos. It is also very easy to compress the video in several ways to limit the file size.

[https://github.com/oskarestrom/mp4_video_generation](https://github.com/oskarestrom/mp4_video_generation)

## Calculation of DNA polymer dynamics variables
This package can calculate the relevant lengths, radii of gyration and overlap concentrations for a DNA solution with a certain DNA length and salt concentration. Very useful if you work with DNA physics.

[https://github.com/oskarestrom/polymer_dynamics](https://github.com/oskarestrom/polymer_dynamics)

## Fourier Transforms and Spectra Plotting
To extract frequency information (both temporal and spatial) from images you can calculate their Fourier Transforms. While the transform functions already exists, it can be tricky to plot the results. This package does this in a neat way for both 1D and 2D transforms. It deemed very useful in my articles about DNA waves ([paper 1](https://pubs.rsc.org/en/content/articlehtml/2023/lc/d2lc01051h), [paper 2](https://arxiv.org/abs/2212.11802))

[https://github.com/oskarestrom/DNA_waves_FFT](https://github.com/oskarestrom/DNA_waves_FFT)