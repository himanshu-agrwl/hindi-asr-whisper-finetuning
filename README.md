# hindi-asr-whisper-finetuning
📖 Overview

This project implements an end-to-end Automatic Speech Recognition (ASR) pipeline using the OpenAI Whisper-small model. The system is fine-tuned on Hindi conversational speech data and evaluated using Word Error Rate (WER).

In addition to model training, the project focuses heavily on error analysis, identifying common failure modes such as repetition collapse and language drift, and explores improvements through post-processing and lattice-based evaluation.

🚀 Key Features
Fine-tuning of Whisper-small on Hindi speech data
Audio preprocessing (resampling to 16kHz)
Segment-level dataset creation
Evaluation using Word Error Rate (WER)
Detailed qualitative error analysis
Error taxonomy (repetition, substitution, language drift, truncation)
Post-processing pipeline for output cleanup
Lattice-based evaluation for flexible scoring
🛠️ Tech Stack
Python
HuggingFace Transformers & Datasets
Librosa & Soundfile (audio processing)
JiWER (WER evaluation)
Google Colab
⚙️ Pipeline Overview
Data Preprocessing
Fix dataset URLs
Load audio from cloud storage
Extract transcription segments
Audio Processing
Convert audio to waveform
Resample to 16kHz (required by Whisper)
Feature Extraction
Convert audio → log-Mel spectrogram
Model Training
Fine-tune Whisper-small using HuggingFace Trainer
Evaluation
Compare baseline vs fine-tuned model using WER
Error Analysis
Identify patterns like repetition and substitution errors
Post-processing
Remove repeated tokens
Normalize numbers and detect English words
Advanced Evaluation
Apply lattice-based scoring to handle valid variations
📊 Results
Model	WER
Whisper-small (Baseline)	0.38
Fine-tuned Whisper-small	0.32
🔍 Observations
Fine-tuning led to modest improvement
Performance limited due to small and noisy dataset
Conversational Hindi and code-mixing are challenging
⚠️ Error Analysis

The following major error types were observed:

1. Repetition Collapse
Example: “जी जी जी जी…”
Cause: Decoder instability
2. Substitution Errors
Incorrect or unrelated words generated
3. Language Drift
Model outputs non-Hindi text
4. Truncated Output
Very short or incomplete predictions
🧠 Key Insights
Data quality impacts performance more than model size
Fine-tuning alone is not sufficient for noisy datasets
Post-processing has limited effect on severely degraded outputs
Lattice-based evaluation provides more realistic scoring
🔧 Improvements Explored
✔ Repetition Removal
Removes consecutive repeated words
Limited improvement observed
✔ Text Normalization Pipeline
Hindi number normalization
English word tagging
✔ Lattice-Based Evaluation
Handles variations like:
“14” vs “चौदह”
Reduced WER significantly in controlled examples
📁 Project Structure
├── notebook.ipynb
├── README.md
├── requirements.txt
├── outputs/
└── data_sample/
▶️ How to Run
pip install transformers datasets librosa soundfile jiwer accelerate
Run the notebook in Google Colab or locally
Ensure audio URLs are accessible
🔮 Future Improvements
Train on larger and cleaner Hindi datasets
Use beam search decoding instead of greedy decoding
Apply language constraints during inference
Improve audio-text alignment
Deploy as a real-time ASR application
📌 Conclusion

This project demonstrates a complete ASR workflow, from data preprocessing to model evaluation and error analysis. While fine-tuning improves performance, the results highlight the importance of data quality, decoding strategies, and robust evaluation methods in real-world speech recognition systems.
