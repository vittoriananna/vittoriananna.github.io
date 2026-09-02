+++
date = '2026-08-25'
draft = true
title = "Best way to generate ChimeraX movies"
tags = ["chimerax", "visualization"]
categories = ["tutorials"]
description = "A step-by-step guide to create the best movie with ChimeraX you have ever made"
+++

```chimerax
movie record format PNG directory "C:\Users\vitto\OneDrive - CNR\Conferenze e Missioni\52nd Meeting of AIC\Flash\figures" supersample 8 size 3812,2500
```


```chimerax
coordset #4 1,50
```

Instead of 
```chimerax
movie encode md_highres.mp4 framerate 10
```


```python
import os
import subprocess

def create_video_from_images(input_folder, output_video, frame_rate=16, crf=23):
    """
    Create a high-quality video from a folder of PNG images while keeping the file size small.

    Parameters:
    - input_folder: The folder containing PNG images.
    - output_video: The name of the output video file.
    - frame_rate: Frame rate of the video.
    - crf: Constant Rate Factor for controlling the quality (lower means better quality).
    """
    # Ensure the input folder exists
    if not os.path.isdir(input_folder):
        raise FileNotFoundError(f"The input folder {input_folder} does not exist.")
    
    # Create the ffmpeg command
    command = [
        'ffmpeg',
        '-framerate', str(frame_rate),
        '-i', os.path.join(input_folder, 'chimovie_Vyrt-%05d.png'),  # Adjust the pattern as necessary[!!!!]
        '-c:v', 'libx264',
        '-crf', str(crf),
        '-pix_fmt', 'yuv420p',
        output_video
    ]

    # Run the ffmpeg command
    try:
        subprocess.run(command, check=True)
        print(f"Video successfully created: {output_video}")
    except subprocess.CalledProcessError as e:
        print(f"An error occurred while creating the video: {e}")

# Example usage
input_folder = 'C:\\Users\\vitto\\OneDrive - CNR\\Conferenze e Missioni\\52nd Meeting of AIC\\Flash\\figures'
output_video = 'C:\\Users\\vitto\\OneDrive - CNR\\Conferenze e Missioni\\52nd Meeting of AIC\\Flash\\figures\\fecto.mp4'
create_video_from_images(input_folder, output_video, frame_rate=8)
```