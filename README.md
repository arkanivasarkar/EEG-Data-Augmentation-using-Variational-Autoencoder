# EEG Data Augmentation using Variational Autoencoder 

This repository contains the implementation of a variational autoencoder (VAE) for generating synthetic EEG signals, and investigating how the generated signals can affect the performance of motor imagery classification. 
It is referred by the literature - Ahuja, C., & Sethia, D. (2024). Harnessing Few-Shot Learning for EEG signal classification: a survey of state-of-the-art techniques and future directions. Frontiers in human neuroscience, 18, 1421922. https://doi.org/10.3389/fnhum.2024.1421922
</br>

## Dataset
The dataset is obtained from [BCI Competition IV - Data sets 2a](http://www.bbci.de/competition/iv/#datasets). It consists of 22 channels EEG data of 9 subjects with 4 different classes of motor-imagery tasks. The signals are of 0.5-100 Hz, with a sampling rate 250Hz, and are filtered with a notch filter.
</br>

## Methods
The EEG signals acquired from the dataset were augmented using a variational autoencoder (VAE). It was seen that a 2D CNN based VAE performs better than a 1D CNN based VAE for this case. The augmented EEG signals were saved and later used for training the classifier.

The [EEGNet](https://www.researchgate.net/publication/310953136_EEGNet_A_Compact_Convolutional_Network_for_EEG-based_Brain-Computer_Interfaces) architecture was used for performing motor imagery classification. Two EEGNet models were trained, one with the actual EEG signals from the dataset and one with the generated signals, and their classification performances were tested using a test dataset from the same origin.

All models were trained using NVIDIA MX-150 GPU. 
</br>

## Results
The classification performances using original as well as augmented signals are shown below.

- Performance when trained with actual signals:

|              | **Precision** | **recall** | **f1-score** |
|:------------:|:-------------:|:----------:|:------------:|
| 0            | 0.81          | 0.74       | 0.78         |
| 1            | 0.70          | 0.81       | 0.75         |
| 2            | 0.64          | 0.68       | 0.66         |
| 3            | 0.80          | 0.68       | 0.74         |

**Accuracy :** 0.73
</br>
</br>
- Performance when trained with generated signals:

|              | **Precision** | **recall** | **f1-score** |
|:------------:|:-------------:|:----------:|:------------:|
| 0            | 1.00          | 0.52       | 0.69         |
| 1            | 0.89          | 0.92       | 0.90         |
| 2            | 0.90          | 0.98       | 0.94         |
| 3            | 0.82          | 1.00       | 0.90         |

**Accuracy :** 0.88

It can be seen that the classifcation performance is increased when augmented EEG data is used for training the classifier.
</br>

## References

1. Lawhern, Vernon & Solon, Amelia & Waytowich, Nicholas & Gordon, Stephen & Hung, Chou & Lance, Brent. (2016). EEGNet: A Compact Convolutional Network for EEG-based Brain-Computer Interfaces. Journal of Neural Engineering. 15. 10.1088/1741-2552/aace8c. 
2. Aznan, Nik & Atapour Abarghouei, Amir & Bonner, Stephen & Connolly, Jason & Al Moubayed, Noura & Breckon, Toby. (2019). Simulating Brain Signals: Creating Synthetic EEG Data via Neural-Based Generative Models for Improved SSVEP Classification. 
