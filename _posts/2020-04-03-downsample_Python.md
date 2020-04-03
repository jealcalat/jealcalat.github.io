---
layout: post
title: Downsample and crop a video using ffmpeg from Python
tags: [python, ffmpeg]
comments: true
---

Batch edition of videos in Linux is straightforward, using `ffmpeg` and a for loop in a shell script. Here I show how to call `ffmpeg` from Python using the `subprocess` module. I found this useful for downsampling, reduce the length and cropping videos for other tasks (in my case, the original videos were too heavy to process them for further analysis using [DeepLabCut](<http://www.mousemotorlab.org/deeplabcut>), and I was just interested in some portion of them).

Here is a Python function to do that. 

```python
from pathlib import Path
import subprocess, os
import cv2


def CropThenDownSample(vname, out_w, out_h, x, y, start, end,
                       width=300, height=-2, out_path=None):
    """
    vname: file name of the input video
    out_w: desired output width
    out_h: desired output heigth 
    x: initial x position of the cropping area
    y: initial y position of the cropping area. Beware that the width 
    and height define the lengths of a rectangle, so it's 
    necessary to specify the initial x1 and y1 positions from which the lengths
    will be taken
    start: desired start of output video
    width: resolution width, 300 px by default
    height: resolution height, integer -2 is for rescaling h to keep constant ratio
    out_path: path for the output video 
    """
    # Check if there is path for the out file
    if out_path is None:
        vidpath = os.path.dirname(vname)
        outsuffix = 'd'
    else:
        outsuffix = '' 
        vidpath = out_path

    new_file = os.path.join(vidpath, str(Path(vname).stem) + str(outsuffix) + str(Path(vname).suffix))
    
    # -i for input, -ss for specify the start in seconds (e.g., 10), -filter:v is 
    # for pipeline effects in ffmpeg, in this case crop=<options>,scale=<options>
    # filters must be separated by a coma. vname and new_file will be printed in 
    # quotes for avoiding errors due to unexpected spaces in the filenames

    command = f'ffmpeg -i "{vname}" -ss {start} -filter:v crop={out_w}:{out_h}:{x}:{y},scale={width}:{height} -c:a copy -to {end} "{new_file}"'
    subprocess.call(command, shell=True)
    
    return str(f'{new_file} has been processed')


```



The important function 

```shell
command = f'ffmpeg -i "{vname}" -ss {start} -filter:v crop={out_w}:{out_h}:{x}:{y},scale={width}:{height} -c:a copy -to {end} "{new_file}"'
```

This will print something of the like:

```shell
ffmpeg -i "video 1.mp4" -ss 10 -filter:v crop=350:200:0:0,scale=300:-2 -c:a copy -to 30 "video 1d.mp4"
```

