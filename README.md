# Night Photography Rendering Challenge

This challenge tackles the complexities of nighttime photography by leveraging paired datasets of raw Huawei smartphone images and processed Sony camera images, providing a clear ground truth for evaluation. The goal is to develop algorithms that process raw Huawei images to convincingly resemble the high-quality Sony outputs, addressing a long-standing challenge in computer vision.

Night photography is vital for applications like surveillance and security and also has artistic significance in creating stunning images. By combining objective ground-truth comparisons with human perception through mean opinion scores, the challenge ensures that results are both technically accurate and visually convincing.

This unique framework bridges mobile device constraints, low-light conditions, and human-centric evaluation, advancing the state of the art in night image processing.

Submissions will be evaluated by mean opinion scores and objective metrics.

This repo contains the source code of [Night Photography Rendering Challenge 2024](https://nightimaging.org/).

# Initial data processing

File crop_resize.py contains function "def crop_resize" which allows to bring source images from smartphone to size of ground truth images from photo camera. **CAUTION**! Crop and resize should be performed after debayering and distortion correction of input images.  
