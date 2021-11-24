# AdaNEC

The implementation of Anonymous Submission 3582 "[Adaptive Network Combination for Single-Image Reflection Removal: A Domain Generalization Perspective](https://github.com/Anonymous3582/AdaNEC)"


## Envoronment

This repo has been tested in the following environment
* Platforms: Ubuntu 20.04
* Framework: We use PyTorch 1.8, and it should work with PyTorch 1.2 - PyTorch 1.10
* Requirements: opencv-python, tensorboardX, visdom, dominate, scikit-image, etc
* GPU: We use RTX 3090 with CUDA 11


## Quick Start

### Downloading this repository
We provide the pre-trained model via git-lfs (large file support), please clone this repository via one of the following methods.
1) `git lfs clone https://github.com/Anonymous3582/AdaNEC` or
2) `git clone https://github.com/Anonymous3582/AdaNEC`, then download the pre-trained model from [this page](./checkpoints/ERRNet_AdaNEC_OF/final_release.pt), and place it in the `checkpoints/ERRNet_AdaNEC_OF` folder.

### Preparing your testing datasets

Note that we have provided the *Real20* testing set in the `datasets` folder, and the *SIR^2* subsets are not provided due to their policy. You can request for them and organize the *SIR^2* sub-datasets as *Real20*.
* 20 real testing images from [Berkeley real dataset](https://github.com/ceciliavision/perceptual-reflection-removal).
* Three sub-datasets, namely *Objects*, *Postcard*, *Wild* from [SIR^2 dataset](https://sir2data.github.io/)

### Testing
We provide two working schemes of AdaNEC, i.e., output fusion (OF) and network interpolation (NI).

#### Output Fusion (OF)
The OF model has been provided, you can run the OF scheme via
```shell
$ bash test_AdaNEC_OF.sh
```

#### Network Interpolation (NI)
The NI model can be generated by running `python merge_model.py` under the `checkpoints/ERRNet_AdaNEC_NI` directory.
And then the NI scheme can be excueted via
```shell
$ bash test_AdaNEC_NI.sh
```
Particularly note that you should generate an NI model for each testing dataset. Please see [`merge_model.py`](./checkpoints/ERRNet_AdaNEC_NI/merge_model.py) for more details.

### Results
The results will be placed in the `results` folder.

## Acknowledgments
The code is built upon [ERRNet](https://github.com/Vandermode/ERRNet), one of the backbone models of our work. We will include their github commits when releasing the code publicly.
We highly appreciate all the authors of [ERRNet](https://github.com/Vandermode/ERRNet), [IBCLN](https://github.com/JHL-HUST/IBCLN), and [RAGNet](https://github.com/liyucs/RAGNet) for their efforts.
