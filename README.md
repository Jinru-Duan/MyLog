# Lyapunov Joint Optimization Controller (FoV + Diffusion + Keyframe)

This project implements a Lyapunov drift-plus-penalty controller for **real-time, multi-variable optimization** in immersive/360° video streaming. The controller jointly decides:
- **FoV radius** (viewport-adaptive compression)
- **Diffusion enhancement** on/off (peripheral perceptual enhancement)
- **Keyframe timing** (adaptive keyframe placement)

It tracks **quality debt** and **latency debt** via **two virtual queues**, enabling stable control under dynamic bandwidth/latency constraints.

## Contents
- `Final_Project.ipynb` — main notebook (Google Colab friendly)
- Outputs saved to `WORK_DIR` (plots, JSON logs, model weights)

## Dependencies
The notebook installs dependencies directly. Key packages:
- `torch`
- `compressai`
- `opencv-python-headless`
- `matplotlib`
- `lpips`
- `tqdm`, `pandas`, `numpy`
- (optional) `diffusers`, `accelerate` (installed in the diffusion section)

System tools (recommended):
- `ffmpeg` (used for video format conversion)

## Quick Start (Recommended: Google Colab)
1. Open `Final_Project.ipynb` in **Google Colab**
2. Run cells **top-to-bottom**:
   - **Preparation**: installs deps + checks GPU
   - **Main**: FoV-aware compressor and core utilities
   - **Download Data**: downloads a test video to your working directory
   - Experiments: run the sections you need (FoV compression, Lyapunov control, diffusion module, ablation, codec comparison)

> The notebook includes Google Drive mounting; you can keep it (Colab) or remove it (local).

## Running Locally (Optional)
1. Create an environment and install deps:
   ```bash
   pip install compressai opencv-python-headless matplotlib lpips pandas tqdm
