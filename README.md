# Reproduction of 2020CVPR_IMODA

Hi! This my work on reproduction of the paper [Towards Inheritable Models for Open-set Domain Adaptation](https://arxiv.org/abs/2002.08546). The original code is [here](https://sites.google.com/view/inheritune). Although the code is detailed enough, some problems I faced are not to be ignored. 

**This is just for research and study. If there is any infringement, please tell me.**

## Some tips about python2->python3 in the original code
1. `.next() -> .__next__()`
2. `raw_input() -> input()`
3. When cuda is not compatible, use the command `conda install cudatoolkit=version`

## Step 1: Setup

`pip install -r requirements.txt`

`python create_dataset.py`

`python augment_dataset.py`

## Step 2: Train an Inheritable Model on the Source Domain
**Note**: Delete the files **spliced_m_feats.npy** and **spliced_m_kmeans_labels.npy** in the folder **code/inheritune_base**, between two sessions of inheritable model training.

### 2.1. Training command

`python Train_supervised.py`

### 2.2. Use tensorboard for vsualization

`cd summaries/experiment_name`

`tensorboard --logdir .`

**Note**: Because my server has a version incompatibility issue, I download the folder **summaries** and use the local tensorboard with the command `tensorboard --logdir=logdir_val`

### 2.3. Results(DtoA_vendor)

**1. train**

classification loss 

![](https://ftp.bmp.ovh/imgs/2020/12/f6e61091573d43d2.png)

source batch loss

![](https://ftp.bmp.ovh/imgs/2020/12/3821154e0e1099f9.png)

**2. validation**

source average

![](https://ftp.bmp.ovh/imgs/2020/12/eb58909ce42fba10.png)

## Step 3: Adapt to the Target Domain

### 3.1. Training command

`python Train_adapt.py`

### 3.2. Use tensorboard for visualization

`cd summaries/experiment_name`

`tensorboard --logdir .`

### 3.3. Results(DtoA_client)

**1. train**

target accuracy

![](https://ftp.bmp.ovh/imgs/2020/12/019b2c243eef2444.png)

adaptation loss

![](https://ftp.bmp.ovh/imgs/2020/12/1c600abe4ed6ec97.png)

pseudo labels classification loss

![](https://ftp.bmp.ovh/imgs/2020/12/4d11094f4e6867ba.png)

**2. validation**

os accuracy

![](https://ftp.bmp.ovh/imgs/2020/12/1bee424e031bb449.png)

priv accuracy

![](https://ftp.bmp.ovh/imgs/2020/12/8c440987c6d7e8fc.png)
