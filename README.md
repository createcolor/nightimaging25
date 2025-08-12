# Night Photography Rendering Challenge

This challenge tackles the complexities of nighttime photography by leveraging paired datasets of raw Huawei smartphone images and processed Sony camera images, providing a clear ground truth for evaluation. The goal is to develop algorithms that process raw Huawei images to convincingly resemble the high-quality Sony outputs, addressing a long-standing challenge in computer vision.

Night photography is vital for applications like surveillance and security and also has artistic significance in creating stunning images. By combining objective ground-truth comparisons with human perception through mean opinion scores, the challenge ensures that results are both technically accurate and visually convincing.

This unique framework bridges mobile device constraints, low-light conditions, and human-centric evaluation, advancing the state of the art in night image processing.

Submissions will be evaluated by mean opinion scores and objective metrics.

This repo contains the source code of [Night Photography Rendering Challenge 2025](https://nightimaging.org/).

# Participants' solutions

All solutions submitted to the final stage of the challenge are available for [download via link (Google Drive)](https://drive.google.com/drive/folders/1jBW31fpwlATD7FBOVI_F70Xr15-dikQFEX4xh0FV1FPnD-UDsXP1DTW4SngDsMTYDpuExEIK?usp=sharing).

# Initial data processing

File crop_resize.py contains function "def crop_resize" which allows to bring source images from smartphone to size of ground truth images from photo camera. **CAUTION**! Crop and resize should be performed after debayering and distortion correction of input images. 

# Baseline

Raw images with metadata should be placed in the /data directory. 
 
## Installation and requirements

To work with code it is recommended to use **Python 3.9+**.
The required packages are listed in `requirements.txt` and can be installed by calling:

```bash
pip install -r requirements.txt
```

## raw_prc_pipeline

Module `raw_prc_pipeline` contains the source code of various methods and functions that can be used for processing raw images, including:

- Parsing metadata (see `raw_prc_pipeline/exif_*.py` files)
- Demosaicing, white_balancing (Gray World, White Patch, Shades of Gray, [Improved White Patch](https://ieeexplore.ieee.org/document/7025121)), tone mapping and other methods (see `raw_prc_pipeline/pipeline_utils.py`)
- Implemtations of demo classes of raw image processing pipeline and image processing pipeline executor (see `raw_prc_pipeline/pipeline.py`)

**Caution** If `color_matrix_*` is not provided average color matrix of Huawei Mate 40 Pro is used instead.

## demo

Directory `demo` contains demonstration script for processing PNG raw images with JSON metadata using implemented classes and finctions from `raw_prc_pipeline`.

To process PNG images with corresponding metadata from `data` directory call the following command:

```bash
python -m demo.process_pngs -p data -ie gw -tm Flash
```

To see other arguments of the script call `python -m demo.process_pngs -h` from the root directory.

Also you can use more reproducible way via Docker:

```bash
sudo docker build -t nightimaging .
sudo docker run --rm -u $(id -u):$(id -g) -v $(pwd)/data:/data nightimaging ./run.sh
```

