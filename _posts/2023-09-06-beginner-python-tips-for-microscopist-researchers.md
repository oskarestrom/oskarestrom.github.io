---
title: Beginner Python Tips for Microscopist Researchers
date: 2023-09-06 15:00:00 +0200
categories: [Research]
tags: [coding, python, image processing]     # TAG names should always be lowercase
---

### Basic Rules
- Keep your code as simple, neat and clean as possible. Your future self will thank you. Contemplate over the guidelines of the [Zen of Python](https://peps.python.org/pep-0020/).
- Make a new file for every experiment you analyze. Do not re-use the same file even if the data is almost identical. Copy the contents from the last file and modify it. You will not regret doing this. By doing this, you save all the code you have ever generated and can re-run old code. Make sure you organize your files in a clean way.

### Useful Libraries
- [numpy](https://numpy.org/) - Master this library. I promise you won't regret it. 
    - Make sure you understand the different datatypes of numpy arrays (e.g. uint8 and uint16...). Using datatypes with too high bit depth can cost you in processing power.
- [matplotlib](https://matplotlib.org/) - Master this library as well. 
    - For example, learn how to effectively apply [colormaps](https://matplotlib.org/3.1.0/tutorials/colors/colormaps.html) in matplotlib to enhance your figures.
    - If you want your plots to look the same without having to add many lines of code every time, you can use ['styles sheets'](https://matplotlib.org/stable/tutorials/introductory/customizing.html) in matplotlib. For example, if I am to publish in PNAS, I just change the style sheet to the PNAS one and all my plots will automatically be updated if I just type ```plt.style.use('PNAS') ```. It will go faster to publish and look prettier if you can keep the fonts, fontsize, figuresize, ticks and so on constant for all your figures.
- [seaborn](https://seaborn.pydata.org/) - A library based on matplotlib with which you can generate beautiful plots very easily.
- [Pillow](https://pillow.readthedocs.io/en/stable/) - Contains many useful functions for image editing.
- [opencv](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html) - Contains both simple and advanced image processing functions.
- [skimage](https://scikit-image.org/) - also contains many effective image processing functions. 
    - A great function is the exposure.rescale_intensity to adjust the brightness and contrast of images.
- [nd2reader](https://github.com/Open-Science-Tools/nd2reader) - Specialized library to read Nis-Elements '.nd2' microscopy images. Only useful if you are using the NIS-Elements microscopy software.
- [pims](https://soft-matter.github.io/pims/v0.6.1/) - Useful to read metadata from images
- [pims-nd2](https://github.com/soft-matter/pims_nd2) - A package from the PIMS infrastructure, solely dedicated to nd2-files. Again, only useful if you are using the NIS-Elements microscopy software.
- [sk-video](http://www.scikit-video.org/) - to load and generate videos
- [plotly.express](https://plotly.com/python/plotly-express/) - Makes it possible to hover over images and get real-time coordinate and pixel values. A function matlab has but python otherwise lacks.
- [tifffile](https://github.com/cgohlke/tifffile/) - A library that very quickly loads and saves TIFF-files.

Also make sure to see [the packages I have created.]({% post_url 2023-09-06-my-python-packages %}).

### Install GitHub Copilot
By installing the [GitHub Copilot](https://github.com/features/copilot), the way you code will be (forever) changed. This AI feature will suggest the next piece of code whenever you are working in a file. I find it mostly correct, sometimes yoou have to adjust minor errors. It cannot read your mind but pretty close to.

### Speed-up your coding
- Test your code of subsets of your data. I made the mistake of running my large 2 GB-files everytime I changed my code. It's better to just use 2 frames or so when you want to know if your code will work.
- Keyboard shortcuts. Learn the keyboard shortcuts of your code editor. If you don't have to drag your mouse everywhere, everything will go much faster.
- Time your functions. Find out where the bottlenecks are. I use the built-in [time.perf_counter](https://www.geeksforgeeks.org/time-perf_counter-function-in-python/) to do this.
- Automatize code that you will use many times
- I so recommend keeping bookmarks in your code editor. For Visual Studio Code I recommend the extension called [Numbered Bookmarks](https://marketplace.visualstudio.com/items?itemName=alefragnani.numbered-bookmarks)

### Share your code
I highly recommend using [Git](https://git-scm.com/) and [GitHub](https://github.com) for making your code available to others. Everyone uses it, it is easy to keep track of changes over time and it is easy to try the code yourself.

### Document your code
Use comments everywhere in your code. It might be obvious for you to understand what the function does, but not for others (or even yourself in a year's time). I also highly recommend making longer guides for using a set of functions if you have time, e.g. in [markdown files (".md")](https://www.markdownguide.org/basic-syntax/).
