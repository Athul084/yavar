# Image Captioning from Contextual Metadata using BLIP

A fine-tuned Vision-Language Model (VLM) that generates context-aware captions for images using visual content and surrounding metadata.

![Example Output](docs/sample_output.jpg) *(example annotated image with captions)*

## Features

- 🖼️ **Multimodal Understanding**: Combines image features with textual metadata
- 📝 **Dual Captioning**: Generates both concise and detailed descriptions
- 🔍 **Context-Aware**: Leverages section headers, captions, footnotes, etc.
- 📊 **Confidence Scoring**: Quantifies prediction certainty for each caption
- 🛠️ **Fine-Tuning**: Adapts BLIP to domain-specific data

## Model Architecture

### Base Model: BLIP (Bootstrapped Language-Image Pre-training)
**Why BLIP?**
- ✅ Open-source (Apache 2.0 license)
- ✅ State-of-the-art on image-text tasks
- ✅ Supports conditional generation
- ✅ Fine-tunable on custom datasets

**Components**:
| Component | Description |
|-----------|-------------|
| Vision Encoder | ViT (Vision Transformer) for image embeddings |
| Text Decoder | Transformer-based language model |
| Multimodal Fusion | Cross-attention between image & text features |

## Data Processing

### Input Structure
