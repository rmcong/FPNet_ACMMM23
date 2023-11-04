# Frequency Perception Network for Camouflaged Object Detection

> **Authors:** [Runmin Cong](https://openreview.net/profile?id=\~Runmin_Cong1), [Mengyao Sun](https://openreview.net/profile?id=\~Mengyao_Sun1), [Sanyi Zhang](https://openreview.net/profile?id=\~Sanyi_Zhang1), [Xiaofei Zhou](https://openreview.net/profile?id=\~Xiaofei_Zhou2), [Wei Zhang](https://openreview.net/profile?id=\~Wei_Zhang7), and [Yao Zhao](https://openreview.net/profile?id=\~Yao_Zhao1).

## 1. Preface

*   This repository provides code for "***Frequency Perception Network for Camouflaged Object Detection***" ACM MM 2023. [Paper](https://openreview.net/pdf?id=ug66Ewg8bi)

## 2. Proposed Method

### 2.1. Training/Testing

The training and testing experiments are conducted using [PyTorch](https://github.com/pytorch/pytorch) with one NVIDIA 2080Ti GPU of 32 GB Memory.

The source code can be found from [Baidu Drive](https://pan.baidu.com/s/1g-2U2mO2nbrhuSI90uWQkQ?pwd=MVPL)，CODE: MVPL 

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

### 2.2 Evaluating your trained model:

One evaluation is written in Python code  please follow this the instructions in `./evaluator.py` and just run it to generate the evaluation results in. We implement four metrics: MAE (Mean Absolute Error), weighted F-measure, mean E-measure, S-Measure.

**[⬆ back to top](#1-preface)**
