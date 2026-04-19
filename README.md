# 🗣️ Hindi ASR Fine-Tuning using Whisper

## 📌 Project Overview
This project implements an end-to-end **Automatic Speech Recognition (ASR)** system using the Whisper-small model. The model is fine-tuned on Hindi conversational speech data and evaluated using Word Error Rate (WER).

The project goes beyond basic training by performing **detailed error analysis**, identifying key failure patterns, and exploring improvements using post-processing techniques and lattice-based evaluation.

---

## 🎯 Objectives
- Fine-tune Whisper-small for Hindi speech recognition  
- Evaluate model performance using WER  
- Identify and categorize ASR errors  
- Improve predictions using post-processing  
- Explore alternative evaluation methods (lattice-based scoring)  

---

## ⚙️ Pipeline Overview

### 1. Data Preparation
- Fixed dataset URLs for accessibility  
- Loaded audio and transcription data  
- Extracted segment-level speech-text pairs  

### 2. Audio Processing
- Converted audio into waveform  
- Resampled audio to 16kHz (model requirement)  

### 3. Feature Extraction
- Converted audio into **log-Mel spectrograms**  

### 4. Model Training
- Fine-tuned Whisper-small using HuggingFace Trainer  
- Used tokenized text and extracted audio features  

### 5. Evaluation
- Compared baseline vs fine-tuned model  
- Used Word Error Rate (WER) as the primary metric  

### 6. Error Analysis
Identified major failure patterns:
- Repetition collapse  
- Substitution errors  
- Language drift  
- Truncated outputs  

### 7. Post-processing
- Repetition removal  
- Number normalization  
- English word tagging  

### 8. Advanced Evaluation
- Implemented lattice-based evaluation  
- Allowed flexible matching (e.g., "14" vs "चौदह")  

---

## 🛠️ Tech Stack
- Python  
- HuggingFace Transformers & Datasets  
- Librosa & Soundfile  
- JiWER  
- Google Colab  

---

## 📊 Results

| Model | WER |
|------|-----|
| Baseline Whisper-small | 0.38 |
| Fine-tuned Model | 0.32 |

---

## 🔍 Key Insights
- Fine-tuning improves performance but is limited by dataset size  
- Conversational Hindi and code-mixed speech are challenging  
- Repetition collapse is a major failure mode  
- Post-processing alone is not sufficient  
- Lattice-based evaluation provides more realistic scoring  

---

## ⚠️ Challenges
- Small and noisy dataset  
- Code-mixed Hindi speech  
- Limited GPU resources  
- Model instability during decoding  

---

## 🚀 Future Improvements
- Train on larger and cleaner datasets  
- Use beam search decoding  
- Apply language constraints during inference  
- Improve preprocessing and alignment  
- Deploy as a real-time ASR system  

---

## 📁 Project Structure

├── ASR_whisper_finetuning.ipynb
├── README.md
└── requirements.txt


---

## ▶️ How to Run

```bash
pip install transformers datasets librosa soundfile jiwer accelerate


```

## 🌍 Why This Project Matters

Speech recognition for Hindi and code-mixed languages is still challenging due to limited datasets and informal speech patterns. This project explores real-world limitations of ASR systems and highlights key challenges in low-resource language settings.

---

## 📌 Conclusion

This project demonstrates a complete ASR pipeline, including training, evaluation, and error analysis. It highlights the importance of data quality, preprocessing, and evaluation strategies in building robust speech recognition systems.
