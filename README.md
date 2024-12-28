# DBA-Fire Dataset

## Overview

The DBA-Fire dataset is designed for fire and smoke detection in real-world scenarios. This dataset was created through a comprehensive data collection, segmentation, cleansing, and labeling process. It consists of 3905 high-quality images, accompanied by corresponding YOLO-format labels, providing a robust foundation for training deep learning models focused on fire and smoke detection. 

The dataset covers a wide range of fire-related scenarios, from small outdoor and indoor flames to large-scale fires in complex environments, including city roads, buildings, supermarkets, and parking lots. It addresses key limitations of existing publicly available datasets, such as small data size, limited scene diversity, and imbalanced object labeling.

The DBA-Fire dataset will be open-sourced and made available on [Huggingface](https://huggingface.co/) and [GitHub](https://github.com/) upon acceptance of the paper.

## Dataset Highlights

- **Size**: 3905 images
- **Categories**: 
  - Flames
  - Smoke
  - Both flames and smoke
- **Scenes**: A diverse collection of fire scenarios, including both indoor and outdoor settings with varying complexities (e.g., city roads, large buildings, supermarkets, and parking lots).
- **Data Format**: 
  - **Images**: JPEG format (stored in `DBA-Fire/JPEGImages/`)
  - **Labels**: YOLO-format labels (stored in `DBA-Fire/txt/`)
  - One label file per image in the dataset.
  
## Data Processing Pipeline

1. **Data Collection**: A web crawler was designed to collect fire-related videos and images. Videos were segmented into frames, and only distinct frames were extracted to avoid redundancy.
   
2. **Frame Segmentation**: Video clips were divided into frames at a rate of 25 frames per second, with a sample taken every 3 frames to ensure variability in the images.

3. **Data Cleansing**: Images were filtered based on several criteria:
   - Scenes where flames and smoke cover less than 30% of the image area.
   - Images with a signal-to-noise ratio (SNR) lower than 35 decibels were excluded.
   - Background pixels were filtered based on RGB values using predefined thresholds (equations (11), (12), and (13)).

4. **Object Labeling**: Images were manually annotated using the LabelImg tool, categorizing the objects into flames and smoke, with bounding box information stored in Pascal VOC XML format. The final label format was converted into YOLO’s TXT format for training compatibility.

## Dataset Structure

The dataset is structured as follows:

DBA-Fire/
│
├── JPEGImages/
│   └── 3905 images in JPEG format
│
└── txt/
    └── 3905 corresponding label files in YOLO TXT format

Each label file corresponds to an image in the `JPEGImages` folder and contains bounding box annotations in YOLO format.

## Intended Use

This dataset is primarily intended for the development and evaluation of deep learning models focused on fire and smoke detection. It can be used for training, fine-tuning, and benchmarking algorithms in a variety of settings, from small indoor flames to large-scale outdoor fires.

### Key Benefits:
- Large-scale dataset covering a wide range of real-world fire and smoke scenarios.
- Balanced and labeled data with two primary object categories: flames and smoke.
- High-quality, properly segmented images and YOLO-compatible labels for model training.

## Licensing and Citation

The dataset is available for research purposes under [appropriate license terms]. Upon acceptance of the associated paper, the dataset will be hosted on Huggingface and GitHub, and we encourage you to cite the paper if you use the dataset in your work.
Paper title: DBA-YOLO: A Lightweight Fire Detection Algorithm with Structural Reparameterized Multiple Attention Mechanisms.
