# Frequency Perception Network for Camouflaged Object Detection

> **Authors:** [Runmin Cong](https://openreview.net/profile?id=\~Runmin_Cong1), [Mengyao Sun](https://openreview.net/profile?id=\~Mengyao_Sun1), [Sanyi Zhang](https://openreview.net/profile?id=\~Sanyi_Zhang1), [Xiaofei Zhou](https://openreview.net/profile?id=\~Xiaofei_Zhou2), [Wei Zhang](https://openreview.net/profile?id=\~Wei_Zhang7), and [Yao Zhao](https://openreview.net/profile?id=\~Yao_Zhao1).

## 1. Preface

*   This repository provides code for "***Frequency Perception Network for Camouflaged Object Detection***" ACM MM 2023. [Paper](https://openreview.net/pdf?id=ug66Ewg8bi)

## 2. Overview

### 2.1. Introduction

Camouflaged object detection (COD) aims to accurately detect objects hidden in the surrounding environment. However, the existing COD methods mainly locate camouflaged objects in the RGB domain, their performance has not been fully exploited in many challenging scenarios. Considering that the features of the camouflaged object and the background are more discriminative in the frequency domain, we propose a novel learnable and separable frequency perception mechanism driven by the semantic hierarchy in the frequency domain. Our entire network adopts a two-stage model, including a frequency-guided coarse localization stage and a detail-preserving fine localization stage. With the multi-level features extracted by the backbone, we design a flexible frequency perception module based on octave convolution for coarse positioning. Then, we design the correction fusion module to step-by-step integrate the high-level features through the prior-guided correction and cross-layer feature channel association, and finally combine them with the shallow features to achieve the detailed correction of the camouflaged objects. Compared with the currently existing models, our proposed method achieves competitive performance in three popular benchmark datasets both qualitatively and quantitatively.

### 2.2. Framework Overview

<p align="center">
    <img src="https://note.youdao.com/yws/res/136/WEBRESOURCEa2387a331965f119e5af32e433315976" width="70%" /> <br />
</p>

***Figure1:*** The overview of our proposed two-stage network FPNet. The input image is first extracted with multi-level features by a PVT encoder. In the frequency-guided coarse localization stage, we use FPM for frequency-domain feature extraction and generate the coarse COD map `$S_1$`. Then, in the detail-preserving fine localization stage, the CFM is used to chieve progressively prior-guided correction and fusion across high-level layers. Finally, the first-level high-resolution features are further introduced to refine the boundaries of camouflaged objects and generate the final result `$S_{output}$`.

### 2.3. Qualitative Results

<p align="center">
    <img src="https://note.youdao.com/yws/res/82/WEBRESOURCE2345c3359dd950f97cdcaf58e4d04fc5" width="70%" /> <br />
</p>

***Figure2:*** Qualitative results of our proposed FPNet model and some state-of-the-art COD methods. The images from left to right are (a) Input image, (b) GT, (c) Ours, (d) FreNet, (e) SINet-V2, (f) PFNet, (g) LSR, and (h) PraNet.

## 3. Proposed Method

### 3.1. Training/Testing

The training and testing experiments are conducted using [PyTorch](https://github.com/pytorch/pytorch) with one NVIDIA 2080Ti GPU of 32 GB Memory.

1.  Configuring your environment (Prerequisites):

    *   Installing necessary packages:&#x20;

        python 3.6&#x20;

        torch 1.11.0

        numpy 1.22.4

        mmcv-full 1.7.1

        timm 0.6.13

        mmdet 2.19.1

2.  Downloading necessary data:

    *   downloading dataset and move it into `./data/`, which can be found from [Baidu Drive](https://pan.baidu.com/s/15ro0EjyKKqPLRFVs8g865w?pwd=sm2e).

    *   downloading our weights and move it into `./snapshot/FPNet-GroupInsert/FPNet.pth`.&#x20;

    *   downloading PVTv1-Large weights and move it into `./lib/models/pvt_large.pth`.

3.  Training Configuration:

    *   After you download training dataset, just run `MyTrain_Val.py` to train our model.

4.  Testing Configuration:

    *   After you download all the pre-trained model and testing dataset, just run `MyTesting.py` to generate the final prediction maps.

    *   You can also download prediction maps ('CHAMELEON', 'CAMO', 'COD10K') from [Baidu Drive](https://pan.baidu.com/s/1qCS-NFUpSMIEqAM4i1Q4eg?pwd=2023).

### 3.2 Evaluating your trained model:

One evaluation is written in Python code  please follow this the instructions in `./evaluator.py` and just run it to generate the evaluation results in. We implement four metrics: MAE (Mean Absolute Error), weighted F-measure, mean E-measure, S-Measure.

**[⬆ back to top](#1-preface)**
