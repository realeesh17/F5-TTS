# F5-TTS: A Fairytaler that Fakes Fluent and Faithful Speech with Flow Matching

[![Python](https://img.shields.io/badge/Python-3.10-brightgreen)](https://github.com/SWivid/F5-TTS)
[![arXiv](https://img.shields.io/badge/arXiv-2410.06885-b31b1b.svg?logo=arXiv)](https://arxiv.org/abs/2410.06885)
[![Demo](https://img.shields.io/badge/GitHub-Demo%20Page-orange.svg)](https://swivid.github.io/F5-TTS/)
[![Hugging Face](https://img.shields.io/badge/🤗-Hugging%20Face%20Demo-yellow)](https://huggingface.co/spaces/mrfakename/E2-F5-TTS)
[![ModelScope](https://img.shields.io/badge/🤖-ModelScope%20Demo-blue)](https://modelscope.cn/studios/modelscope/E2-F5-TTS)
[![X-LANCE Lab](https://img.shields.io/badge/X--LANCE-Lab-grey?labelColor=lightgrey)](https://x-lance.sjtu.edu.cn/)
[![Peng Cheng Lab](https://img.shields.io/badge/Peng%20Cheng-Lab-grey?labelColor=lightgrey)](https://www.pcl.ac.cn)

## Overview
**F5-TTS** is a diffusion transformer with ConvNeXt V2, optimized for faster training and inference. It supports **E2-TTS**, a Flat-UNet Transformer for closest reproduction from [this paper](https://arxiv.org/abs/2406.18009).

**Key Features:**
- **Sway Sampling**: An inference-time flow step sampling strategy that significantly enhances performance.
- **Multi-Style & Multi-Speaker Generation**: Enables flexible and high-quality voice synthesis.
- **Voice Chat**: Powered by **Qwen2.5-3B-Instruct** for interactive conversations.

## Latest Updates
- **2024/10/08**: F5-TTS & E2-TTS base models are now available on:
  - [🤗 Hugging Face](https://huggingface.co/SWivid/F5-TTS)
  - [🤖 ModelScope](https://www.modelscope.cn/models/SWivid/F5-TTS_Emilia-ZH-EN)
  - [🟣 Wisemodel](https://wisemodel.cn/models/SJTU_X-LANCE/F5-TTS_Emilia-ZH-EN)

## Installation

### 1. Setting up the environment
```bash
# Create a Python 3.10 conda environment
conda create -n f5-tts python=3.10
conda activate f5-tts
```

### 2. Installing PyTorch
For different GPUs:
```bash
# NVIDIA GPU (CUDA 11.8)
pip install torch==2.3.0+cu118 torchaudio==2.3.0+cu118 --extra-index-url https://download.pytorch.org/whl/cu118

# AMD GPU (ROCm 6.2, Linux only)
pip install torch==2.5.1+rocm6.2 torchaudio==2.5.1+rocm6.2 --extra-index-url https://download.pytorch.org/whl/rocm6.2

# Intel GPU (XPU support)
pip install --pre torch torchaudio --index-url https://download.pytorch.org/whl/nightly/xpu
```

### 3. Installing F5-TTS
#### As a pip package (for inference only)
```bash
pip install git+https://github.com/SWivid/F5-TTS.git
```

#### Local editable installation (for training & finetuning)
```bash
git clone https://github.com/SWivid/F5-TTS.git
cd F5-TTS
pip install -e .
```

#### Docker usage
```bash
# Build from Dockerfile
docker build -t f5tts:v1 .

# Pull from GitHub Container Registry
docker pull ghcr.io/swivid/f5-tts:main
```

## Inference

### 1. Using Gradio Web App
```bash
# Launch Gradio UI
f5-tts_infer-gradio

# Specify port/host
f5-tts_infer-gradio --port 7860 --host 0.0.0.0

# Launch a share link
f5-tts_infer-gradio --share
```

### 2. Command Line Inference
```bash
# Run with default settings
f5-tts_infer-cli

# Generate audio from text
f5-tts_infer-cli --model "F5-TTS" --gen_text "Hello, world!"
```

## Training & Finetuning
Read [training & finetuning guide](src/f5_tts/train) for detailed instructions.
```bash
# Launch training UI
f5-tts_finetune-gradio
```

## Evaluation
Refer to [evaluation guide](src/f5_tts/eval) for benchmarking and quality assessment.

## Development & Contribution
To maintain code quality:
```bash
pip install pre-commit
pre-commit install
pre-commit run --all-files
```

## Acknowledgements
We acknowledge the contributions from:
- [E2-TTS](https://arxiv.org/abs/2406.18009) for foundational insights.
- Valuable datasets: [Emilia](https://arxiv.org/abs/2407.05361), [LibriTTS](https://arxiv.org/abs/1904.02882), [LJSpeech](https://keithito.com/LJ-Speech-Dataset/).
- Contributors: [lucidrains](https://github.com/lucidrains), [bfs18](https://github.com/bfs18), and others.

## Citation
If you use our work, please cite:
```bibtex
@article{chen-etal-2024-f5tts,
  title={F5-TTS: A Fairytaler that Fakes Fluent and Faithful Speech with Flow Matching},
  author={Yushen Chen, Zhikang Niu, Ziyang Ma, Keqi Deng, Chunhui Wang, Jian Zhao, Kai Yu, Xie Chen},
  journal={arXiv preprint arXiv:2410.06885},
  year={2024}
}
```

## License
- Code: **MIT License**
- Pre-trained models: **CC-BY-NC License** due to the Emilia dataset restrictions.

