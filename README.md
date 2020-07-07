# tf-keras-vis
[![Downloads](https://pepy.tech/badge/tf-keras-vis)](https://pepy.tech/project/tf-keras-vis)
[![PyPI version](https://badge.fury.io/py/tf-keras-vis.svg)](https://badge.fury.io/py/tf-keras-vis)
[![Build Status](https://travis-ci.org/keisen/tf-keras-vis.svg?branch=master)](https://travis-ci.org/keisen/tf-keras-vis)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

tf-keras-vis is a visualization toolkit for debugging `tf.keras` models in Tensorflow2.0+.
Currently supported algorisms for visualization include:

* Activation Maximization
* Class Activation Maps
   - [GradCAM](https://arxiv.org/pdf/1610.02391v1.pdf)
   - [GradCAM++](https://arxiv.org/pdf/1710.11063.pdf)
   - [ScoreCAM](https://arxiv.org/pdf/1910.01279.pdf) :new::zap:
   - [Faster-ScoreCAM](https://github.com/tabayashi0117/Score-CAM/blob/master/README.md#faster-score-cam) :new::zap:
* Saliency Maps
   - [Vanilla Saliency](https://arxiv.org/pdf/1312.6034.pdf)
   - [SmoothGrad](https://arxiv.org/pdf/1706.03825.pdf)

tf-keras-vis is designed to be ease of use, light-weight and flexible.
All visualizations have the features as follows:

* Support **N-dim image inputs**, that's, not only support pictures but also such as 3D images.
* Support **batchwise** processing, so, be able to efficiently process multiple inputs.
* Support the model that have either **multiple inputs** or **multiple outputs**, or both.
* Support Optimizers embeded in tf.keras to process Activation maximization.


## Visualizations

### Visualize Dense Layer

<img src='https://github.com/keisen/tf-keras-vis/raw/master/examples/images/visualize-dense-layer.png' width='600px' />

### Visualize Convolutional Filer

<img src='https://github.com/keisen/tf-keras-vis/raw/master/examples/images/visualize-filters.png' width='800px' />

### GradCAM

<img src='https://github.com/keisen/tf-keras-vis/raw/master/examples/images/gradcam_plus_plus.png' width='600px' />

The images above are generated by `GradCAM++`.

### Saliency Map

<img src='https://github.com/keisen/tf-keras-vis/raw/master/examples/images/smoothgrad.png' width='600px' />

The images above are generated by `SmoothGrad`.


## Requirements

* Python 3.5-3.8
* tensorflow>=2.0


## Installation

* PyPI

```bash
$ pip install tf-keras-vis tensorflow
```

* Docker (container that run Jupyter Notebook)

```bash
$ docker run -itd -p 8888:8888 keisen/tf-keras-vis:0.4.0
```

If you have GPU processors,

```bash
$ docker run -itd --runtime=nvidia -p 8888:8888 keisen/tf-keras-vis:0.4.0-gpu
```

> You can find other images at [Docker Hub](https://hub.docker.com/repository/docker/keisen/tf-keras-vis/tags).


## Usage

Please see below for details:

* [examples/attentions.ipynb](https://github.com/keisen/tf-keras-vis/blob/master/examples/attentions.ipynb)
* [examples/visualize_dense_layer.ipynb](https://github.com/keisen/tf-keras-vis/blob/master/examples/visualize_dense_layer.ipynb)
* [examples/visualize_conv_filters.ipynb](https://github.com/keisen/tf-keras-vis/blob/master/examples/visualize_conv_filters.ipynb)

**[NOTE]**
If you have ever used [keras-vis](https://github.com/raghakot/keras-vis), you may feel that tf-keras-vis is similar with keras-vis.
Actually tf-keras-vis derived from keras-vis, and both provided visualization algorisms are almost the same.
But please notice that tf-keras-vis APIs does NOT have compatibility with keras-vis.


## ToDo
* API documentations
* We're going to add some algorisms such as below.
   - Deep Dream
   - Style transfer


## Known Issues

* With InceptionV3, ActivationMaximization doesn't work well, that's, it might generate meanninglessly bulr image.
* With cascading model, Gradcam and Gradcam++ don't work well, that's, it might occur some error. So we recommnend, in this case, to use FasterScoreCAM.
* Unsupport `channels-first` models and datas.


