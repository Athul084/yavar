Base Model: BLIP (Bootstrapped Language-Image Pre-training)
Why BLIP?
Open-source, strong performance on image-text tasks
Supports conditional generation (text prompts + images)
Fine-tunable on custom datasets

Model Components:
Vision Encoder: ViT (Vision Transformer) for image embeddings
Text Decoder: Transformer-based language model
Multimodal Fusion: Cross-attention between image & text features

Data Preprocessing
Input Data Structure
Images: Tables, graphs, photos, diagrams (.jpg, .png)
Metadata (.txt files per image)
json
Preprocessing Steps
Image Processing:
Resize to 512×512 (ViT-compatible)
Convert to RGB
Normalize pixel values
Text Processing:
Context Concatenation: Combine metadata fields into a structured prompt
Truncation: Limit to 200 tokens (BLIP max length = 200)
Fine-Tuning Methodology
Dataset Preparation
Custom Dataset class to load (image + metadata + captions)
Train/Val Split: 80/20
Training Setup
Framework: Hugging Face Trainer
Hyperparameters:
Batch size: 8
Epochs: 3
Learning rate: 5e-5
Optimizer: AdamW
Loss: Cross-entropy
Evaluation Metrics:
BLEU (n-gram precision)
ROUGE-L (recall-focused)
BERTScore (semantic similarity)
Caption Generation Pipeline
Step-by-Step Process
Load Image + Metadata
Generate Captions:
Short Caption (max_len=20)
Detailed Caption (max_len=64)
Confidence Scoring:
Derived from token probabilities (exp(mean(logits)))
Low confidence (<0.5) → Highlighted in orange
Consistency Check:
Ensure captions align with metadata (e.g., don’t contradict section headers)
