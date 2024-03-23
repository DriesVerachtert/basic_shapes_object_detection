---
language:
- en
license: apache-2.0
pretty_name: 'Basic Shapes Object Detection'
tags:
- object-detection
- simple
- example
- basic-geometric-shapes
annotations_creators:
- machine-generated
task_categories:
  - object-detection
dataset_info:
  features:
    - name: image_id
      dtype: int64
    - name: image
      dtype: image
    - name: width
      dtype: int32
    - name: height
      dtype: int32
    - name: objects
      sequence:
        - name: id
          dtype: int64
        - name: area
          dtype: int64
        - name: bbox
          sequence: float32
          length: 4
        - name: category
          dtype:
            class_label:
              names:
                '0': Square
                '1': Circle
                '2': Triangle
configs:
  - config_name: default
    data_files:
      - split: train
        path: data/train-*
      - split: test
        path: data/test-*
---

# Basic Shapes Object Detection

## Description

This Basic Shapes Object Detection dataset has been created to test fine-tuning of object detection models. Fine-tuning some model to detect the basic shapes should be rather easy: just a bit of training should be enough to get the model to do correct object detection quite fast.

Each entry in the dataset has a RGB PNG image with a white background and 3 basic geometric shapes:

* A blue square
* A red circle
* A green triangle

All images have the same size. Each image has exactly 1 square, 1 circle and 1 triangle, with their fixed colors. Each entry in the dataset has consequently 3 bounding boxes. The shapes do not overlap.The category IDs are 0, 1 and 2, corresponding to the labels Square, Circle and Triangle.

The dataset has exactly the same structure as the https://huggingface.co/datasets/cppe-5 dataset, but fine-tuning some model to this dataset with basic geometric shapes should require considerable less training compared to the cppe-5 dataset. Once you have tested your fine-tuning code on this dataset, it should also work on more complicated datasets such as the cppe-5 dataset.

![](https://github.com/DriesVerachtert/basic_shapes_object_detection/blob/main/examples.png)

## Links

The Python code to generate the images can be found at https://github.com/DriesVerachtert/basic_shapes_object_detection
The dataset can be downloaded from https://huggingface.co/datasets/driesverachtert/basic_shapes_object_detection

## Structure

The bounding boxes are in COCO format (x_min, y_min, width, height).

## License

This dataset is released under Apache 2.0.

## Usage

```python
from datasets import load_dataset
dataset = load_dataset("driesverachtert/basic_shapes_object_detection")
```