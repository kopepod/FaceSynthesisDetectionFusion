# BayesianFusion

<img src="https://github.com/kopepod/FaceSynthesisDetectionFusion/blob/main/Pipeline.png" width="1200" height="200" />

[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1elztvJ-Wz1qsFMH2T-uc1y-V-7-3An7i)
[![arXiv](https://img.shields.io/badge/arXiv-1234.56789-b31b1b.svg)](https://arxiv.org/abs/2401.04257)

This is the implementation of the paper entitled _Detecting Face Synthesis Using a Concealed Fusion Model_ this repository is divided as follows:

1. Create Environment
2. Dataset
3. Train Models
4. Test Models

## Create Environment

To create the environment you have to install [anaconda](https://www.anaconda.com/download) and run the following command:
```bash
conda env create -f environment.yml
```
You should be able to run this command:
```bash
conda run -n bayesianfusion python --version
```
## Dataset

It is necessary to download the [FFHQ](https://github.com/NVlabs/ffhq-dataset) dataset from the original authors. Create the following structure with the Real and Synthetic Images:

```bash
tree
.
└── FFHQ
    ├── Fake
    │       ├── seed0000.png
    │       ├── seed0001.png
    │       └── seed0002.png
    └── Real
            ├── 00000.png
            ├── 00001.png
            └── 00002.png
```
Where the Real is the folder comprises the FFHQ samples and the Fake the ones generated from the synthesizer, respectively.

## Train Models

The model bank requires training separately each feature model and then produce the scores individually.

We can pass specific parameters to train the models. Running the following command you will observe what the parameters control.

```bash
python Main.py TrainModel  --help 

usage: Fake Synthesis Detection via Late Fusion TrainModel [-h] [--Epochs EPOCHS] [--LR LR] [--DB DB] [--Split SPLIT] [--dbn_samples DBN_SAMPLES]
                                                           [--minacc MINACC] [--PolDegreeRange POLDEGREERANGE] [--Visualize VISUALIZE]

This code trains a model from binary labels

options:
  -h, --help            show this help message and exit
  --Epochs EPOCHS
  --LR LR               Fusion Model learning rate
  --DB DB
  --Split SPLIT         Training testing set size
  --dbn_samples DBN_SAMPLES
                        Bayesian model samples to map
  --minacc MINACC       Minimum acceptable fusion model accuracy
  --PolDegreeRange POLDEGREERANGE
                        Polinomia degree range
  --Visualize VISUALIZE
                        Visualize polinoma

```




