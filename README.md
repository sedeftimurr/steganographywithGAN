# 🖼️ Deep Learning-Based Steganography with GANs

> A practical attempt at building a deep learning-based system for invisible copyright watermarking using SteganoGAN and VidaGAN principles.  
> This project explored multiple versions, highlighting both failure and incremental success.

---

## 🎯 Project Objective

The goal of this project was to build a **deep learning-powered steganography system** to hide copyright messages inside images. The core idea was inspired by:

- 🧠 [SteganoGAN (Zhang et al., 2019)](https://arxiv.org/abs/1901.03892)
- 🧠 VidaGAN (2021), particularly its use of **MSE targeting** and **error correction**

I aimed to create a robust system that:
- Embeds messages into cover images invisibly
- Resists visual detection
- Recovers messages reliably using **Reed–Solomon** coding

---

## 🧠 Architecture

The system follows a hybrid architecture based on both **SteganoGAN** and **VidaGAN** insights:

[Cover Image] + [Message] ──> 🧠 Encoder
↓
[Stego Image] ───→ Discriminator
↓
🧠 Decoder ──→ [Recovered Message]


- **MSE Targeting** was applied during training to keep distortion minimal.
- **Reed–Solomon** coding was added to correct bit-level decoding errors.
- Models were trained on the [Flickr30k](https://shannon.cs.illinois.edu/DenotationGraph/) dataset.

---

## 📂 Versions Overview

| Version | Description | Outcome |
|---------|-------------|---------|
| **v1** | Basic Encoder–Decoder architecture (no GAN, no RS) | ❌ Failed to recover message reliably |
| **v2** | GAN architecture + Reed–Solomon added | ❌ Still low accuracy; decoder too noisy |
| **v3** | Optimized encoder/decoder + improved loss tuning (MSE-targeted) | ⚠️ Partial success (improved visuals, better decoding) |

---

## ⚠️ Limitations

- **Training Environment**: All training was done on Google Colab due to hardware limitations. This limited batch sizes, training duration, and depth.
- **Reed–Solomon Failure**: In versions 1 & 2, decoding accuracy did not exceed 90%, so **RS decoding failed** due to insufficient message recovery.
- **Third Version** showed promising results, but **not production-grade** yet.

---

## 📁 Outputs Provided

This repository includes only **sample results** for each version:

results/
│
├── v1/
│ ├── original.png
│ ├── stego.png
│ └── decoded.png
│
├── v2/
│ ├── original.png
│ ├── stego.png
│ └── decoded.png
│
└── v3/
├── original.png
├── stego.png
└── decoded.png


You can clearly observe the visual similarity between `original` and `stego`, and compare the accuracy of `decoded`.

---

## 📌 Takeaways

- Even **failed models can teach a lot**: handling noise, visual loss, GAN stability, and more.
- **Reed–Solomon** is powerful but requires high-accuracy binary recovery.
- **Colab constraints** significantly limit experimentation on steganography tasks due to their GPU and memory demands.

---

## 🤝 License & Usage

This project is shared for **educational and research purposes only.**  
No code is included. Please contact me if you are interested in collaboration or full access.

📧 Email: sedeftimurrr@gmail.com  
🔗 LinkedIn: [linkedin.com/in/sedeftimur](https://www.linkedin.com/in/sedeftimur)
