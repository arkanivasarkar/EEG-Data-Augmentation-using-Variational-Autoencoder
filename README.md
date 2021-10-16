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

|              | **Precision** | **recall** | **f1-score** |
|:------------:|:-------------:|:----------:|:------------:|
| 0            | 0.81          | 0.74       | 0.78         |
| 1            | 0.70          | 0.81       | 0.75         |
| 2            | 0.64          | 0.68       | 0.66         |
| 3            | 0.80          | 0.68       | 0.74         |

**Accuracy :** 0.73


|              | **Precision** | **recall** | **f1-score** |
|:------------:|:-------------:|:----------:|:------------:|
| 0            | 1.00          | 0.52       | 0.69         |
| 1            | 0.89          | 0.92       | 0.90         |
| 2            | 0.90          | 0.98       | 0.94         |
| 3            | 0.82          | 1.00       | 0.90         |

**Accuracy :** 0.88









## References

1. Lawhern, Vernon & Solon, Amelia & Waytowich, Nicholas & Gordon, Stephen & Hung, Chou & Lance, Brent. (2016). EEGNet: A Compact Convolutional Network for EEG-based Brain-Computer Interfaces. Journal of Neural Engineering. 15. 10.1088/1741-2552/aace8c. 
2. Aznan, Nik & Atapour Abarghouei, Amir & Bonner, Stephen & Connolly, Jason & Al Moubayed, Noura & Breckon, Toby. (2019). Simulating Brain Signals: Creating Synthetic EEG Data via Neural-Based Generative Models for Improved SSVEP Classification. 

&nbsp;
&nbsp;
&nbsp;


