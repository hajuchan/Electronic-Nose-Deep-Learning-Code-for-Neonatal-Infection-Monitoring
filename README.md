# Electronic Nose Deep Learning Code for Neonatal Infection Monitoring

This repository contains the deep learning implementation for the research paper:

**"Microbial Volatile Organic Compound Fingerprints for Non-Contact and Real-Time Infection Monitoring Using Electronic Nose in Infant Incubator"**

Published in: https://doi.org/10.1016/j.snb.2025.138376


## 🔬 Research Overview
This study develops a non-invasive electronic nose system for real-time infection monitoring in neonatal incubators by identifying pathogens through microbial volatile organic compounds (mVOCs). 

The system can distinguish between:

- Gram-positive bacteria: S. aureus, S. epidermidis
- Gram-negative bacteria: E. coli, K. pneumoniae
- Fungi: C. albicans, C. glabrata, C. parapsilosis

## 🏆 Key Results

97% accuracy in laboratory conditions using LSTM model
85.4% accuracy in real-size incubator (155L) testing
Superior performance over traditional diagnostic methods

## 🧠 Deep Learning Models
**Primary Models**

- LSTM (Long Short-Term Memory) - Best performance (97% accuracy)
- CNN (Convolutional Neural Network) - 92% accuracy
- LSTM-FCN (LSTM-Fully Convolutional Networks) - Multivariate time-series classification

**Baseline Models**

- SVM (Support Vector Machine)
- Decision Tree
- Naive Bayes
- Logistic Regression

## Transfer Learning

TL-ResNet50 - Pre-trained on ImageNet, fine-tuned for pathogen classification

## 📊 Dataset Specifications
**Sensor Array**

9 metal oxide sensors (TGS series, MQ series)
9 mVOC chemicals for pathogen identification
Time-series data with 2-second intervals over 60 seconds

## Target VOCs

Common to all pathogens: Ethanol, 3-methyl-1-butanol, Acetic acid
Bacterial markers: Formaldehyde, Indole, 2-undecanone
Fungal markers: 3-octanone, Isobutyl acetate, Cyclohexanone

## 🛠 Implementation Details
**Data Preprocessing**
```
# python Baseline correction and normalization
normalized_response = V / V0  # V0: baseline voltage, V: response voltage

# Train-test split
train_data = 80%
test_data = 20%

# Zero-padding for sequence length matching
sequence_length = 60_seconds / 2_second_intervals = 30_timesteps
```

**LSTM Architecture**
- **Input**: Multivariate time-series (9 sensors × 30 timesteps)
Memory cells for long-term dependencies
Output: 7-class classification (pathogen types)
Optimization: Grid-search for hyperparameters

**Performance Metrics**

- **Accuracy**: 97% (laboratory), 85.4% (real incubator)
- **AUC-ROC**: >0.95 for all pathogens
- **R² values**: >0.80 for pathogen quantification

## 🚀 Quick Start
**Installation**
```
git clone https://github.com/username/electronic-nose-neonatal-infection.git
cd electronic-nose-neonatal-infection
pip install -r requirements.txt
```

**Requirements**
```
tensorflow>=2.8.0
scikit-learn>=1.0.0
numpy>=1.21.0
pandas>=1.3.0
matplotlib>=3.5.0
seaborn>=0.11.0
```

## 📈 Model Performance
| Model | Precision | Recall | F1-Score | Accuracy |
|-------|-----------|--------|----------|----------|
| **LSTM** | **0.97** | **0.97** | **0.98** | **0.97** |
| CNN | 0.92 | 0.92 | 0.92 | 0.92 |
| Naive Bayes | 0.74 | 0.74 | 0.76 | 0.75 |
| Logistic Regression | 0.68 | 0.68 | 0.71 | 0.68 |
| SVM | 0.55 | 0.55 | 0.69 | 0.59 |

## 🔬 Clinical Applications
**Smart Incubator Integration**
- Real-time monitoring of infection status
- Evidence-based antibiotic prescriptions
- Non-contact pathogen detection
- Reduction of antibiotic misuse

**Target Pathogens**
- Late-onset sepsis prevention in NICU
- Nosocomial infection early detection
- Antimicrobial resistance mitigation

## 📚 Citation
```bibtex
@article{LEE2025138376,
title = {Microbial Volatile Organic Compound Fingerprints for Non-Contact and Real-Time Infection Monitoring Using Electronic Nose in Infant Incubator},
journal = {Sensors and Actuators B: Chemical},
pages = {138376},
year = {2025},
issn = {0925-4005},
doi = {https://doi.org/10.1016/j.snb.2025.138376},
url = {https://www.sciencedirect.com/science/article/pii/S0925400525011529},
author = {Solpa Lee and Bum Ju Ahn and Juchan Ha and Anmo J Kim and Hyun‑Kyung Park and Yongwoo Jang}
}
```

## 🤝 Contributing
We welcome contributions to improve the electronic nose system for neonatal infection monitoring. Please see our Contributing Guidelines for details.

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
