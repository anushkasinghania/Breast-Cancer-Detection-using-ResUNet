# Breast Tumour Detection using Deep Convolutional Neural Networks


[![Published](https://img.shields.io/badge/IJERCSE-Published-blue)](https://ijercse.com/viewabstract.php?id=16195&volume=Volume10&issue=Issue1)
[![ISSN](https://img.shields.io/badge/ISSN-2394--2320-green)](https://ijercse.com/viewabstract.php?id=16195&volume=Volume10&issue=Issue1)

Automated breast tumour detection and segmentation using a **Residual U-Net (ResU-Net)** — combining residual skip connections with the U-Net encoder–decoder architecture for robust pixel-level tumour localisation on breast ultrasound images.

> 📄 **Published in IJERCSE, Vol. 10, Issue 1 (Jan 2023).** See [Publication](#publication).

---

## Overview

Breast cancer is one of the most fatal cancers for women, and its high mortality rate makes precise, early detection critical. This project implements the model behind our published paper, *"Breast Tumour Detection using Deep Convolutional Neural Networks,"* which proposes **semantic image segmentation of breast tumours using a ResU-Net model**. Residual connections in the encoder improve gradient flow and feature learning compared to a standard U-Net, producing binary masks that highlight tumour regions in ultrasound scans.

---

## Model Architecture - ResU-Net

ResU-Net extends U-Net by replacing plain convolution blocks with **residual blocks**, enabling deeper training without performance degradation.

- **Encoder:** 5-level residual downsampling path (feature maps double at each level)
- **Bridge:** bottleneck residual block at the deepest level
- **Decoder:** upsampling path with skip connections from the corresponding encoder levels
- **Output:** 1×1 convolution + sigmoid activation → binary tumour mask

---

## Dataset

- **Source:** Breast ultrasound images (loaded from Google Drive)
- **Resolution:** 304 × 304 pixels
- **Size:** 64 labelled images with corresponding ground-truth masks
- **Normalisation:** pixel values scaled to [0, 1]
- **Split:** 90% training / 10% validation

---

## Training

| Setting | Value |
|---------|-------|
| Optimizer | Adam |
| Loss | Binary cross-entropy |
| Metrics | Accuracy, AUC, Sensitivity @ 0.5, Specificity @ 0.5 |
| Batch size | 6 |
| Epochs | 5 (+ early stopping) |
| Callbacks | EarlyStopping, ReduceLROnPlateau, ModelCheckpoint, CSVLogger, TensorBoard |
| Threshold | 0.5 (for binary mask) |

---

## Results

The proposed ResU-Net model attained a high **training accuracy of 0.9871**.

Sample prediction outputs are in the [`Results/`](./Results/) folder.

| File | Description |
|------|-------------|
| `Learning Curve.png` | Training vs validation loss/accuracy over epochs |
| `Grount Truth.png` | Ground-truth segmentation masks |
| `Pred1.png` – `pred10.png` | Model predictions on sample images |

---

## Repository Structure

.
├── Documents/
│   ├── AnushkaSinghania_Major_Project_Report.pdf
│   └── Published_Paper.pdf
├── Results/
│   ├── Learning_Curve.png
│   ├── Ground_Truth.png
│   ├── Pred1.png ... Pred10.png
├── breast_cancer_detection_resunet.py    # Model architecture, training, and inference
└── README.md                             # Project documentation



---

## Publication

**Breast Tumour Detection using Deep Convolutional Neural Networks**
*Himashri Mehra, Anushka Singhania, Anu Narera, Neha Singh*
International Journal of Engineering Research in Computer Science and Engineering (**IJERCSE**), Vol. 10, Issue 1 — ISSN: 2394-2320 (Online)
Published: 30 January 2023

🔗 **[Read the paper on IJERCSE](https://ijercse.com/viewabstract.php?id=16195&volume=Volume10&issue=Issue1)**

A local copy is included at [`Documents/Breast Tumour Detection using Deep Convolutional Published paper.pdf`](./Documents/Breast%20Tumour%20Detection%20using%20Deep%20Convolutional%20Published%20paper.pdf).

### Abstract

> Breast cancer is one of the most fatal cancers for women. Because of its high mortality rate, it is becoming a necessity for the researchers to come up with models for precise detection of disease and subsequent treatments. By doing this, the researchers will not only promote the new technology but also contribute to the mankind. We are also trying to do the same. This paper proposes the semantic image segmentation of breast tumour using ResUNet model. The proposed model attained a high accuracy of 0.9871 on our training dataset. The complete empirical analysis along with the exhaustive literature review is presented in the paper.

---

## Citation

```bibtex
@article{mehra2023breast,
  title   = {Breast Tumour Detection using Deep Convolutional Neural Networks},
  author  = {Mehra, Himashri and Singhania, Anushka and Narera, Anu and Singh, Neha},
  journal = {International Journal of Engineering Research in Computer Science and Engineering (IJERCSE)},
  volume  = {10},
  number  = {1},
  year    = {2023},
  issn    = {2394-2320},
  url     = {https://ijercse.com/viewabstract.php?id=16195&volume=Volume10&issue=Issue1}
}
```

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat&logo=keras&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logo=python&logoColor=white)
![scikit-image](https://img.shields.io/badge/scikit--image-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=flat&logo=googlecolab&logoColor=white)

---

## Authors

| Name | Role |
|------|------|
| Himashri Mehra | Co-author |
|[Anushka Singhania | Co-author |
| Anu Narera | Co-author |
| Neha Singh | Co-author |

