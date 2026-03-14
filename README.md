# ComfyUI Text-to-Image Workflow (Flux Dev Model)

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![ComfyUI](https://img.shields.io/badge/ComfyUI-Workflow-green)
![Model](https://img.shields.io/badge/Model-Flux%20Dev-purple)
![License](https://img.shields.io/badge/License-MIT-yellow)

This repository demonstrates a **Text-to-Image generation workflow built in ComfyUI using the Flux Dev model**.  
The workflow converts **natural language prompts into high-quality generated images** using a structured **node-based pipeline**.

The pipeline uses:

- Flux Dev checkpoint
- CLIP text encoding
- Latent image generation
- Diffusion sampling using **KSampler**

This workflow is designed for **AI image generation, prompt experimentation, and workflow automation**.

---

# Workflow Architecture

The workflow consists of several interconnected nodes responsible for different stages of the image generation process.

Load Checkpoint
│
▼
CLIP Text Encode (Positive Prompt)
│
▼
Flux Guidance
│
▼
Empty Latent Image
│
▼
KSampler
│
▼
VAE Decode
│
▼
Save Image


---

# Features

- High-quality **Flux Dev image generation**
- Modular **node-based pipeline**
- Easy to modify prompts and parameters
- Supports **1024×1024 high-resolution images**
- Designed for **automation and experimentation**

---

# Workflow Nodes Explanation

## 1. Load Checkpoint

Loads the **Flux Dev diffusion model**.

**Model used**

flux1-dev-fp8.safetensors


**Purpose**

- Provides the base model for image generation
- Supplies CLIP, VAE, and diffusion weights

Outputs:

- Model
- CLIP
- VAE

---

## 2. CLIP Text Encode (Positive Prompt)

Encodes the text prompt into embeddings using the CLIP model.

**Example Prompt**

photorealistic Pakistani man wearing traditional shalwar kameez,
modern hairstyle, soft lighting, cinematic background,
8k ultra realistic photography


**Purpose**

- Converts text prompts into numerical embeddings
- Guides the diffusion model to generate relevant images

---

## 3. Flux Guidance

Controls prompt influence strength.

guidance: 3.5


**Purpose**

- Improves prompt adherence
- Controls how strongly the model follows the text prompt

---

## 4. Empty Latent Image

Creates a blank latent space where the image will be generated.

width: 1024
height: 1024
batch size: 1


**Purpose**

- Defines image resolution
- Initializes the diffusion process

---

## 5. KSampler (Diffusion Sampling)

Core generation step where noise is converted into an image.

steps: 20
CFG: 1.0
sampler: Euler
scheduler: Simple
denoise: 1.0


**Purpose**

- Iteratively denoises latent noise
- Generates the final image structure

---

## 6. VAE Decode

Converts the latent representation into a visible RGB image.

**Purpose**

- Transforms the latent output into a final displayable image

---

## 7. Save Image

Stores the generated image to disk.

**Purpose**

- Saves generated outputs for later use

---

# Example Outputs

The workflow can generate:

- Photorealistic portraits
- Artistic scenes
- Concept art
- Character designs

You can add generated examples inside the **outputs/** folder and display them here.

---

# Project Structure

flux-dev-comfyui-workflow
│
├── workflow
│ └── flux_workflow.json
│
├── outputs
│ └── generated_images
│
├── assets
│ └── workflow_diagram.png
│
├── README.md
└── LICENSE


---

# Requirements

## Software

- ComfyUI
- Python 3.10+

## Model

Flux Dev Model

flux1-dev-fp8.safetensors


## Recommended Hardware

- GPU with **8GB+ VRAM**

---

# How to Use

## 1. Install ComfyUI

```bash
git clone https://github.com/comfyanonymous/ComfyUI
2. Download Flux Dev Model
Place the model inside:

ComfyUI/models/checkpoints/
3. Load the Workflow
Open ComfyUI and load the workflow JSON file:

flux_workflow.json
4. Generate Images
Modify the text prompt

Click Queue Prompt

The generated image will appear in the output folder

Author
Muhammad Sameer Khan
AI Workflow Engineer

GitHub:
https://github.com/muhammadsameerkhan-edit20

