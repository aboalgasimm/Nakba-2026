# Arabic Handwritten Manuscript OCR

This repository contains our deep learning-based Optical Character Recognition (OCR) system for Arabic handwritten manuscript recognition. The model is designed to handle the complexity of cursive Arabic script, including character connectivity, dot ambiguity, and irregular word spacing.

---

## Architecture

Our system follows an end-to-end **CNN–BiLSTM–CTC** framework:

- **CNN (Convolutional Neural Network)**  
  Extracts spatial visual features from input manuscript line images.

- **BiLSTM (Bidirectional Long Short-Term Memory)**  
  Models sequential dependencies in both forward and backward directions, capturing contextual relationships between characters.

- **CTC (Connectionist Temporal Classification)**  
  Enables alignment-free training without explicit character-level segmentation.

This architecture allows the model to jointly learn visual representations and sequence modeling directly from raw image inputs.

![architecture](https://github.com/user-attachments/assets/dbd67322-f87e-4e13-9cbc-6bae3c09fb36)


---

## Training Setup

- Trained using the official **AR-MS** training dataset.
- Input images are resized and normalized before being passed to the network.
- Training is performed end-to-end using **CTC loss**.
- Learning rate scheduling and early stopping are applied for optimization stability.

---

## Decoding & Post-Processing

To improve recognition performance, we applied Arabic-specific decoding and post-processing techniques:

- Greedy decoding with CTC
- Dot-level ambiguity correction
- Word segmentation refinement (handling merged/split words)
- Vocabulary-aware filtering

These strategies help reduce **Character Error Rate (CER)** and **Word Error Rate (WER)**, especially in cases of dot confusion and cursive word merging.

---

## Output

The system takes a **line image** as input and produces a fully reconstructed **Arabic text line** as output.
