---
layout: post
title: Downsample and crop a video using ffmpeg from Python
tags: [python, ffmpeg]
comments: true
---

Batch edition of videos in Linux is straightforward, using `ffmpeg` and a for loop in a shell script. Here I show how to call `ffmpeg` from Python using the `subprocess` module. I found this useful for downsampling and cropping videos for other tasks (in my case, the original videos were too heavy to process them, and I was just interested in some portion of them).

Here is a Python function to do that. 

```python
from pathlib import Path
import subprocess, os
import cv2


def CropVideo(vname, out_w, out_h, x1, y1, out_path=None):
    """
    vname: file name of the input video
    out_w: desired output width
    out_h: desired output heigth 
    x: initial x position of the cropping area
    y: initial y position of the cropping area. Beware that the width 
    and height define the lengths of a rectangle, so it's 
    necessary to specify the initial x1 and y1 positions from which the lengths
    will be taken    
    out_path: path for the output video 
    """
    # Check if there is path for the out file
    if out_path is None:
        vid_path = os.path.dirname(vname)
        out_suffix = 'd'
    else:
        out_suffix = '' 
        vid_path = out_path

    new_filename = os.path.join(vid_path, str(Path(vname).stem) + str(out_suffix) + str(Path(vname).suffix))
    print("Down and cropped video...", new_filename)
    command = f"ffmpeg -i {vname} -filter:v 'crop={out_w}:{out_h}:{x1}:{y1}' {new_filename}"
    subprocess.call(command, shell=True)
    


```

