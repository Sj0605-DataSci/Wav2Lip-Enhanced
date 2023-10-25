## Wav2Lip-Enhanced for OpeninAPP:


# Installation:

### For the easiest and most compatible way to use this tool, use the Google Colab version:

ipynb link: [https://github.com/Sj0605-DataSci/Wav2Lip-Enhanced/blob/main/Easy_Wav2Lip_v8.ipynb](https://github.com/Sj0605-DataSci/Wav2Lip-Enhanced/blob/main/Easy_Wav2Lip_v8.ipynb)


# Credits:
* [The Original Wav2Lip](https://github.com/Rudrabha/Wav2Lip) of course.
* The huge speed increase and improved base quality come from [cog-Wav2Lip](https://github.com/devxpy/cog-Wav2Lip).
* Code to upscale with [GFPGAN](https://github.com/TencentARC/GFPGAN) mainly came from [wav2lip-hq-updated-ESRGAN](https://github.com/GucciFlipFlops1917/wav2lip-hq-updated-ESRGAN).
* [The Easy Wav2Lip](https://github.com/anothermartz/Easy-Wav2Lip/tree/v8) of course.
* Thanks to [JustinJohn](https://github.com/justinjohn0306) for making the [Wav2Lip_simplified].


# Best practices:
* The best results come from lining up the speech to the actions and expressions of the speaker before you send it through wav2lip!

Video files:
* Must have a face in all frames or Wav2Lip will fail
* Crop or mask out faces you don't want to lipsync or it'll choose randomly.
* Use h264 .mp4 - other file types may be supported but this is what it outputs as
* Images are currently untested.
* Use a small file in every way (try <720p, <30 seconds, 30fps <b></b> etc. - Bigger files may work but are usually the reason it fails)
* For your first try, use a really tiny clip just to get used to the process, only once you're familiar should you try bigger files to see if they work.


# Advanced Tweaking:
## wav2lip_version:
| Option | Pros | Cons |
|:-------|:-----|:-----|
| Wav2Lip | - More accurate lipsync <br> - Closes the mouth when there is no sound | - Sometimes produces missing teeth (uncommon) |
| Wav2Lip_GAN | - Looks nicer <br> - Keeps the original expressions of the speaker | - Less accurate lipsync <br> - Keeps the mouth similar to the original when there is no sound |

I suggest trying Wav2Lip first and switching to the GAN version if you experience an effect where it looks like the speaker has big gaps in their teeth.

### nosmooth:
* When enabled, wav2lip will crop the face on each frame independently.
  * Good for fast movements or cuts in the video.
  * May cause twitching if the face is on a weird angle.

* When disabled, wav2lip will blend the detected position of the face between 5 frames.
  * Good for slow movements, especially for faces on an unusual angle.
  * Mouth can be offset when the face moves within the frame quickly, looks horrible between cuts.

## Padding:
This option controls how many pixels are added or removed from the face crop in each direction.

| Value | Example | Effect |
|:------|:--------|:-------|
| U | U = -10 | Removes 5 pixels from the top of the face |
| D | D = 10 | Adds 10 pixels to the bottom of the face |
| L | L = 0 | No change to the left of the face |
| R | R = 15 | Adds 15 pixels to the right of the face |

Padding can help remove hard lines at the chin or other edges of the face, but too much or too little padding can change the size or position of the mouth. It's common practice to add 10 pixels to the bottom, but you should experiment with different values to find the best balance for your clip.

## Mask:
This option controls how the processed face is blended with the original face. This has no effect on the "Fast" quality option.

* **size** will increase the size of the area that the mask covers.
* **feathering** determines the amount of blending between the centre of the mask and the edges.
* **mouth_tracking** will update the position of the mask to where the mouth is on every frame (slower)
*   * Note: The mouth position is already well approximated due to the frame being cropped to the face, enable this only if you find a video where the mask doesn't appear to follow the mouth.
* **debug_mask** will make the background grayscale and the mask in colour so that you can easily see where the mask is in the frame.

# Other options:

# Batch processing:
This option allows you to process multiple video and/or audio files automatically. 
* Name your files with a number at the end, eg. Video1.mp4, Video2.mp4, etc. and put them all in the same folder.
* Files will be processed in numerical order starting from the one you select. For example, if you select Video3.mp4, it will process Video3.mp4, Video4.mp4, and so on.
* If you select numbered video files and a non-numbered audio file, it will process each video with the same audio file. Useful for making different images/videos say the same line.
* Likewise, if you select a non-numbered video file and numbered audio files, it will use the same video for each audio file. Useful for making the same image/video say different things.

### output_suffix:
This adds a suffix to your output files so that they don't overwite your originals.

### include_settings_in_suffix:
Adds what settings were used - good for comparing different settings as you will know what you used for each render.
Will add: Qualty_resolution_nosmooth_pads-UDLR
EG: _Enhanced_720_nosmooth1_pads-U15D10L-15R30
pads_UDLR will not be included if they are set to 0.
resolution will not be included if it output_height is set to full resolution



### Input and Output
- [View Creator's Tamil Video as Input 1](https://drive.google.com/file/d/1wKg8ShQ06UT5wKIdXG7QGlwTNbUaDXCW/view?usp=sharing)
- [Listen Creator's Hindi voice as Input 2](https://drive.google.com/file/d/1zermbJPiKetEAln-uHkY_g2BMg4gY7Cj/view?usp=sharing)
- [View Creator's Hindi Vedio as Output](https://drive.google.com/file/d/1XbM7O3d6kDnBFfa1-fu9akmSHrtd94-n/view?usp=sharing)
