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

### 2.3. Results

## Step 3: Adapt to the Target Domain

### 3.1. Training command

`python Train_adapt.py`

### 3.2. Use tensorboard for visualization

`cd summaries/experiment_name`

`tensorboard --logdir .`

### 3.3. Results
**acc_os**

![acc_os](https://ftp.bmp.ovh/imgs/2020/12/cd97cacc5a6c53f7.png)

**acc_priv**

![acc_priv](https://ftp.bmp.ovh/imgs/2020/12/d61e7374864d3a79.png)

