<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="#">
<img src="assets/d-cube_logo.png" alt="Logo" width="310"></a>
  <h4 align="center">A detection dataset with class names characterized by intricate and flexible expressions</h4>
    <p align="center">
    The repo is the toolbox for <b>D<sup>3</sup></b>
    <br />
    <a href="doc.md"><strong> [Doc 📚]</strong></a>
    <a href="https://huggingface.co/datasets/zbrl/d-cube"><strong> [HuggingFace 🤗]</strong></a>
    <a href="#"><strong> [Papers 📄] »</strong></a>
    <br />
  </p>
</p>

***
Description Detection Dataset ($D^3$, /dikju:b/) is an attempt at creating a next-generation object detection dataset. Unlike traditional detection datasets, the class names of the objects are no longer simple nouns or noun phrases, but rather complex and descriptive, such as `a dog not being held by a leash`. For each image in the dataset, any object that matches the description is annotated. The dataset provides annotations such as bounding boxes and finely crafted instance masks. We believe it will contribute to computer vision and vision-language communities.


# News
[07/18/2023] We have released our Description Detection Dataset ($D^3$) and the first version of $D^3$ toolbox. You can download it now for your project.

# Contents
- [Dataset Highlight](#task-and-dataset-highlight)
- [Download](#download)
- [Installation](#installation)
- [Usage](#usage)

# Task and Dataset Highlight

The $D^3$ dataset is meant for the Description Object Detection (DOD) task. In the image below we show the difference between Referring Expression Comprehension (REC), Object Detection/Open-Vocabulary Detection (OVD) and Described Object Detection (DOD). OVD detect object based on category name, and each category can have zero to multiple instances; REC grounds one region based on a language description, whether the object truly exits or not; DOD detect all instances on each image in the dataset, based on a flexible reference.

![Dataset Highlight](assets/teaser.png "Highlight of the task & dataset")

For more information on the characteristics of this dataset, please refer to our paper.

# Download
Currently we host the $D^3$ dataset on cloud drives. You can download the dataset from [Google Drive](https://drive.google.com/drive/folders/11kfY12NzKPwsliLEcIYki1yUqt7PbMEi?usp=sharing) or [Baidu Pan]().

After downloading the `d3_images.zip` (images in the dataset), `d3_pkl.zip` (dataset information for this toolkit) and `d3_json.zip` (annotation for evaluation), please extract these 3 zip files to your custom `IMG_ROOT`, `PKL_PATH` and `JSON_ANNO_PATH` directory. These paths will be used when you perform inference or evaluation on this dataset.

# Installation

## Prerequisites
This toolkit requires a few python packages like `numpy` and `pycocotools`. Other packages like `matplotlib` and `opencv-python` may also be required if you want to utilize the visualization scripts.

There are three ways to install $D^3$ toolbox, and the third one (with huggingface) is currently in the works and will be available soon.

## Install with pip
```bash
pip install d-cube
```
## Install from source
```bash
git clone https://github.com/shikra/d-cube.git
# option 1: install it as a python package
cd d-cube
python -m pip install .
# option 2: just put it in the root folder of your local repository
```

## Via HuggingFace Datasets 🤗
```bash
coming soon
```

# Usage
Please refer to the [documentation 📚](doc.md) for more details.
Our toolbox is similar to [cocoapi](https://github.com/cocodataset/cocoapi) in style.

Here is a quick example of how to use $D^3$.
```python
from d_cube import D3
d3 = D3(IMG_ROOT, PKL_ANNO_PATH)
img_ids = d3.get_img_ids()  # get the image ids in the dataset
img_info = d3.load_imgs(img_ids)  # load images by passing a list of some image ids
img_path = img_info[0]["file_name"]  # obtain image path so you can load it and inference
```

# Citation
If you use our $D^3$ dataset, this toolbox, or otherwise find our work valuable, please cite our paper:
```bibtex
@article{xie2023DOD,
  title={Exposing the Troublemakers in Described Object Detection},
  author={Xie, Chi and Zhang, Zhao and Wu, Yixuan and Zhu, Feng and Zhao, Rui and Liang, Shuang},
  journal={arXiv preprint},
  year={2023}
}
```
