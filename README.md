# Stable Diffusion (reForge) with Paperspace

This is an installation guide for dummies using Paperspace $8 tier. It installs the (reForge)[https://github.com/Panchovix/stable-diffusion-webui-reForge] web UI, allowing you to generate images.

It only uses the models I gave it (I think you need to change the launcher to change that) but idc this is for my purposes, cry

shoutout to **Shalie** for telling me how tf to do this <3

## Prerequisites

create notebook (from scratch) auto shutdown always on 6h and select free a4000

view advanced options, we will change the container to have python 3.10.10, put `cyberes/gradient-base-py3.10:latest` as container name then create

## Installation

```
git clone https://github.com/lucoalove/PaperspaceStableDiffusion
```

```
git clone https://github.com/Panchovix/stable-diffusion-webui-reForge.git
cd stable-diffusion-webui-reForge
git checkout main
```

Refresh the file explorer.

Open `/stable-diffusion-webui-reForge/webui.sh`

CTRL+F "root"

Replace line `can_run_as_root=0` with `can_run_as_root=1`

Save the file

```
python -m venv venv
source venv/bin/activate
```

open `webui-user.sh` and paste this at the bottom
```
export COMMANDLINE_ARGS="--xformers --share"
export ACCELERATE="True"
```

### Set up venv

Venv allows for persistent storage (we install stuff here so it is kept installed in venv).

```
pip install torch==2.1.2 torchvision==0.16.2 torchaudio==2.1.2 --index-url https://download.pytorch.org/whl/cu118
pip install xformers==0.0.23.post1 --index-url https://download.pytorch.org/whl/cu118
pip install bitsandbytes==0.43.3
python -m bitsandbytes
```

```
pip install pillow-avif-plugin==1.4.3
pip install aiofiles==23.2.1
pip install altair==4.2.2
pip install diskcache
pip install easygui==0.98.3
pip install einops==0.7.0
pip install fairscale==0.4.13
pip install ftfy==6.2.3
pip install huggingface-hub==0.24.6
pip install imagesize==1.4.1
pip install invisible-watermark==0.2.0
pip install omegaconf==2.3.0
pip install onnx==1.16.1
pip install accelerate==0.33.0
pip install transformers==4.44.0
pip install open-clip-torch==2.20.0
pip install protobuf==4.25.4
pip install pytorch-lightning==1.9.4
pip install rich==13.8.0
pip install diffusers[torch]==0.29.2
pip install opencv-python==4.10.0.84
pip install safetensors
pip install sentencepiece==0.2.0
pip install timm==1.0.9
pip install tk==0.1.0
pip install easygui==0.98.3
pip install toml==0.10.2
pip install voluptuous==0.13.1
pip install wandb==0.15.11
pip install asyncer
pip install filetype
pip install ImageHash
pip install watchdog
pip install datasets transformers
pip install scipy scikit-learn
pip install triton
pip install pip -U prodigyopt
pip install lycoris_lora
pip install dadaptation
pip install pytorch-optimizer
pip install came_pytorch
```

## Running

1. Start with machine "Free-A4000"
2. Open `launcher.ipynb` and press "RUN ALL"; wait for it to finish
3. Open a command prompt and run:
```
cd /notebooks/PaperspaceStableDiffusion/stable-diffusion-webui-reForge
source venv/bin/activate
./webui.sh
```
