# **Table of Contents**

[TOCM]

[TOC]

# SAM-dPCR
SAM-dPCR is a deep-learning assisted bioanalysis tool, developed for rapid and accruate quantification of biological models. Its applications include image analysis of droplet-PCR and microwell-PCR of samples such as agarose and bacteria. Below is a structured guide of how to implement SAM-dPCR on a standard desktop computer, and use it to analyse laboratory images, thus speeding up the bio-analysis process. 


## System requirements
### Hardware requirements
The system requires no non-standard hardware and could run on standard desktop computers. It could operate without a GPU, while implementing one would decrease the expected run time.
### Software requirements
#### OS requirements:
**This package is supported for *MacOS*, *Windows* and *Linux*. It had been tested on the systems listed below:**
1. *macOS*: Ventura 13.0 & Sonoma 14.2.1
2. *Windows*: 11 Home 22H2
#### Environment dependencies:
**The Segment-Anything Model depends on the following python environment to run:**
- python>=3.8
- pytorch>=1.7
- torchvision>=0.8
- OpenCV-Python
- Pycocotools
- Matplotlib
- ONNX Runtime
- ONNX
  
- **Details could be found in the README file in this folder: https://mycuhk-my.sharepoint.com/:f:/g/personal/1155118045_link_cuhk_edu_hk/EhtR4c0tv3pFuA9Fq9bR-zcBsSB42pe_choK7oZ71k1kLw?e=UI1Pom**

## Installation guide
### Creating a Conda Environment for SAM-dPCR
You can create a conda environment for Sam by following the steps below:

1. **Locate the yml file**: Find the conda `samdpcr.yml` file in the project directory. This file contains the necessary dependencies for the environment.

2. **Create the environment**: Use the following command in your terminal to create a new conda environment:
`conda env create -f samdpcr.yml`

3. **Activate the environment**: Once the environment is created, you can activate it using:
`conda activate samdpcr`

### Steps to Install Requirements
Follow the steps below to install the requirements:

1. **Locate the requirements file**: Find the `samdpcr_requirements.txt` file in the project directory. This file contains the necessary packages for the project.

2. **Install the requirements**: Use the following command in your terminal to install the requirements:
`pip install -r samdpcr_requirements.txt`

3. **Download SAM checkpoint**: Make sure you have downloaded `sam_vit_h_4b8939.pth` and put it under the folder of `samdpcr`. You can download it from [here](https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth "here"). If you want to use your own checkpoint, please modify the checkpoint path in the `main.py` on line 8, and change the relative `model_type` on line 9.

Please ensure that you have the correct permissions to install packages on your system. If you encounter any issues, you may need to use `sudo` or consult your system's documentation.

### (optional) Steps to Set Up CUDA

Follow the steps below to set up CUDA to run the code faster:

1. **Check your system compatibility**: Ensure that your system has a CUDA-compatible GPU. You can check this on the NVIDIA website.

2. **Install PyTorch for CUDA**: If you wish to use GPU acceleration, install the appropriate version of PyTorch for CUDA. Follow the instructions provided on the [official website](http://https://pytorch.org/get-started/locally/ "official website") to do this.

3.**Modify the code**: Change line 10 `device = "cpu"` to `device = "cuda"` in the `main.py`.

Please note that using CUDA is optional for this project. If you do not have a CUDA-compatible GPU or do not wish to use GPU acceleration, you can use the CPU version of our project.

## Instructions for use
### Steps to Run the Code
Follow the steps below to run the code:

1. **Locate the Python file**: Find the `main.py` file in the project directory:
`cd samdpcr`

2. **Modify the input and output directories**: In `main.py`, replace the values of `inputDirectory` and `outputDirectory` on lines 16 and 17 with your desired input and output paths. The pre-set values are set to a demo path.

3. **Run the code**: Use the following command in your terminal to run the code:
`python main.py`

*- **Special Note**：When running **different concentrations** samples, using the **S channel** is preferred over the **V channel**. To do this, simply change line 81 in `visualize.py` from:*
```python
imgSatu = hsv_targetImage[:, :, 2]
```
*to:*
```python
imgSatu = hsv_targetImage[:, :, 1]
```
*In all other cases, the default initial setting `imgSatu = hsv_targetImage[:, :, 2]` is more optimal.*

## Demo
- For SAM-dPCR: Demo images have been placed in `data/test/files`. After installation progress, simply run `python main.py`, the output files will be loaded to both `data/test/files` and `data/test/outputfiles `.

- For Deep-qGFP: Same demo images have been placed in `data/test/files`. After installation progress, simply run `python detect_LabelsOutput.py`, the output files will be loaded to `runs/detect/exp`.
*Instructions on Deep-qGFP is given below for further reference.

### Expected run time for demo on a "normal" desktop computer (SAM-dPCR)
- Without GPU: approximately 45s per image 
- Utilizing GPU: <4s per image

------------

# Deep-qGFP
> To compare the performance of SAM-dPCR, we also provide the installation and operation mode of Deep-qGFP.

## System requirements

### Creating a Conda Environment for Deep-qGFP
You can create a conda environment for Deep-qGFP by following the steps below:

1. **Locate the yml file**: Find the conda `deepqgfp.yml` file in the project directory. This file contains the necessary dependencies for the environment.

2. **Create the environment**: Use the following command in your terminal to create a new conda environment:
`conda env create -f deepqgfp.yml`

3. **Activate the environment**: Once the environment is created, you can activate it using:
`conda activate deepqgfp`

## Installation guide
Follow the steps below to install the requirements:

1. **Locate the requirements file**: Find the `deepqgfp_requirements.txt` file in the project directory. This file contains the necessary packages for the project.

2. **Install the requirements**: Use the following command in your terminal to install the requirements:
`pip install -r deepqgfp_requirements.txt`

Please ensure that you have the correct permissions to install packages on your system. If you encounter any issues, you may need to use `sudo` or consult your system's documentation.

### optional) Steps to Set Up CUDA

Follow the steps below to set up CUDA:

1. **Check your system compatibility**: Ensure that your system has a CUDA-compatible GPU. You can check this on the NVIDIA website.

2. **Install PyTorch for CUDA**: If you wish to use GPU acceleration, install the appropriate version of PyTorch for CUDA. Follow the instructions provided on the [official website](http://https://pytorch.org/get-started/locally/ "official website") to do this.

3.**Modify the code**: Change line 64 `device='cuda device, i.e. 0 or 0,1,2,3 or cpu'` in `detect_LabelsOutput.py`. Or add `--device 'cuda device, i.e. 0 or 0,1,2,3 or cpu' ` in the command line.

Please note that using CUDA is optional for this project. If you do not have a CUDA-compatible GPU or do not wish to use GPU acceleration, you can use the CPU version of our project.

## Instructions for use
### Steps to Run the Code
Follow the steps below to run the code:

1. **Locate the Python file**: Find the `detect_LabelsOutput.py` file in the project directory:
`cd deepqgfp`

2. **(Optional) Modify the input directories**: In `detect_LabelsOutput.py`, replace the values of `source` and `default` on lines 58 and 248 with your desired input path. The pre-set values are set to a demo path. The default output path is `/runs/detect/exp(number)`, the number will automatically increased to avoid name conflict. If you want to change the name of the output path, you can simply replace the values of `project`, `name` and `default` on lines 75, 76, 265 and 266 with your desired output path *(project=output path, name=output folder under the output path, save results to project/name)*.

3. **Run the code**: Use the following command in your terminal to run the code if you follow the step 2 :
`python detect_LabelsOutput.py`
**else:**
`python detect_LabelsOutput.py --source input_directory --project output_path --name output_folder_name --device 'cuda device, i.e. 0 or 0,1,2,3 or cpu' `

