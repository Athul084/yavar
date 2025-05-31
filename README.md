# 🖼️ BLIP-Based Image Captioning System

A **Vision-Language Model (VLM)** powered by **BLIP (Bootstrapped Language-Image Pretraining)** for generating concise and detailed captions from images and their associated metadata.

---

## 🚀 Why BLIP?

- ✅ **Open-source** and well-maintained  
- 🏆 **State-of-the-art performance** on image-text understanding tasks  
- 💬 **Conditional generation**: Uses both image and text prompts  
- 🔧 Easily **fine-tunable** on custom datasets  

---

## 🧠 Model Architecture

- **Vision Encoder**: ViT (Vision Transformer) – for image embeddings  
- **Text Decoder**: Transformer-based language model  
- **Multimodal Fusion**: Cross-attention between image & text features  

---

## 🗂️ Data Preprocessing

### 🔹 Input Data Format

- **Images**: `.jpg`, `.png` (can be tables, graphs, diagrams, etc.)  
- **Metadata**: Structured `.txt` or `.json` files per image  

### 🔧 Preprocessing Steps

#### 🖼 Image Processing

- Resize to **512×512** (ViT-compatible)  
- Convert to **RGB**  
- Normalize pixel values (using standard mean/std)  

#### 📝 Text Processing

- **Context Concatenation**: Combine metadata fields into structured prompts  
- **Truncation**: Limit to **200 tokens** (BLIP max input length)  

---

## 🏋️ Fine-Tuning Methodology

### 📁 Dataset Preparation

- Custom `Dataset` class to load:  
  - Image  
  - Metadata (context prompt)  
  - Target caption  
- Train/Validation Split: **80% / 20%**

### ⚙️ Training Configuration

- **Framework**: 🤗 Hugging Face `Trainer`  
- **Hyperparameters**:  
  - Batch Size: `8`  
  - Epochs: `3`  
  - Learning Rate: `5e-5`  
  - Optimizer: `AdamW`  
  - Loss: `Cross-Entropy`  

---

## 📊 Evaluation Metrics

| Metric       | Focus                                   |
|--------------|------------------------------------------|
| **BLEU**     | N-gram precision                         |
| **ROUGE-L**  | Longest common subsequence (recall)      |
| **BERTScore**| Semantic similarity                      |

---

## 🧾 Caption Generation Pipeline

### 🔄 Step-by-Step Inference

1. **Load** image and corresponding metadata  
2. **Generate Captions**:  
   - Short Caption → `max_length = 20`  
   - Detailed Caption → `max_length = 64`  
3. **Confidence Scoring**:  
   - Based on: `exp(mean(token logits))`  
   - Low confidence (< 0.5) → 🔶 *highlighted in orange*  
4. **Consistency Check**:  
   - Validate that captions do not contradict metadata (e.g., section headers, keywords)  

---

