

![image](https://github.com/Paper-ID-1349/CD-FSOD/blob/main/figures/figure1.png)

### Introduction
This repo contains the official PyTorch implementation of our paper CD-FSOD: A Benchmark for Cross-domain Few-shot Object Detection.


### Datasets


#### Source domain: 

* [MS COCO](https://cocodataset.org/#home)

#### Target domains: 

* [ArTaxOr](https://www.kaggle.com/datasets/mistag/arthropod-taxonomy-orders-object-detection-dataset)

* [UODD](https://github.com/LehiChiang/Underwater-object-detection-dataset)

* [DIOR](https://drive.google.com/drive/folders/1UdlgHk49iu6WpcJ5467iT-UqNPpx__CC)


#### Dataset Statistics

| Dataset | classses | train images | test images |
| :-----: | :----: | :----: | :----: |
| ArTaxOr | 7 | 13,991 | 1,383 |
| UODD | 3 | 3,194 | 506 |
| DIOR | 20 | 18,463 | 5,000 |

### Baselines

Under the proposed benchmarks, we evaluate existing FSOD methods, including meta-learning methods and fine-tuning methods.  We use their official implementation.

#### Meta-learning methods
* [A-RPN](https://github.com/fanq15/FewX) [5]
* [H-GCN](https://github.com/GuangxingHan/QA-FewDet) [6]
* [Meta-RCNN ](https://github.com/guangxinghan/meta-faster-r-cnn) [7]

#### Fine-tuned methods
*  [TFA](https://github.com/ucbdrive/few-shot-object-detection) [8]
*  [FSCE](https://github.com/megvii-research/FSCE) [9]
*  [DeFRCN](https://github.com/er-muyue/DeFRCN) [10]

## Quick Start

#### 1. Check Requirements.
* python >= 3.8
* detectron2 == 0.6
* PyTorch >= 1.10 & torchvision that matches the PyTorch version.
* CUDA==11.3
* GCC >= 5.4

#### 2. Build Environment

* Clone Code

```
git clone https://github.com/Paper-ID-1349/CD-FSOD.git
cd CD-FSOD
```

* Install PyTorch 1.10 with CUDA 11.3

```
conda install pytorch==1.9.0 torchvision==0.10.0 torchaudio==0.9.0 cudatoolkit=11.3 -c pytorch -c conda-forge
```

* Install [Detectron2](https://github.com/facebookresearch/detectron2)

```
python -m pip install detectron2 -f https://dl.fbaipublicfiles.com/detectron2/wheels/cu113/torch1.10/index.html
```

* Install other requirements.
 
 ```
python -m pip install -r requirements.txt
```

#### 3. Prepare Data and Weights

* Data Preparation
    * Data splits. Download the preprocessed datasets and splits from here([Goodle Drive](https://drive.google.com/file/d/1C-_V6wBO--m_Qy1ll2WXmWb0VaeWDVPU/view?usp=sharing), or [Baidu Wangpan](https://pan.baidu.com/s/1Pi2no3cpx8P_y0zjGrNMrA)(password: uer8))
    * Unzip the downloaded data-source to datasets and put it into your project directory:

     ```
     ...
     datasets
       | -- coco (train2017/*.jpg, val2017/*.jpg, annotations/*.json)
       | -- ArTaxOr (train/*.jpg, test/*.jpg, annotations/*.json)
       | -- UOOD (train/*.jpg, test/*.jpg, annotations/*.json)
       | -- DIOR (train/*.jpg, test/*.jpg, annotations/*.json)
     net
     train_net.py
     ...
     ```

* Weights Preparation
  * We use the MS COCO pretrain weights to initialize our model. Download the pretrain weights from [here](https://github.com/facebookresearch/detectron2/blob/main/MODEL_ZOO.md) (R50-FPN	with 3x)


#### 4. Training and Evaluation

```
    bash run.sh [dataset]
```
    
For example:

```
    bash run.sh DIOR
```


#### Acknowledgement
This repo is developed based on [Detectron2](https://github.com/facebookresearch/detectron2). Please check them for more details and features.


#### References

[1] Lin, Tsung-Yi, et al. "Microsoft coco: Common objects in context." ECCV 2014.

[2] https://www.kaggle.com/datasets/mistag/arthropod-taxonomy-orders-object-detection-dataset

[3] Jiang, Lihao, et al. "Underwater species detection using channel sharpening attention." ACM MM 2021.

[4] Li, Ke, et al. "Object detection in optical remote sensing images: A survey and a new benchmark." ISPRS J. Photogramm. Remote Sens. 2020).

[5] Fan, Qi, et al. "Few-shot object detection with attention-RPN and multi-relation detector." CVPR 2020.

[6] Han, Guangxing, et al. "Query adaptive few-shot object detection with heterogeneous graph convolutional networks." ICCV 2021.

[7] Han, Guangxing, et al. "Meta faster r-cnn: Towards accurate few-shot object detection with attentive feature alignment." AAAI 2022.

[8]  Wang, Xin, et al. "Frustratingly Simple Few-Shot Object Detection." ICML 2020.

[9] Sun, Bo, et al. "Fsce: Few-shot object detection via contrastive proposal encoding." CVPR 2021.

[10] Qiao, Limeng, et al. "Defrcn: Decoupled faster r-cnn for few-shot object detection." ICCV 2021.
