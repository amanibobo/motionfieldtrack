# MotionField
MotionField creates a panorama out of a video and lets the user make measurements on it and track objects' paths and speeds.

# Demo

![A Demo Video](https://media.giphy.com/media/VxyFqfLxsI4srd5OSV/giphy.gif)

You can [download the demo video here](https://mega.nz/file/f9ERhYaQ#J7wMQrfppweOgWFkCc-vw-aCCHnT5u-d6UhH41NGYnQ), if you would like to tinker with the program. Feel free to test it on any video you would like.

# How does it work?

Understanding the stitching pipeline can help achieve correct panoramas for almost any video input. The program is generalizable through Expert Mode, to allow different types, angles, and speeds of videos to be correctly transformed into a panorama.

The stitching algorithm consists of 5 steps:
1. Choosing what frames to stitch - Not every frame of the video is eventually chosen for the final panorama, so as to reduce redundancy and speed up the computation. Each frame is searched for unique "key-points", special areas in the image which can be found despite spatial changes. A choice is done by minimizing the overlapping key-points between consecutive frames as much as possible.
2. Creating an Homography matrix - a matrix to relate pixels from one image to another is created - the homography matrix. 
3. Cylindrical projection - The images are then projected onto a cylinder, to correct for the warping done when panning the camera across a scene (the cylinder’s curvature can be controlled by in Expert Mode to allow maximum generalizability).
4. Creating the panorama - Each frame is warped by the homography matrix and stitched onto one big panorama. This is done without recalculating the homography after each stitching.
5. Attaching all the video frames to the panorama - Each frame of the video is warped and placed in the correct place on the panorama to create a Panoramic Video.

Some useful information about Expert Mode, and many more features, can be found in the Help menu present in the app.

# License

[MIT License](LICENSE.txt)

Copyright (c) 2022 Amani Bobo
