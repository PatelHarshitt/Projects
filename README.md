CPF-SK System Comparison using Deep Learning

A Hybrid Communication-ML Pipeline for Robust Demodulation

📌 Overview

This project compares traditional CPF-SK (Continuous Phase Frequency Shift Keying) demodulation with deep-learning–based demodulators under realistic channel impairments.
The goal is to evaluate whether neural networks can outperform classical signal processing methods, particularly in noisy and multipath environments.

The project includes:

📡 Signal simulation with multipath fading

🧠 CNN-based Softmax Demodulator

🔢 CNN-based Sigmoid/Binary Demodulator

📉 BER evaluation across SNR levels

📊 Performance comparison with classical CPF-SK demodulation

🚀 Features
✔ Complete end-to-end simulation

Symbol generation

Pulse shaping

Multipath channel

Noise addition

Oversampling (SPS = 16)

✔ Two Deep Learning Models

Softmax model (multiclass symbol prediction)

Sigmoid model (binary bit-level prediction)

✔ Classical System A (Baseline)

No ML

Standard CPF-SK demodulation pipeline

✔ BER Curve Analysis

Model vs. baseline

Robustness at various SNR levels

Impact of channel taps

🧠 Model Architectures
1. Softmax CNN Demodulator

Conv1D → MaxPooling → Upsampling

TimeDistributed Dense

Output: probability distribution over symbols

2. Sigmoid CNN Binary Demodulator

Similar architecture

Output: bit-wise sigmoid for binary decisions

Both models learn channel behavior, pulse shaping, and symbol transitions purely from data.

🔧 Simulation Parameters
Parameter	Value
Samples per symbol (SPS)	16
Roll-off factor (H)	0.5
Window size	128 samples
Channel taps	[0.9, 0, 0.6+0.1j, 0.3-0.2j, 0]
Training windows	Generated from simulated received signal
📂 Project Structure
│── cpfsk-system-comparison.ipynb       # Main notebook
│── README.md                           # Documentation
│── results/                            # BER plots, saved metrics
│── models/                             # Trained ML models (optional)
└── presentation/                       # PPT generated from this project

📊 Results Summary

ML-based demodulators significantly outperform the classical system under low and mid-SNR.

The Softmax CNN offers smoother and more stable predictions.

Sigmoid binary decoder works well at higher SNR but struggles in deep fades.

Classical CPF-SK fails to track channel variations compared to learned models.

🗂 How to Run

Install dependencies:

pip install tensorflow numpy matplotlib


Open the notebook:

jupyter notebook cpfsk-system-comparison.ipynb


Run each cell step-by-step to:

Generate signals

Create labels

Train the neural demodulators

Evaluate BER

🔮 Future Improvements

Use real RF recordings instead of only simulated data

Add RNN/Transformer layers for temporal context

Train on fading profiles varying with time

Deploy model on an SDR (GNU Radio + USRP)

📝 Conclusion

This project demonstrates that Deep Learning significantly improves demodulation accuracy in CPF-SK communication systems affected by noise and multipath.
Through CNN-based symbol prediction, the system achieves lower BER, better generalization, and better resilience to channel distortions than classical demodulators.
