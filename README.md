# Sleep Spindle and K-Complex Detection

## Dataset Description
The dataset used for this study is the **DREAMS** dataset, a publicly available resource consisting of excerpts from clinical polysomnography (PSG) recordings. These recordings are crucial for sleep research and include expert-annotated events of sleep spindles and K-complexes, which are essential markers of sleep quality and neural processing.

### Sleep Spindle Data
The dataset includes **eight** 30-minute excerpts from the central EEG channel, obtained from full-night PSG recordings conducted in a sleep laboratory in Belgium. The recordings were acquired using a **32-channel digital polygraph (Brainnet™ System, MEDATEC, Brussels, Belgium)** and included patients diagnosed with various sleep disorders such as **dysomnia, restless legs syndrome, insomnia, and apnea/hypopnea syndrome**.

For this study, **six excerpts** were considered for sleep spindle detection. Each EEG excerpt was independently annotated by two sleep experts, ensuring reliability. The dataset provides:
- EEG recordings sampled at **50 Hz, 100 Hz, and 200 Hz**
- Three EEG channels (**CZ-A1 or C3-A1, FP1-A1, O1-A1**)
- Two Electrooculography (EOG) channels (**P8-A1, P18-A1**)
- One submental electromyography (EMG) channel

The **sleep spindles** are short bursts of brain activity, typically occurring in the frequency range **11-16 Hz** with a duration of at least **0.5 seconds**. They are critical for memory consolidation and neurological health. Two independent experts annotated these events, marking spindle-rich epochs while avoiding noisy segments.

### K-Complex Data
The dataset also includes **ten** 30-minute excerpts for K-complex detection, recorded under similar conditions. These recordings were obtained from healthy subjects and annotated by two experts. The **K-complexes** are **high-amplitude, bi-phasic waveforms** that appear every **30-60 seconds** in NREM sleep. They play a crucial role in **sensory gating, memory processing, and sleep protection**. The annotation criteria included:
- Duration: **0.5 - 1.5 seconds**
- Amplitude: **At least twice the background EEG amplitude**
- Presence of a **sharp negative wave followed by a slower positive wave**

### Data Storage Format
The dataset is stored in the **European Data Format (EDF)**, which is a standard format for biomedical signals. The raw EEG signals were processed for feature extraction and model training.

## Methods
The proposed framework leverages deep learning techniques to classify sleep spindles and K-complexes. The models used include:

### Sleep Spindle Detection
- **Vision Transformer (ViT)**: Utilizes **Wigner-Ville spectrograms** to capture long-range dependencies in EEG signals. ViT processes spectrogram representations and applies self-attention mechanisms to distinguish spindles from non-spindles.
- **Temporal Convolutional Network (TCN)**: Captures temporal dependencies in EEG signals using dilated convolutions.
- **1D Convolutional Neural Network (1D-CNN)**: Extracts spatial hierarchies from the EEG time-series data.

### K-Complex Detection
- **1D-CNN**: Identifies local temporal patterns in EEG waveforms.
- **TCN**: Recognizes long-term dependencies in EEG data, improving classification accuracy.

### Explainable AI (XAI)
To enhance interpretability, **SHAP (SHapley Additive exPlanations)** was employed to analyze feature importance, ensuring model transparency for clinical applications.

## Results
The models achieved state-of-the-art performance on the DREAMS dataset:

### Sleep Spindle Classification (ViT)
- **Precision:** 0.9707
- **Recall:** 0.9707
- **F1-Score:** 0.9707
- **Accuracy:** 0.9708

### K-Complex Classification (1D-CNN)
- **Precision:** 0.9849
- **Recall:** 0.9977
- **F1-Score:** 0.9912
- **Accuracy:** 0.9913

The **ViT-based model** outperformed traditional CNN and RNN approaches for sleep spindle detection, while the **1D-CNN model** achieved exceptional performance in K-complex classification. The integration of **XAI techniques** further validated the reliability of model predictions, making this framework a promising tool for **automated sleep monitoring and neurological research**.

## Installation & Dependencies
To run the models, install the following dependencies:
```bash
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow torch torchvision shap
```

## Usage Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/sleep-spindle-kcomplex.git
   ```
2. Navigate to the project directory:
   ```bash
   cd sleep-spindle-kcomplex
   ```
3. Open and run the Jupyter Notebook files (`.ipynb`) to train and test the models.

## How to Contribute
Contributions are welcome! If you’d like to improve this project:
- Fork the repository.
- Create a feature branch.
- Submit a pull request with a detailed explanation of changes!


