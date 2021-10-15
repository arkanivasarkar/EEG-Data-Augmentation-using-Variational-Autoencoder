# Improving performance of motor imagery classification using Variational-Autoencoder and synthetic EEG signals.

This repository contains the implementation of a variational autoencoder(VAE) for generating synthetic EEG signals. 
The generated signals were used for motor imagery classification using the [EEGNet](https://www.researchgate.net/publication/310953136_EEGNet_A_Compact_Convolutional_Network_for_EEG-based_Brain-Computer_Interfaces) architecture.


The primary goals were:

    Construct artifical EEG data using two neural network models:
    i. Generative adverserial networks (GAN)
    ii. variational autoencoders (VAE).
    Examine how artifical EEG data affects motor imagery classification
    




Four architecures/models were made keeping U-NET architecture as the base.
The models used are:
- Simple U-NET
- Residual U-NET (Res-UNET)
- Attention U-NET
- Residual Attention U-NET (RA-UNET)


## Dataset
The dataset is obtained from the [BCI Competition IV](http://www.bbci.de/competition/iv/#datasets) - Data sets 2a. It consists of 22 EEG channels signals of sampling rate 250Hz, from 9 subjects. The signals are of 0.5-100 Hz and are filtered with a notch filter. There are 4 classes of motor-imagery tasks .




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









## References

1. Lawhern, Vernon & Solon, Amelia & Waytowich, Nicholas & Gordon, Stephen & Hung, Chou & Lance, Brent. (2016). EEGNet: A Compact Convolutional Network for EEG-based Brain-Computer Interfaces. Journal of Neural Engineering. 15. 10.1088/1741-2552/aace8c. 
&nbsp;
&nbsp;
&nbsp;
&nbsp;


