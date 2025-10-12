# RFdiffusion for Apple Silicon (MPS Support)

This repository provides a modified version of RFdiffusion with MPS (Metal Performance Shaders) support for Apple Silicon Macs.

## Features

- Full MPS support for Apple Silicon GPUs
- Optimized for macOS
- Compatible with all RFdiffusion functionalities

## Related Repositories

- Original RFdiffusion: [RosettaCommons/RFdiffusion](https://github.com/RosettaCommons/RFdiffusion)
- MPS-test branch: [YaoYinYing/RFdiffusion](https://github.com/YaoYinYing/RFdiffusion/tree/mps-test)

## Acknowledgments

- Original RFdiffusion authors from [RosettaCommons](https://github.com/RosettaCommons)
- [YaoYinYing](https://github.com/YaoYinYing) for MPS adaptations

## Installation

### Prerequisites

- macOS with Apple Silicon (M1/M2/M3/M4)
- Conda package manager

### Step-by-Step Installation

1. **Clone the repository and switch to mps-test branch**
   ```bash
   git clone https://github.com/YaoYinYing/RFdiffusion.git
   cd RFdiffusion
   git checkout mps-test
   ```
2. **Create and activate conda environment**
   ```bash
   conda env create -f env/SE3nv_macos.yml
   conda activate RFdiffusion
   ```
3. **Install PyTorch with MPS support**
   ```bash
   conda install 'pytorch==2.3.0' torchvision torchaudio -c pytorch
   ```
4. **Install additional dependencies**
   ```bash
   pip install 'dgl==2.2.1' -f https://data.dgl.ai/wheels/repo.html
   pip install git+https://github.com/YaoYinYing/nvtx-mock --force-reinstall
   pip install nvtx
   pip install git+https://github.com/YaoYinYing/SE3Transformer@rfdiffusion-mps-test
   pip install git+https://github.com/NVIDIA/dllogger#egg=dllogger
   pip install pydantic
   ```
5. **Download model files**
   ```bash
   mkdir models && cd models
   wget https://files.ipd.uw.edu/pub/RFdiffusion/6f5902ac237024bdd0c176cb93063dc4/Base_ckpt.pt
   wget https://files.ipd.uw.edu/pub/RFdiffusion/e29311f6f1bf1af907f9ef9f44b8328b/Complex_base_ckpt.pt
   wget https://files.ipd.uw.edu/pub/RFdiffusion/60f09a193fb5e5ccdc4980417708dbab/Complex_Fold_base_ckpt.pt
   wget https://files.ipd.uw.edu/pub/RFdiffusion/74f51cfb8b440f50d70878e05361d8f0/InpaintSeq_ckpt.pt
   wget https://files.ipd.uw.edu/pub/RFdiffusion/76d00716416567174cdb7ca96e208296/InpaintSeq_Fold_ckpt.pt
   wget https://files.ipd.uw.edu/pub/RFdiffusion/5532d2e1f3a4738decd58b19d633b3c3/ActiveSite_ckpt.pt
   wget https://files.ipd.uw.edu/pub/RFdiffusion/12fc204edeae5b57713c5ad7dcb97d39/Base_epoch8_ckpt.pt
   cd ../
   ```
6. **Install RFdiffusion in editable mode**
   ```bash
   pip install -e .
   ```


