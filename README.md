# tf-keras-vis
[![Downloads](https://pepy.tech/badge/tf-keras-vis)](https://pepy.tech/project/tf-keras-vis)
[![PyPI version](https://badge.fury.io/py/tf-keras-vis.svg)](https://badge.fury.io/py/tf-keras-vis)
[![Build Status](https://travis-ci.org/keisen/tf-keras-vis.svg?branch=master)](https://travis-ci.org/keisen/tf-keras-vis)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

tf-keras-vis is a visualization toolkit for debugging `tf.keras` models in Tensorflow2.0+.
Currently supported methods for visualization include:

* Activation Maximization
* Class Activation Maps
   - [GradCAM](https://arxiv.org/pdf/1610.02391v1.pdf)
   - [GradCAM++](https://arxiv.org/pdf/1710.11063.pdf)
   - [ScoreCAM](https://arxiv.org/pdf/1910.01279.pdf)
   - [Faster-ScoreCAM](https://github.com/tabayashi0117/Score-CAM/blob/master/README.md#faster-score-cam)
* Saliency Maps
   - [Vanilla Saliency](https://arxiv.org/pdf/1312.6034.pdf)
   - [SmoothGrad](https://arxiv.org/pdf/1706.03825.pdf)

tf-keras-vis is designed to be light-weight, flexible and ease of use.
All visualizations have the features as follows:

* Support **N-dim image inputs**, that's, not only support pictures but also such as 3D images.
* Support **batchwise** processing, so, be able to efficiently process multiple input images.
* Support the model that have either **multiple inputs** or **multiple outputs**, or both.
* Support Optimizers embedded in tf.keras to process Activation maximization.


## Visualizations

### Visualizing Dense Layer

<img src='https://github.com/keisen/tf-keras-vis/raw/master/examples/images/visualize-dense-layer.png' width='600px' />

### Visualizing Convolutional Filer

<img src='https://github.com/keisen/tf-keras-vis/raw/master/examples/images/visualize-filters.png' width='600px' />

### GradCAM

<img src='https://github.com/keisen/tf-keras-vis/raw/master/examples/images/gradcam_plus_plus.png' width='600px' />

The images above are generated by `GradCAM++`.

### Saliency Map

<img src='https://github.com/keisen/tf-keras-vis/raw/master/examples/images/smoothgrad.png' width='600px' />

The images above are generated by `SmoothGrad`.


## Requirements

* Python 3.6-3.9
* tensorflow>=2.0.2


## Installation

* PyPI

```bash
$ pip install tf-keras-vis tensorflow
```

* Docker (container that run Jupyter Notebook)

```bash
$ cd tf-keras-vis
$ docker build -t <TAG> -f dockerfiles/gpu.Dockerfile .
$ docker run --gpus all --privileged -itd -p 8888:8888 <TAG>
```

Or

```bash
$ docker run --gpus all --privileged -itd -p 8888:8888 keisen/tf-keras-vis:0.6.0-gpu
```

> You can find other images at [Docker Hub](https://hub.docker.com/repository/docker/keisen/tf-keras-vis/tags).


## Usage

Please see below for details:

### Getting Started Guides

* [Saliency and CAMs](https://github.com/keisen/tf-keras-vis/blob/master/examples/attentions.ipynb)
* [Visualize Dense Layer](https://github.com/keisen/tf-keras-vis/blob/master/examples/visualize_dense_layer.ipynb)
* [Visualize Convolutional Filer](https://github.com/keisen/tf-keras-vis/blob/master/examples/visualize_conv_filters.ipynb)

**[NOTE]**
If you have ever used [keras-vis](https://github.com/raghakot/keras-vis), you may feel that tf-keras-vis is similar with keras-vis.
Actually tf-keras-vis derived from keras-vis, and both provided visualization methods are almost the same.
But please note that tf-keras-vis APIs does NOT have compatibility with keras-vis.

### Guides (ToDo)

* Visualizing multiple attention or activation images at once utilizing batch-system of model
* Define various score functions
* Visualizing attentions with multiple inputs models
* Visualizing attentions with multiple outputs models
* Advanced score functions
* Tuning Activation Maximization
* Visualizing attentions for N-dim image inputs


## ToDo

* Guide documentations
* API documentations
* We're going to add some methods such as below.
   - Deep Dream
   - Style transfer


## Known Issues

* With InceptionV3, ActivationMaximization doesn't work well, that's, it might generate meaninglessly blur image.
* With cascading model, Gradcam and Gradcam++ don't work well, that's, it might occur some error. So we recommend, in this case, to use FasterScoreCAM.
* `channels-first` models and data is unsupported.


## Use Cases

* [chitra](https://github.com/aniketmaurya/chitra)
   * A Deep Learning Computer Vision library for easy data loading, model building and model interpretation with GradCAM/GradCAM++.
