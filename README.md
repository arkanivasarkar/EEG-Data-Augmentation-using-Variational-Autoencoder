# EEG-Data-Augmentation-using-Variational-Autoencoder

"Improving performance of motor imagery classification using Variational-Autoencoder and synthetic EEG signals".

This repository contains the implementation of a variational autoencoder(VAE) for generating synthetic EEG signals. 
The generated signals were used for motor imagery classification using the EEGNet architecture[1].


The primary goals were:

    Construct artifical EEG data using two neural network models:
    i. Generative adverserial networks (GAN)
    ii. variational autoencoders (VAE).
    Examine how artifical EEG data affects motor imagery classification
    


![alt text](https://i.ibb.co/BKr7cVF/Picture1.png) 


Four architecures/models were made keeping U-NET architecture as the base.
The models used are:
- Simple U-NET
- Residual U-NET (Res-UNET)
- Attention U-NET
- Residual Attention U-NET (RA-UNET)

The performance metrics used for evaluation are accuracy and mean IoU.


## Methods
Images from HRF, DRIVE and STARE datasets are used for training and testing. The following pre-processing steps are applied before training the models:
- Green channel selection
- Contrast-limited adaptive histogram equalization (CLAHE)
- Cropping into non-overlapping patches of size 512 x 512

10 images from DRIVE and STARE and 12 images from HRF was kept for testing the models. The training dataset was then split into 70:30 ratio for training and validation.

Adam optimizer with a learning rate of 0.001 was used as optimizer and IoU loss was used as the loss function. The models were trained for 150 epochs with a batch size of 16, using NVIDIA Tesla P100-PCIE GPU. 

## Results
The performance of the models were evaluated using the test dataset.
Out of all the models, Attention U-NET achieved a greater segmentation performance. 


The following table compares the performance of various models

| **Datasets** |    **Models**    | **Average Accuracy**| **Mean IoU**|
|:------------:|:----------------:|:-------------------:|:-----------:|
| HRF          | Simple U-NET     | 0.965               |0.854        |
| HRF          | Res-UNET         | 0.964               |0.854        |
| HRF          | Attention U-NET  | 0.966               |0.857        |
| HRF          | RA-UNET          | 0.963               |0.85         |
| DRIVE        | Simple U-NET     | 0.9                 |0.736        |
| DRIVE        | Res-UNET         | 0.903               |0.741        |
| DRIVE        | Attention U-NET  | 0.905               |0.745        |
| DRIVE        | RA-UNET          | 0.9                 |0.735        |
| STARE        | Simple U-NET     | 0.882               |0.719        |
| STARE        | Res-UNET         | 0.893               |0.737        |
| STARE        | Attention U-NET  | 0.893               |0.738        |
| STARE        | RA-UNET          | 0.891               |0.733        |

![alt text](https://i.ibb.co/W07sGYv/Picture3.png)



### Datasets
The datasets of the fundus images can be acquired from:
1. [HRF](https://www5.cs.fau.de/research/data/fundus-images/)
2. [DRIVE](http://www.isi.uu.nl/Research/Databases/DRIVE/)
3. [STARE](https://cecas.clemson.edu/~ahoover/stare/)

The base project provided was to explore datasets collected from electroencephalography (EEG). The data is obtained from the BCI Competition IV, Data sets 2a. It consists of 22 EEG channels from 9 subjects performing 4 motor-imagery tasks. A more complete description of the data is available here: BCI Competition 2008 – Graz data set A.

The trained models are present in `Trained models` folder.



## References

[1] 
&nbsp;
&nbsp;
&nbsp;
&nbsp;



