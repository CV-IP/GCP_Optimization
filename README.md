# What Deep CNNs Benefit from Global Covariance Pooling: An Optimization Perspective
This is an code implementation of CVPR20 paper ([What Deep CNNs Benefit from Global Covariance Pooling: An Optimization Perspective]()), created by [Qilong Wang](https://csqlwang.github.io/homepage/) and Li Zhang.

## Introduction
Recent works have demonstrated that global covariance pooling (GCP) has the ability to improve performance of deep convolutional neural networks (CNNs) on visual classification task. Despite considerable advance, the reasons on effectiveness of GCP on deep CNNs have not been well studied. In this paper, we make an attempt to understand what deep CNNs benefit from GCP in a viewpoint of optimization. Specifically, we explore the effect of GCP on deep CNNs in terms of the Lipschitzness of optimization loss and the predictiveness of gradients, and show that GCP can make the optimization landscape more smooth and the gradients more predictive. Furthermore, we discuss the connection between GCP and second-order optimization for deep CNNs. More importantly, above findings can account for several merits of covariance pooling for training deep CNNs that have not been recognized previously or fully explored, including significant acceleration of network convergence (i.e., the networks trained with GCP can support rapid decay of learning rates, achieving favorable performance while significantly reducing number of training epochs), stronger robustness to distorted examples generated by image corruptions and perturbations, and good generalization ability to different vision tasks, e.g., object detection and instance segmentation. We conduct extensive experiments using various deep CNN models on diversified tasks, and the results provide strong support to our findings.

## Citation

@inproceedings{wang2020deep,
  title={What Deep CNNs Benefit from Global Covariance Pooling: An Optimization Perspective},
  author={Wang, Qilong and Zhang, Li and Wu, Banggu and Ren, Dongwei and Li, Peihua and Zuo, Wangmeng and Hu, Qinghua},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  year={2020}
}

## Environments

- OS: Ubuntu 16.04
- CUDA: 9.0/10.0
- Toolkit: PyTorch 1.3/1.4
- GPU: GTX 2080Ti/TiTan XP

## Installation

pytorch installation following [pytorch.org](https://pytorch.org/)

## Plot Loss Landscape and Gradient Predictiveness

![Lipschitzness](https://github.com/ZhangLi-CS/GCP_Optimization/blob/master/Lipschitzness.png)

1. Test MobileNetV2 models' LandScape: In the floder `./landscape/MobileNetV2` , run `sh ./scripts/train.sh`

2. Test ResNet models' LandScape: In the floder `./landscape/ResNet` , run `sh ./scripts/train.sh`

*Note that you need to modify  the `dataset path` or `model name` in `train.sh` for fitting your configurations, and descriptions on all parameters can be found in file `./landscape/readme.txt`.


## Experiments on ImageNet

### Setting Parameters 

We divide the parameters into three types `LRnorm`,`LRfast` and `LRadju`.

![LearningRate](https://github.com/ZhangLi-CS/GCP_Optimization/blob/master/LearningRate.png)

### Training Models

1. Training models (except ShuffleNetV2) on ImageNet : In floder `src` , run ` sh ./scripts/train/train.sh `

2. Training ShuffleNetV2 models on ImageNet : In floder `src` , run ` sh ./scripts/train/train_shufflenet.sh `

3. Testing models on ImageNet : In floder `src` , run ` sh ./scripts/val/val.sh `

*Note that you need to modify  the `dataset path` or `model name` in `train.sh` or `val.sh` for fitting your configurations, and descriptions on all parameters can be found in file `./src/scripts/readme.txt`.

### Main Results and Models 

#### MobileNetV2
|Models|Top-1 acc.(%)|Top-5 acc.(%)|BaiduDrive(models)|Extract code|GoogleDrive|
|:-----|:-----------:|:-----------:|:-----------------|:----------:|:----------|
|MobileNetV2_GAP_LRnorm|&nbsp;&nbsp;&nbsp;71.62&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;90.18&nbsp;&nbsp;&nbsp;|[MobileNetV2_GAP_LRnorm](https://pan.baidu.com/s/1L0DHZhyzp_h02WfZ1xq8Hw)|va25|[MobileNetV2_GAP_LRnorm](https://drive.google.com/open?id=1NTKVzjpuJtDEBBShgBPailKdhntUXwKs)|
|MobileNetV2_GAP_LRfast|69.29|89.01|[MobileNetV2_GAP_LRfast](https://pan.baidu.com/s/1-vujnIa4RVxw4QVG2j5zZg)|f5n4|[MobileNetV2_GAP_LRfast](https://drive.google.com/open?id=1_OeoWrDUoSsRDFOA0-ZmIOzmWyelv9op)|
|MobileNetV2_GAP_LRadju|71.27|90.08|[MobileNetV2_GAP_LRadju](https://pan.baidu.com/s/1ZKk_m-XQ7gwt6Z1kEDg_cw)|pai8|[MobileNetV2_GAP_LRadju](https://drive.google.com/open?id=177K9xr89XJ-Upax2NB3WNb9s6X1eWZA7)|
|MobileNetV2_GCP_LRnorm|74.39|91.86|[MobileNetV2_GCP_LRnorm](https://pan.baidu.com/s/1cdCpSV8Md6faxkUt7v-tDQ)|3r9q|[MobileNetV2_GCP_LRnorm](https://drive.google.com/open?id=18OpYWyBUGqSIiY4m0BqKsHNo22IuNB80)|
|MobileNetV2_GCP_LRfast|72.45|90.51|[MobileNetV2_GCP_LRfast](https://pan.baidu.com/s/1seBLgrtT9gnLgEJk80hbJA)|dq5w|[MobileNetV2_GCP_LRfast](https://drive.google.com/open?id=1VHTcaoZU-IoeQlflbpPZJrmlP79vgMYF)|
|MobileNetV2_GCP_LRadju|73.97|91.53|[MobileNetV2_GCP_LRadju](https://pan.baidu.com/s/1HBacuaQ_8qbBaZFSJhn20Q)|i7y3|[MobileNetV2_GCP_LRadju](https://drive.google.com/open?id=1b77p7IkLVMGKcvBb2p7tHgjr_I6tZjWh)|
|MobileNetV2_GCP_LRnorm_128|73.28|91.26|[MobileNetV2_GCP_LRnorm_128](https://pan.baidu.com/s/1egJRYtCmMTNnz5uhy5KvGg)|cxhu|[MobileNetV2_GCP_LRnorm_128](https://drive.google.com/open?id=1D5ab0tRhIWvFsV9vR67-GQtnen71MFmB)|
|MobileNetV2_GCP_LRadju_128|72.58|90.87|[MobileNetV2_GCP_LRadju_128](https://pan.baidu.com/s/1WcOX5fKaGGDIcM6zTqL8fw)|3qdx|[MobileNetV2_GCP_LRadju_128](https://drive.google.com/open?id=1ZSZBIgknAOX3oC0sx6gsfbmMEV0gFKJ4)|

#### ShuffleNetV2
|Models|Top-1 acc.(%)|Top-5 acc.(%)|BaiduDrive(models)|Extract code|GoogleDrive|
|:-----|:-----------:|:-----------:|:-----------------|:----------:|:----------|
|ShuffleNetV2_GAP_LRnorm|&nbsp;&nbsp;&nbsp;67.96&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;87.84&nbsp;&nbsp;&nbsp;|[ShuffleNetV2_GAP_LRnorm](https://pan.baidu.com/s/1N43tW6kFwurjOn-YR9kukg)|rbew|[ShuffleNetV2_GAP_LRnorm](https://drive.google.com/open?id=1MtG2wGDk-JweO1vzX_7LxBvJvF_jCo1r)|
|ShuffleNetV2_GAP_LRfast|66.13|86.54|[ShuffleNetV2_GAP_LRfast](https://pan.baidu.com/s/1Ot7COL8DmJAhLVy51Y6kqg)|7y58|[ShuffleNetV2_GAP_LRfast](https://drive.google.com/open?id=1apUs5zfR_ZdJO00tJHZwYHi2dIv6zVpm)|
|ShuffleNetV2_GAP_LRadju|67.15|87.35|[ShuffleNetV2_GAP_LRadju](https://pan.baidu.com/s/1YKkFzLgMtcJ1Uw4nGoLqdg)|c7i8|[ShuffleNetV2_GAP_LRadju](https://drive.google.com/open?id=1xnmnY7Dk6A5UaKSkS3xx71dz-kiMLrzw)|
|ShuffleNetV2_GCP_LRnorm|71.83|90.04|[ShuffleNetV2_GCP_LRnorm](https://pan.baidu.com/s/18_RE34Y0j7vxSXeyIY5dmA)|tr5u|[ShuffleNetV2_GCP_LRnorm](https://drive.google.com/open?id=1fEOyjZrXdcGuXvj8l0XwYCdt5uQx6fAM)|
|ShuffleNetV2_GCP_LRfast|70.29|89.00|[ShuffleNetV2_GCP_LRfast](https://pan.baidu.com/s/1Eg4Gu3-qmqnzWxGjlJyfsA)|8qxx|[ShuffleNetV2_GCP_LRfast](https://drive.google.com/open?id=1-r46jSo8qooPeQdymyToaL3pQNTmOHtr)|
|ShuffleNetV2_GCP_LRadju|71.17|89.74|[ShuffleNetV2_GCP_LRadju](https://pan.baidu.com/s/1rEPaU7Cyv8O1DUdHyFrW7Q)|nud1|[ShuffleNetV2_GCP_LRadju](https://drive.google.com/open?id=1P-RlJat6XL7BxD5oCDz_ifKDq7NNRYqj)|

#### ResNet18
|Models|Top-1 acc.(%)|Top-5 acc.(%)|BaiduDrive(models)|Extract code|GoogleDrive|
|:-----|:-----------:|:-----------:|:-----------------|:----------:|:----------|
|ResNet18_GAP_LRnorm|&nbsp;&nbsp;&nbsp;70.47&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;89.59&nbsp;&nbsp;&nbsp;|[ResNet18_GAP_LRnorm](https://pan.baidu.com/s/1PYlOx5Ap8iy0JPz1nURZhQ)|z7ab|[ResNet18_GAP_LRnorm](https://drive.google.com/open?id=1hK56OuyrXiEIrp7D3CroaGM2L2-FSTl0)|
|ResNet18_GAP_LRfast|66.02|86.69|[ResNet18_GAP_LRfast](https://pan.baidu.com/s/1Wam0yraiZoeAHqfScGcDXA)|78uw|[ResNet18_GAP_LRfast](https://drive.google.com/open?id=1870WX_VaHZd5qgcyUXaqtJ-EFpqx9uX4)|
|ResNet18_GAP_LRadju|69.62|89.00|[ResNet18_GAP_LRadju](https://pan.baidu.com/s/1sBWTZodgD27V2Tr6hoIYnQ)|29cn|[ResNet18_GAP_LRadju](https://drive.google.com/open?id=1ttvh_nt6JURkkLHKhVr9r-VwcwXd7cfS)|
|ResNet18_GCP_LRnorm|75.48|92.23|[ResNet18_GCP_LRnorm](https://pan.baidu.com/s/1Nr6FH8PUbY60oAOi41pYWQ)|eje8|[ResNet18_GCP_LRnorm](https://drive.google.com/open?id=1D4ZmTHJ5dmTTpdL2IA3UJUIm54cF45na)|
|ResNet18_GCP_LRfast|72.02|89.97|[ResNet18_GCP_LRfast](https://pan.baidu.com/s/1PkbvOYPtPGQoaXt5CVeJWA)|k6f6|[ResNet18_GCP_LRfast](https://drive.google.com/open?id=1PkMvpWj6FH1d4RxgNKkqoalt3mqRo9J8)|
|ResNet18_GCP_LRadju|74.86|91.81|[ResNet18_GCP_LRadju](https://pan.baidu.com/s/1LAX4EKZW2SXx_TiOOYQNmQ)|tci6|[ResNet18_GCP_LRadju](https://drive.google.com/open?id=1BnO-zTz_L3zqO9bW4c-YE9Ao0d2qDZuD)|

#### ResNet34
|Models|Top-1 acc.(%)|Top-5 acc.(%)|BaiduDrive(models)|Extract code|GoogleDrive|
|:-----|:-----------:|:-----------:|:-----------------|:----------:|:----------|
|ResNet34_GAP_LRnorm|&nbsp;&nbsp;&nbsp;74.19&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;91.60&nbsp;&nbsp;&nbsp;|[ResNet34_GAP_LRnorm](https://pan.baidu.com/s/17hwLgIaRtsnziS3qj83MwQ)|1yp6|[ResNet34_GAP_LRnorm](https://drive.google.com/open?id=1V-4n8sxtCmp5iiWws1kBhYXFXsG6fVrX)|
|ResNet34_GAP_LRfast|69.88|89.25|[ResNet34_GAP_LRfast](https://pan.baidu.com/s/1cm40DbKD9BtJGbo4vEH3_g)|nmni|[ResNet34_GAP_LRfast](https://drive.google.com/open?id=1c5RxEeipeWt07OlOT1BYWRJhf3XcEDA9)|
|ResNet34_GAP_LRadju|73.13|91.14|[ResNet34_GAP_LRadju](https://pan.baidu.com/s/1gAbzSqi_1_1FMJJ9t2c89w)|5eyk|[ResNet34_GAP_LRadju](https://drive.google.com/open?id=1-NgzG9zN5nY0jJpV07yKtfKIJ0CpQCkb)|
|ResNet34_GCP_LRnorm|77.11|93.33|[ResNet34_GCP_LRnorm](https://pan.baidu.com/s/1T4lKenLGKbrHZrt3cOtDPg)|bn2d|[ResNet34_GCP_LRnorm](https://drive.google.com/open?id=15k8roxdmpq8iwasi6Piysh8HK4vlsG_m)|
|ResNet34_GCP_LRfast|73.88|91.42|[ResNet34_GCP_LRfast](https://pan.baidu.com/s/1EMGIUc60SwWDxyVyMWO1XQ)|wmky|[ResNet34_GCP_LRfast](https://drive.google.com/open?id=1I145XHsrAjfuseIdCqesxK825-FrA6Zj)|
|ResNet34_GCP_LRadju|76.81|93.04|[ResNet34_GCP_LRadju](https://pan.baidu.com/s/1T2_M2q-WJ8klUomxA0olcA)|4w21|[ResNet34_GCP_LRadju](https://drive.google.com/open?id=1C3m6uicOuYoWiqRrt8ZUjgloa6iSLw-Y)|

#### ResNet50
|Models|Top-1 acc.(%)|Top-5 acc.(%)|BaiduDrive(models)|Extract code|GoogleDrive|
|:-----|:-----------:|:-----------:|:-----------------|:----------:|:----------|
|ResNet50_GAP_LRnorm|&nbsp;&nbsp;&nbsp;76.02&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;92.97&nbsp;&nbsp;&nbsp;|[ResNet50_GAP_LRnorm](https://pan.baidu.com/s/1iaDm9ZNiyeANfe6Zzi-PFg)|3r9p|[ResNet50_GAP_LRnorm](https://drive.google.com/open?id=17MyDHCKS8wla8GZvwSbfNfQAJ12KofV_)|
|ResNet50_GAP_LRfast|71.08|90.04|[ResNet50_GAP_LRfast](https://pan.baidu.com/s/1en48JRo9DaqAAC0nljR-3Q)|reub|[ResNet50_GAP_LRfast](https://drive.google.com/open?id=10yk2wFB_q1VICyTu4CrjWUv-_fnV9Dt2)|
|ResNet50_GAP_LRadju|75.32|92.47|[ResNet50_GAP_LRadju](https://pan.baidu.com/s/10ZQ4XAnnhsUNazzt_2bvgg)|5tdw|[ResNet50_GAP_LRadju](https://drive.google.com/open?id=1PMNcVO_CNR2JUgXRhBCrqSg9Btj4m4cO)|
|ResNet50_GCP_LRnorm|78.56|94.09|[ResNet50_GCP_LRnorm](https://pan.baidu.com/s/1gZ6_KMqfUBAjq913zKOPkw)|e7iy|[ResNet50_GCP_LRnorm](https://drive.google.com/open?id=1TmnusKSArjKTTb28cnw2OzrUVc_DAi98)|
|ResNet50_GCP_LRfast|75.31|92.11|[ResNet50_GCP_LRfast](https://pan.baidu.com/s/1Qg-_jms3AChBw9ZXwl31Qw)|3j8e|[ResNet50_GCP_LRfast](https://drive.google.com/open?id=1at9nxW658Yeh-jqCUc544ex4_j_iA2VJ)|
|ResNet50_GCP_LRadju|78.03|93.95|[ResNet50_GCP_LRadju](https://pan.baidu.com/s/1PGLAKzNuQRkqtjygYov90w)|n4vq|[ResNet50_GCP_LRadju](https://drive.google.com/open?id=1t2j5LNLr51TZ3O1QtYmgRyPe8zDSg9yr)|
|ResNet50_GCP_LRnorm_128|78.02|94.02|[ResNet50_GCP_LRnorm_128](https://pan.baidu.com/s/1FZV-_8lHFzK4_j8_AZna3g)|976a|[ResNet50_GCP_LRnorm_128](https://drive.google.com/open?id=1taR2AvNC32YnF9ge4To30JUVa4SNq62g)|
|ResNet50_GCP_LRadju_128|77.72|93.73|[ResNet50_GCP_LRadju_128](https://pan.baidu.com/s/1GxiLO3RTBZoV-3IfIZnupQ)|xf7g|[ResNet50_GCP_LRadju_128](https://drive.google.com/open?id=1t6r70Vx4J7ev6Lhm0SAalptyF3gQ_5Qk)|

#### ResNet101
|Models|Top-1 acc.(%)|Top-5 acc.(%)|BaiduDrive(models)|Extract code|GoogleDrive|
|:-----|:-----------:|:-----------:|:-----------------|:----------:|:----------|
|ResNet101_GAP_LRnorm|&nbsp;&nbsp;&nbsp;77.67&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;93.83&nbsp;&nbsp;&nbsp;|[ResNet101_GAP_LRnorm](https://pan.baidu.com/s/19ptqTR4yZLDSotDimuUzbA)|3u9a|[ResNet101_GAP_LRnorm](https://drive.google.com/open?id=1N-Wu6VAiOHfD4DqbCm-IfupkxZWjUvTc)|
|ResNet101_GAP_LRfast|73.13|91.06|[ResNet101_GAP_LRfast](https://pan.baidu.com/s/1hlqHfkfbJH69PBxiq-kx3Q)|11g2|[ResNet101_GAP_LRfast](https://drive.google.com/open?id=1uXVyPGOTgBxwAl1gowyuCgcFRqXT3G0Y)|
|ResNet101_GAP_LRadju|77.53|93.53|[ResNet101_GAP_LRadju](https://pan.baidu.com/s/17Aw2IWHyJ9TwqTui1dpGkg)|nikb|[ResNet101_GAP_LRadju](https://drive.google.com/open?id=16JhBYDeQI6-kKAAILFDCfeoPt5nUVAv3)|
|ResNet101_GCP_LRnorm|79.47|94.71|[ResNet101_GCP_LRnorm](https://pan.baidu.com/s/1UVxS_HRrcFUZnYXKEoBU6A)|kr4s|[ResNet101_GCP_LRnorm](https://drive.google.com/open?id=1y8oI2IodJuG7R_gIdrYoXSTPafmszwMh)|
|ResNet101_GCP_LRfast|76.38|92.82|[ResNet101_GCP_LRfast](https://pan.baidu.com/s/1ubrAmWAIXKc_Yhia2jUeRA)|iy77|[ResNet101_GCP_LRfast](https://drive.google.com/open?id=1iLAV7Hu3jWTRINJ6wRumqkReZEpqubHr)|
|ResNet101_GCP_LRadju|79.18|94.47|[ResNet101_GCP_LRadju](https://pan.baidu.com/s/1GzT6IgwdhkFVwSfisl7j_w)|ytfb|[ResNet101_GCP_LRadju](https://drive.google.com/open?id=17lNCi6r8CXHM6-Z8Q7YckRReeZXsRQwQ)|

*If you would like to evaluate above pre-trained models, please do the following:

1. Download the pre-trained models.

2. Testing on ImageNet: In floder `src` , run ` sh ./scripts/val/val_download.sh` 

## Experiments on ImageNet-C and ImageNet-P

You can download the test code and the dateset from  [https://github.com/hendrycks/robustness](https://github.com/hendrycks/robustness)

### Result on ImageNet-C and ImageNet-P 

<table>
  <tr>
    <th rowspan="2">Method</th>
    <th colspan="2">IMAGENET-C</th>
    <th colspan="2">IMAGENET-P</th>
  </tr>
  <tr>
    <th>mCE</th>
    <th>Relative mCE</th>
    <th>mFP</th>
    <th>mT5D</th>
  </tr>
  <tr>
    <td align=left>MobileNetV2_GAP_LRnorm</td>
    <td>87.1</td>
    <td>114.9</td>
    <td>79.8</td>
    <td>96.5</td> 
  </tr>
  <tr>
    <td align=left>MobileNetV2_GCP_LRnorm</td>
    <td>81.7</td>
    <td>110.6</td>
    <td>64.3</td>
    <td>87.6</td> 
  </tr>
  <tr>
    <td align=left>ShuffleNetV2_GAP_LRnorm</td>
    <td>92.7</td>
    <td>126.7</td>
    <td>94.7</td>
    <td>108.2</td> 
  </tr>
  <tr>
    <td align=left>ShuffleNetV2_GCP_LRnorm</td>
    <td>85.2</td>
    <td>112.6</td>
    <td>75.2</td>
    <td>95.5</td> 
  </tr>
  <tr>
    <td align=left>ResNet18</td>
    <td>84.7</td>
    <td>103.9</td>
    <td>72.8</td>
    <td>87.0</td> 
  </tr>
  <tr>
    <td align=left>ResNet18_GCP_LRnorm</td>
    <td>76.3</td>
    <td>101.3</td>
    <td>53.2</td>
    <td>77.1</td> 
  </tr>
  <tr>
    <td align=left>ResNet34</td>
    <td>77.9</td>
    <td>98.7</td>
    <td>61.7</td>
    <td>79.5</td> 
  </tr>
  <tr>
    <td align=left>ResNet34_GCP_LRnorm</td>
    <td>72.4</td>
    <td>96.9</td>
    <td>47.7</td>
    <td>72.4</td> 
  </tr>
  <tr>
    <td align=left>ResNet50</td>
    <td>76.7</td>
    <td>105.0</td>
    <td>58.0</td>
    <td>78.3</td> 
  </tr>
  <tr>
    <td align=left>ResNet50_GCP_LRnorm</td>
    <td>70.7</td>
    <td>97.9</td>
    <td>47.5</td>
    <td>74.6</td> 
  </tr>
  <tr>
    <td align=left>ResNet101</td>
    <td>70.3</td>
    <td>93.7</td>
    <td>52.6</td>
    <td>73.9</td> 
  </tr>
  <tr>
    <td align=left>ResNet101_GCP_LRnorm</td>
    <td>65.5</td>
    <td>89.1</td>
    <td>42.1</td>
    <td>68.3</td> 
  </tr>
</table>

## Experiments on Object Detection and Instance Segmentation

We use the [mmdetection](https://github.com/open-mmlab/mmdetection) to test our models on Object Detection and Instance Segmentation.

### Object Detection Results on COCO val2017

#### Faster R-CNN

<table>
  <tr>
    <th>Backbone Model</th>
    <th>Method</th>
    <th>AP</th>
    <th>AP<sub>50</sub></th>
    <th>AP<sub>75</sub></th>
    <th>AP<sub>S</sub></th>
    <th>AP<sub>M</sub></th>
    <th>AP<sub>L</sub></th>
  </tr>
  <tr>
    <th rowspan="3">ResNet50</th>
    <td>GAP</td>
    <td>36.4</td>
    <td>58.2</td>
    <td>39.2</td>
    <td>21.8</td>
    <td>40.0</td>
    <td>46.2</td>
  </tr>
  <tr>
    <td>GCP<sub>D</sub></td>
    <td>36.6</td>
    <td>58.4</td>
    <td>39.5</td>
    <td>21.3</td>
    <td>40.8</td>
    <td>47.0</td>
  </tr>
  <tr>
    <td>GCP<sub>M</sub></td>
    <th>37.1</th>
    <th>59.1</th>
    <th>39.9</th>
    <th>22.0</th>
    <th>40.9</th>
    <th>47.6</th>
  </tr>
  <tr>
    <th rowspan="3">ResNet101</th>
    <td>GAP</td>
    <td>38.7</td>
    <td>60.6</td>
    <td>41.9</td>
    <td>22.7</td>
    <td>43.2</td>
    <td>50.4</td>
  </tr>
  <tr>
    <td>GCP<sub>D</sub></td>
    <td>39.5</td>
    <td>60.7</td>
    <td>43.1</td>
    <td>22.9</td>
    <th>44.1</th>
    <th>51.4</th>
  </tr>
  <tr>
    <td>GCP<sub>M</sub></td>
    <th>39.6</th>
    <th>61.2</th>
    <th>43.1</th>
    <th>23.3</th>
    <td>43.9</td>
    <td>51.3</td>
  </tr>
</table>

#### Mask R-CNN

<table>
  <tr>
    <th>Backbone Model</th>
    <th>Method</th>
    <th>AP</th>
    <th>AP<sub>50</sub></th>
    <th>AP<sub>75</sub></th>
    <th>AP<sub>S</sub></th>
    <th>AP<sub>M</sub></th>
    <th>AP<sub>L</sub></th>
  </tr>
  <tr>
    <th rowspan="3">ResNet50</th>
    <td>GAP</td>
    <td>37.2</td>
    <td>58.9</td>
    <td>40.3</td>
    <td>22.2</td>
    <td>40.7</td>
    <td>48.0</td>
  </tr>
  <tr>
    <td>GCP<sub>D</sub></td>
    <td>37.3</td>
    <td>58.8</td>
    <td>40.4</td>
    <td>22.0</td>
    <td>41.1</td>
    <td>48.2</td>
  </tr>
  <tr>
    <td>GCP<sub>M</sub></td>
    <th>37.9</th>
    <th>59.4</th>
    <th>41.3</th>
    <th>22.4</th>
    <th>41.5</th>
    <th>49.0</th>
  </tr>
  <tr>
    <th rowspan="3">ResNet101</th>
    <td>GAP</td>
    <td>39.4</td>
    <td>60.9</td>
    <td>43.3</td>
    <td>23.0</td>
    <td>43.7</td>
    <td>51.4</td>
  </tr>
  <tr>
    <td>GCP<sub>D</sub></td>
    <td>40.3</td>
    <td>61.5</td>
    <td>44.0</td>
    <th>24.1</th>
    <td>44.7</td>
    <td>52.5</td>
  </tr>
  <tr>
    <td>GCP<sub>M</sub></td>
    <th>40.7</th>
    <th>62.0</th>
    <th>44.6</th>
    <td>23.9</td>
    <th>45.2</th>
    <th>52.9</th>
  </tr>
</table>

### Instance Segmentation Result on COCO val2017

#### Mask R-CNN

<table>
  <tr>
    <th>Backbone Model</th>
    <th>Method</th>
    <th>AP</th>
    <th>AP<sub>50</sub></th>
    <th>AP<sub>75</sub></th>
    <th>AP<sub>S</sub></th>
    <th>AP<sub>M</sub></th>
    <th>AP<sub>L</sub></th>
  </tr>
  <tr>
    <th rowspan="3">ResNet50</th>
    <td>GAP</td>
    <td>34.1</td>
    <td>55.5</td>
    <td>36.2</td>
    <td>16.1</td>
    <td>36.7</td>
    <td>50.0</td>
  </tr>
  <tr>
    <td>GCP<sub>D</sub></td>
    <td>34.2</td>
    <td>55.3</td>
    <td>36.4</td>
    <td>15.8</td>
    <td>37.1</td>
    <td>50.1</td>
  </tr>
  <tr>
    <td>GCP<sub>M</sub></td>
    <th>34.7</th>
    <th>56.3</th>
    <th>36.8</th>
    <th>16.4</th>
    <th>37.5</th>
    <th>50.6</th>
  </tr>
  <th rowspan="3">ResNet101</th>
    <td>GAP</td>
    <td>35.9</td>
    <td>57.7</td>
    <td>38.4</td>
    <td>16.8</td>
    <td>39.1</td>
    <td>53.6</td>
  </tr>
  <tr>
    <td>GCP<sub>D</sub></td>
    <td>36.5</td>
    <td>58.2</td>
    <td>38.9</td>
    <td>17.3</td>
    <td>39.9</td>
    <td>53.5</td>
  </tr>
  <tr>
    <td>GCP<sub>M</sub></td>
    <th>36.7</th>
    <th>58.7</th>
    <th>39.1</th>
    <th>17.6</th>
    <th>39.9</th>
    <th>53.7</th>
  </tr>
</table>

### Our Pre-trained Models on Object Detection and Instance Segmentation

|Models|BaiduDrive(models)|Extract code|GoogleDrive|
|:-----|:-----------------|:----------:|:----------|
|ResNet18_GCP_D|[ResNet18_GCP_D]()|   |[ResNet18_GCP_D]()|
|ResNet18_GCP_Downsample|[ResNet18_GCP_Downsample]()|   |[ResNet18_GCP_Downsample]()|
|ResNet50_GAP|[ResNet50_GAP]()|   |[ResNet50_GAP]()|
|ResNet50_GCP_D|[ResNet50_GCP_D]()|   |[ResNet50_GCP_D]()|
|ResNet50_GCP_M|[ResNet50_GCP_M]()|   |[ResNet50_GCP_M]()|
|ResNet50_GCP_Downsample|[ResNet50_GCP_Downsample]()|   |[ResNet50_GCP_Downsample]()|
|ResNet101_GAP|[ResNet101_GAP]()|   |[ResNet101_GAP]()|
|ResNet101_GCP_D|[ResNet101_GCP_D]()|   |[ResNet101_GCP_D]()|
|ResNet101_GCP_M|[ResNet101_GCP_M]()|   |[ResNet101_GCP_M]()|
|ResNet101_GCP_Downsample|[ResNet101_GCP_Downsample]()|   |[ResNet101_GCP_Downsample]()|

## Acknowledgments
We would like to thank the team behind the [iSQRT-COV](https://github.com/jiangtaoxie/fast-MPN-COV), [ImageNet-C & ImageNet-P](https://github.com/hendrycks/robustness) and [mmdetection](https://github.com/open-mmlab/mmdetection) for providing a nice code, and our code is based on it.

## Contact
If you have any questions or suggestions, please feel free to contact us: qlwang@tju.edu.cn; li_zhang@tju.edu.cn.
