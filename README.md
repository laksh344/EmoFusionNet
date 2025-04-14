# 🎯 EmoFusionNet

**EmoFusionNet** is a multimodal deep learning system that detects human emotional and mental states using synchronized data from:

- 🎥 **Facial Expressions** (Video – FER-2013)
- 🔊 **Speech Emotion** (Audio – RAVDESS)
- 🧠 **EEG Signals** (Brainwaves – Bonn Dataset)

By combining insights from the face, voice, and brain, EmoFusionNet achieves highly accurate sentiment and mental health classification – and even suggests AI-powered remedies to improve well-being.

---

## 🌟 Features

- ✅ **Tri-Modal Fusion**: Combines Video + Audio + EEG features using attention-based fusion
- 🧠 **EEG Analysis**: Extracts brainwave patterns using spectral band power
- 🗣️ **Speech Emotion Recognition**: Extracts MFCCs + spectrograms
- 😶 **Facial Emotion Recognition**: Pretrained ResNet50 on FER-2013
- 🤖 **AI-Based Remedy Generator**: Integrates a transformer LLM (e.g., Mistral) for mental health tips
- ⚡ Optimized with `mixed_precision` for fast training on Colab or GPU

---

## 📁 Dataset Summary

| Modality | Dataset          | Description                                 |
|----------|------------------|---------------------------------------------|
| EEG      | Bonn EEG         | Raw EEG data from healthy and epileptic patients |
| Audio    | RAVDESS          | Emotional speech dataset with labeled samples |
| Video    | FER-2013         | Facial expression images (7-class → 3-class) |

---

## 🔍 Emotion Classes

We reduce original emotion labels to **3 core classes**:

- 😊 **Happy**
- 😔 **Sad**
- 😐 **Neutral**

These are derived from original datasets via mapping logic.

---

## 🧠 Model Architecture

```text
[EEG Input] → [Power Band Extraction] → [Dense Layers]
[Audio Input] → [MFCC/Spectrogram] → [EfficientNetB0]
[Video Input] → [FER-2013 Image] → [ResNet50]

           → [Attention-Based Fusion Layer]
                    ↓
         [Dense → Dropout → BatchNorm]
                    ↓
             [Softmax Output]
```

---

## 📈 Performance

| Modality     | Accuracy   |
|--------------|------------|
| EEG Only     | ~85%       |
| Audio Only   | ~70%       |
| Video Only   | ~75%       |
| **Fused**    | **90%+**   |

---

## 🔧 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/laksh344/EmoFusionNet.git
cd EmoFusionNet
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Download Datasets

Download and place the datasets in the following structure:
```bash
/data/
    /FER2013/
    /RAVDESS/
    /BONN_EEG/
```

You can get them here:
- [FER-2013](https://www.kaggle.com/datasets/msambare/fer2013)
- [RAVDESS](https://zenodo.org/record/1188976)
- [Bonn EEG](https://epilepsy.uni-freiburg.de)

---

## ▶️ Running the Model

Launch the Jupyter notebook:

```bash
jupyter notebook newmmb3.ipynb
```

Or run using Google Colab for faster GPU training.

---

## 💬 AI-Powered Remedy Generation

Once an emotion is detected, the model optionally calls a transformer LLM (e.g., [Mistral](https://huggingface.co/mistralai/Mistral-7B-v0.1)) to generate:

- Breathing techniques
- Calming activities
- Music or meditation suggestions
- Cognitive wellness tips

> Requires HuggingFace Transformers.

---

## 📌 TODOs & Future Plans

- [ ] Add real-time webcam/audio/EEG inference
- [ ] Expand emotion classes to 5 or 7 categories
- [ ] Integrate lightweight LLM (e.g., DistilGPT2) for on-device remedy suggestion
- [ ] Build a web UI (Next.js or Streamlit)

---

## 🤝 Contributing

Contributions are welcome!  
If you find this project helpful, please ⭐ the repo and submit pull requests for enhancements or bug fixes.

---

---

## 🙏 Acknowledgements

- FER-2013 (Facial Expression Recognition)
- RAVDESS (Speech Emotion Dataset)
- Bonn EEG Dataset (University of Bonn)
- Hugging Face Transformers
- TensorFlow & Keras

---

## 📫 Contact

**Laksh** – [laksh344@github](https://github.com/laksh344)  
Drop a ⭐ if you like this project and follow for more AI-based healthcare tools!

