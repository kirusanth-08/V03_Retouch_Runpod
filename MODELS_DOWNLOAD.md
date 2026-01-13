# V03 Retouch API - Model Download Links

This document lists all the models and custom nodes required for the v03_retouch_api workflow.

## Core Models

### 1. Flux Fill Dev Model (UNET)
- **File**: `flux1-fill-dev.safetensors`
- **Download**: https://huggingface.co/black-forest-labs/FLUX.1-Fill-dev
- **Location**: `ComfyUI/models/unet/`
- **Size**: ~23 GB
- **Description**: Flux inpainting model for high-quality image retouching

### 2. Flux VAE
- **File**: `fulx_fill_vae.safetensors`
- **Download**: https://huggingface.co/black-forest-labs/FLUX.1-Fill-dev/tree/main
- **Location**: `ComfyUI/models/vae/`
- **Size**: ~335 MB
- **Description**: VAE for Flux Fill model

### 3. CLIP Text Encoders
#### T5XXL (FP16)
- **File**: `t5xxl_fp16.safetensors`
- **Download**: https://huggingface.co/comfyanonymous/flux_text_encoders/tree/main
- **Location**: `ComfyUI/models/clip/`
- **Size**: ~9.7 GB

#### CLIP-L
- **File**: `clip_l.safetensors`
- **Download**: https://huggingface.co/comfyanonymous/flux_text_encoders/tree/main
- **Location**: `ComfyUI/models/clip/`
- **Size**: ~246 MB

## Segmentation Models

### 4. SAM (Segment Anything Model)
- **File**: `sam_vit_h (2.56GB)`
- **Download**: https://huggingface.co/spaces/abhishek/StableSAM/resolve/main/sam_vit_h_4b8939.pth
- **Alternative**: https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth
- **Location**: `ComfyUI/models/sams/`
- **Size**: ~2.56 GB
- **Description**: Vision Transformer for segmentation

### 5. Grounding DINO
- **File**: `GroundingDINO_SwinB (938MB)`
- **Download**: https://huggingface.co/ShilongLiu/GroundingDINO/resolve/main/groundingdino_swinb_cogcoor.pth
- **Location**: `ComfyUI/models/grounding-dino/`
- **Size**: ~938 MB
- **Description**: Object detection model for text-based segmentation

### 6. Face Parsing Model
- **Auto-downloaded by**: FaceParsingModelLoader node
- **Download**: Automatically downloaded on first use
- **Location**: `ComfyUI/models/face_parsing/` (or custom nodes directory)
- **Description**: BiSeNet-based face parsing model for facial feature segmentation

## Required Custom Nodes

### 7. ComfyUI-segment-anything-2
- **Repository**: https://github.com/neverbiasu/ComfyUI-SAM2
- **Alternative**: https://github.com/storyicon/comfyui_segment_anything
- **Install**: 
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/storyicon/comfyui_segment_anything
  pip install -r comfyui_segment_anything/requirements.txt
  ```
- **Provides**: SAMModelLoader, GroundingDinoModelLoader, GroundingDinoSAMSegment

### 8. ComfyUI-layerdiffuse (LayerMask)
- **Repository**: https://github.com/chflame163/ComfyUI_LayerStyle
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/chflame163/ComfyUI_LayerStyle
  pip install -r ComfyUI_LayerStyle/requirements.txt
  ```
- **Provides**: LayerMask: MaskGrow, LayerMask: PersonMaskUltra V2

### 9. ComfyUI-faceParsing
- **Repository**: https://github.com/Ryuukeisyou/comfyui_face_parsing
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/Ryuukeisyou/comfyui_face_parsing
  pip install -r comfyui_face_parsing/requirements.txt
  ```
- **Provides**: FaceParse, FaceParsingModelLoader, FaceParsingProcessorLoader, FaceParsingResultsParser

### 10. ComfyUI-A-Person-Mask-Generator
- **Repository**: https://github.com/Yves-X/ComfyUI-A-Person-Mask-Generator
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/Yves-X/ComfyUI-A-Person-Mask-Generator
  pip install -r ComfyUI-A-Person-Mask-Generator/requirements.txt
  ```
- **Provides**: APersonFaceLandmarkMaskGenerator

### 11. ComfyUI-Custom-Scripts (pysssss)
- **Repository**: https://github.com/pythongosssss/ComfyUI-Custom-Scripts
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/pythongosssss/ComfyUI-Custom-Scripts
  ```
- **Provides**: StringFunction|pysssss

### 12. rgthree-comfy
- **Repository**: https://github.com/rgthree/rgthree-comfy
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/rgthree/rgthree-comfy
  pip install -r rgthree-comfy/requirements.txt
  ```
- **Provides**: Any Switch (rgthree)

### 13. ComfyUI_essentials
- **Repository**: https://github.com/cubiq/ComfyUI_essentials
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/cubiq/ComfyUI_essentials
  ```
- **Provides**: GetImageSize+, MaskPreview+

### 14. ComfyUI-Inpaint-CropAndStitch
- **Repository**: https://github.com/lquesada/ComfyUI-Inpaint-CropAndStitch
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/lquesada/ComfyUI-Inpaint-CropAndStitch
  ```
- **Provides**: InpaintCrop, InpaintStitch, InpaintModelConditioning

### 15. comfyui_bmab (GrowMaskWithBlur)
- **Repository**: https://github.com/portu-sim/comfyui_bmab
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/portu-sim/comfyui_bmab
  pip install -r comfyui_bmab/requirements.txt
  ```
- **Provides**: GrowMaskWithBlur

### 16. comfyui-tooling-nodes
- **Repository**: https://github.com/Acly/comfyui-tooling-nodes
- **Install**:
  ```bash
  cd ComfyUI/custom_nodes
  git clone https://github.com/Acly/comfyui-tooling-nodes
  ```
- **Provides**: Cut By Mask

## Installation Order

1. Install all custom nodes first
2. Download core models (Flux, CLIP, VAE)
3. Download segmentation models (SAM, Grounding DINO)
4. Run ComfyUI once to trigger automatic downloads for face parsing
5. Verify all models are in correct directories

## Model Download Commands (wget)

### Download Core Models

```bash
# Create model directories
mkdir -p ComfyUI/models/unet
mkdir -p ComfyUI/models/vae
mkdir -p ComfyUI/models/clip
mkdir -p ComfyUI/models/sams
mkdir -p ComfyUI/models/grounding-dino

# Download Flux Fill Dev UNET (requires HuggingFace authentication)
# Note: This model requires accepting license terms on HuggingFace
# Option 1: Use huggingface-cli
huggingface-cli download black-forest-labs/FLUX.1-Fill-dev flux1-fill-dev.safetensors --local-dir ComfyUI/models/unet

# Option 2: Direct download with authentication token
# wget --header="Authorization: Bearer YOUR_HF_TOKEN" \
#   https://huggingface.co/black-forest-labs/FLUX.1-Fill-dev/resolve/main/flux1-fill-dev.safetensors \
#   -O ComfyUI/models/unet/flux1-fill-dev.safetensors

# Download Flux VAE
wget https://huggingface.co/black-forest-labs/FLUX.1-Fill-dev/resolve/main/ae.safetensors \
  -O ComfyUI/models/vae/fulx_fill_vae.safetensors

# Download CLIP Text Encoders
wget https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors \
  -O ComfyUI/models/clip/t5xxl_fp16.safetensors

wget https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors \
  -O ComfyUI/models/clip/clip_l.safetensors

# Download SAM model
wget https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth \
  -O ComfyUI/models/sams/sam_vit_h_4b8939.pth

# Download Grounding DINO
wget https://huggingface.co/ShilongLiu/GroundingDINO/resolve/main/groundingdino_swinb_cogcoor.pth \
  -O ComfyUI/models/grounding-dino/groundingdino_swinb_cogcoor.pth
```

### Alternative: Download with Progress Bar

```bash
# Using wget with progress bar and resume capability
# CLIP encoders
wget -c --progress=bar:force:noscroll \
  https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors \
  -O ComfyUI/models/clip/t5xxl_fp16.safetensors

wget -c --progress=bar:force:noscroll \
  https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors \
  -O ComfyUI/models/clip/clip_l.safetensors

# Segmentation models
wget -c --progress=bar:force:noscroll \
  https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth \
  -O ComfyUI/models/sams/sam_vit_h_4b8939.pth

wget -c --progress=bar:force:noscroll \
  https://huggingface.co/ShilongLiu/GroundingDINO/resolve/main/groundingdino_swinb_cogcoor.pth \
  -O ComfyUI/models/grounding-dino/groundingdino_swinb_cogcoor.pth
```

## Quick Install Script

```bash
#!/bin/bash
# Complete installation script for v03_retouch_api workflow

set -e  # Exit on error

echo "=== Installing V03 Retouch API Workflow ==="

# Navigate to ComfyUI directory
cd ComfyUI

# Create model directories
echo "Creating model directories..."
mkdir -p models/unet models/vae models/clip models/sams models/grounding-dino

# Download models
echo "Downloading CLIP text encoders..."
wget -c https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors \
  -O models/clip/t5xxl_fp16.safetensors

wget -c https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors \
  -O models/clip/clip_l.safetensors

echo "Downloading Flux VAE..."
wget -c https://huggingface.co/black-forest-labs/FLUX.1-Fill-dev/resolve/main/ae.safetensors \
  -O models/vae/fulx_fill_vae.safetensors

echo "Downloading SAM model..."
wget -c https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth \
  -O models/sams/sam_vit_h_4b8939.pth

echo "Downloading Grounding DINO..."
wget -c https://huggingface.co/ShilongLiu/GroundingDINO/resolve/main/groundingdino_swinb_cogcoor.pth \
  -O models/grounding-dino/groundingdino_swinb_cogcoor.pth

# Install custom nodes
echo "Installing custom nodes..."
cd custom_nodes

git clone https://github.com/storyicon/comfyui_segment_anything
git clone https://github.com/chflame163/ComfyUI_LayerStyle
git clone https://github.com/Ryuukeisyou/comfyui_face_parsing
git clone https://github.com/Yves-X/ComfyUI-A-Person-Mask-Generator
git clone https://github.com/pythongosssss/ComfyUI-Custom-Scripts
git clone https://github.com/rgthree/rgthree-comfy
git clone https://github.com/cubiq/ComfyUI_essentials
git clone https://github.com/lquesada/ComfyUI-Inpaint-CropAndStitch
git clone https://github.com/portu-sim/comfyui_bmab
git clone https://github.com/Acly/comfyui-tooling-nodes

# Install dependencies
echo "Installing Python dependencies..."
for dir in */; do
  if [ -f "$dir/requirements.txt" ]; then
    echo "Installing requirements for $dir"
    pip install -r "$dir/requirements.txt"
  fi
done

cd ..

echo "=== Installation Complete ==="
echo ""
echo "NOTE: Flux Fill Dev model requires manual download with HuggingFace authentication:"
echo "  huggingface-cli download black-forest-labs/FLUX.1-Fill-dev flux1-fill-dev.safetensors --local-dir models/unet"
echo ""
echo "After downloading, place flux1-fill-dev.safetensors in ComfyUI/models/unet/"
```

## Docker Considerations

When building a Docker image, ensure:
1. All custom nodes are cloned during build
2. Models are either baked into the image or downloaded on first run
3. Model paths are correctly mapped to volumes
4. Python dependencies are installed for all custom nodes

## Verification

After installation, verify by:
1. Opening ComfyUI
2. Loading the `v03_retouch_api.json` workflow
3. Checking for missing nodes or models
4. Running a test inference

## Storage Requirements

Total storage needed:
- **Models**: ~37 GB
- **Custom nodes**: ~500 MB
- **Working space**: 10+ GB (for processing)
- **Total recommended**: 50+ GB free space
