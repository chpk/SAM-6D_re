## This repo is Forked from the original SAM-6D repository to rectify and deal with majority of the issues faced with the original repo. the setup.pu in `Pose_Estimation_Model/modelpointnet2/` location has been modified to deal with with pointnet2 model installation. Also, the `environment.yaml` file has been modified to work with latest CUDA version and also to deal with the CUDA mismatch errors. Also the model execution instructions were made clear w.r.t. input paths for the SAM-6D model.


# <p align="center"> <font color=#008000>SAM-6D</font>: Segment Anything Model Meets Zero-Shot 6D Object Pose Estimation </p>

####  <p align="center"> [Jiehong Lin](https://jiehonglin.github.io/), [Lihua Liu](https://github.com/foollh), [Dekun Lu](https://github.com/WuTanKun), [Kui Jia](http://kuijia.site/)</p>
#### <p align="center">CVPR 2024 </p>
#### <p align="center">[[Paper]](https://arxiv.org/abs/2311.15707) </p>

<p align="center">
  <img width="100%" src="https://github.com/JiehongLin/SAM-6D/blob/main/pics/vis.gif"/>
</p>

## Update Log
- [2024/03/05] We update the demo to support [FastSAM](https://github.com/CASIA-IVA-Lab/FastSAM), you can do this by specifying `SEGMENTOR_MODEL=fastsam` in demo.sh.
- [2024/03/03] We upload a [docker image](https://hub.docker.com/r/lihualiu/sam-6d/tags) for running custom data.
- [2024/03/01] We update the released [model](https://drive.google.com/file/d/1joW9IvwsaRJYxoUmGo68dBVg-HcFNyI7/view?usp=sharing) of PEM. For the new model, a larger batchsize of 32 is set, while that of the old is 12. 

## Overview
In this work, we employ Segment Anything Model as an advanced starting point for **zero-shot 6D object pose estimation** from RGB-D images, and propose a novel framework, named **SAM-6D**, which utilizes the following two dedicated sub-networks to realize the focused task:
- [x] [Instance Segmentation Model](https://github.com/JiehongLin/SAM-6D/tree/main/SAM-6D/Instance_Segmentation_Model)
- [x] [Pose Estimation Model](https://github.com/JiehongLin/SAM-6D/tree/main/SAM-6D/Pose_Estimation_Model)


<p align="center">
  <img width="50%" src="https://github.com/JiehongLin/SAM-6D/blob/main/pics/overview_sam_6d.png"/>
</p>


## Getting Started

### 1. Preparation
Please clone the repository locally:
```
git clone https://github.com/chpk/SAM-6D_re.git 
```
Install the environment and download the model checkpoints:
```
cd SAM-6D
sh prepare.sh
```

### 2. Evaluation on the custom data
```
# set the paths
export CAD_PATH=    # absolute path to a given cad model(mm) at -- Data/Example/obj_000005.ply
export RGB_PATH=          # absolute path to a given RGB image at -- Data/Example/rgb.png  
export DEPTH_PATH=       # absolute path to a given depth map(mm) at -- Data/Example/depth.png
export CAMERA_PATH=    # absolute path to given camera intrinsics in -- Data/Example/camera.json
export OUTPUT_DIR=         # absolute path to a pre-defined file for saving results at -- Data/Example/outputs

# run inference

# be carefull with your blenderproc installation, if faced with any issue (typically 403 error), download the blender software and pass it's path using this additional argument --custom_blender_path
cd SAM-6D
sh demo.sh

# all you results will be saved to Data/Example/outputs
```



## Citation
If you find our work useful in your research, please consider citing:

    @article{lin2023sam,
    title={SAM-6D: Segment Anything Model Meets Zero-Shot 6D Object Pose Estimation},
    author={Lin, Jiehong and Liu, Lihua and Lu, Dekun and Jia, Kui},
    journal={arXiv preprint arXiv:2311.15707},
    year={2023}
    }

