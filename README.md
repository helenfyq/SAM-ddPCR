# SAM-dPCR
SAM-dPCR is a deep-learning assisted bioanalysis tool, developed for rapid and accruate quantification of biological models. Its applications include image analysis of droplet-PCR and microwell-PCR of samples such as agarose and bacteria. Below is a structured guide of how to implement SAM-dPCR on a standard desktop computer, and use it to analyse laboratory images, thus speeding up the bio-analysis process.  
## System requirements
### Hardware requirements
The system requires no non-standard hardware and could run on standard desktop computers. It could operate without a GPU, while implementing one would decrease the expected run time.
### Software requirements
#### OS requirements
This package is supported for *MacOS*, *Windows* and *Linux*. It had been tested on the systems listed below:
1. *macOS*: Ventura 13.0 & Sonoma 14.2.1
2. *Windows*: 11 Home 22H2
#### Environment dependencies
The Segment-Anything Model depends on the following python environment to run:
python>=3.8
pytorch>=1.7
torchvision>=0.8
OpenCV-Python
Pycocotools
Matplotlib
ONNX Runtime
ONNX

The SAM-dPCR package depends on the following packages to run:
1.Visualize: C:\Users\Yuanyuan\OneDrive - The Chinese University of Hong Kong\SAM_dPCR\Python codes\SAM-dPCR DL model\visualize.py
2.Plot: C:\Users\Yuanyuan\OneDrive - The Chinese University of Hong Kong\SAM_dPCR\Python codes\SAM-dPCR DL model\plot.py
3.Setup: C:\Users\Yuanyuan\OneDrive - The Chinese University of Hong Kong\SAM_dPCR\Python codes\SAM-dPCR DL model\setup.py

## Demo
### Expected run time for demo on a "normal" desktop computer
Without GPU: approximately 45s per image 
Utilizing GPU: <4s per image
