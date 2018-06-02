# caffe_train_NEW
Caffe Framework for training CMU Human Pose with data augmentation layer
This caffe is made on 02/06/2018, based on this 2 version of caffe:
* [caffe_train](https://github.com/CMU-Perceptual-Computing-Lab/caffe_train) from [@ZheC](https://github.com/ZheC)
* [caffe-augmentation](https://github.com/twtygqyy/caffe-augmentation) from [@twtygqyy](https://github.com/twtygqyy)

I modify [cpm_data_transformer.cpp](https://github.com/albertchristianto/caffe_train_NEW/blob/master/src/caffe/cpm_data_transformer.cpp)(data augmentation layer), so it can change the contrast, brightness, color shift, and smooth filtering on training image data.

# How to Use
This is the example to specify your layer:
```
layer {
  name: "data"
  type: "CPMData"
  top: "data"
  top: "label"
  data_param {
    source: "*YOUR PATH TO LMDB FILE*"
    batch_size: 10
    backend: LMDB
  }
  cpm_transform_param {
    stride: 8
    max_rotate_degree: 40
    visualize: false
    crop_size_x: 368
    crop_size_y: 368
    scale_prob: 1
    scale_min: 0.5
    scale_max: 1.1
    target_dist: 0.6
    center_perterb_max: 40
    do_clahe: false
    num_parts: 56
    np_in_lmdb: 17
    contrast_brightness_adjustment: true
    smooth_filtering: true
    min_contrast: 0.8
    max_contrast: 1.2
    max_smooth: 6
    max_color_shift: 20
    apply_probability: 0.5   
  }
}
```

# Caffe

[![Build Status](https://travis-ci.org/BVLC/caffe.svg?branch=master)](https://travis-ci.org/BVLC/caffe)
[![License](https://img.shields.io/badge/license-BSD-blue.svg)](LICENSE)

Caffe is a deep learning framework made with expression, speed, and modularity in mind.
It is developed by the Berkeley Vision and Learning Center ([BVLC](http://bvlc.eecs.berkeley.edu)) and community contributors.

Check out the [project site](http://caffe.berkeleyvision.org) for all the details like

- [DIY Deep Learning for Vision with Caffe](https://docs.google.com/presentation/d/1UeKXVgRvvxg9OUdh_UiC5G71UMscNPlvArsWER41PsU/edit#slide=id.p)
- [Tutorial Documentation](http://caffe.berkeleyvision.org/tutorial/)
- [BVLC reference models](http://caffe.berkeleyvision.org/model_zoo.html) and the [community model zoo](https://github.com/BVLC/caffe/wiki/Model-Zoo)
- [Installation instructions](http://caffe.berkeleyvision.org/installation.html)

and step-by-step examples.

[![Join the chat at https://gitter.im/BVLC/caffe](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/BVLC/caffe?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Please join the [caffe-users group](https://groups.google.com/forum/#!forum/caffe-users) or [gitter chat](https://gitter.im/BVLC/caffe) to ask questions and talk about methods and models.
Framework development discussions and thorough bug reports are collected on [Issues](https://github.com/BVLC/caffe/issues).

Happy brewing!

## License and Citation

Caffe is released under the [BSD 2-Clause license](https://github.com/BVLC/caffe/blob/master/LICENSE).
The BVLC reference models are released for unrestricted use.

Please cite Caffe in your publications if it helps your research:

    @article{jia2014caffe,
      Author = {Jia, Yangqing and Shelhamer, Evan and Donahue, Jeff and Karayev, Sergey and Long, Jonathan and Girshick, Ross and Guadarrama, Sergio and Darrell, Trevor},
      Journal = {arXiv preprint arXiv:1408.5093},
      Title = {Caffe: Convolutional Architecture for Fast Feature Embedding},
      Year = {2014}
    }
