## Pipline & Scripts

### Installation

#### 1. **Enviornments:**
Docker Image nvidia cuda == 12.1.0
```bash
docker pull nvcr.io/nvidia/cuda:12.1.0-cudnn8-devel-ubuntu20.04
```
Nvidia RTX A6000

#### 2. **Install the Anaconda virtual environment:**
Get install file at Anaconda homepage.
```bash
wget https://repo.anaconda.com/archive/Anaconda3-2024.02-1-Linux-x86_64.sh
bash Anaconda3-2024.02-1-Linux-x86_64.sh
export PATH=~/anaconda3/bin:$PATH
conda config --set auto_activate_base True
conda init
source ~/.bashrc
conda
```

#### 3. **Clone LLaVA-NeXT repository and navigate to the LLaVA folder:**
```bash
git clone https://github.com/LLaVA-VL/LLaVA-NeXT
cd LLaVA-NeXT
```

#### 4. **Install the inference package:**
```bash
conda create -n llava python=3.10 -y
conda activate llava
pip install --upgrade pip  # Enable PEP 660 support.
pip install -e ".[train]"
```

#### 5. **Install SGLang repository in LLaVA folder:**
SGLang for SpeedUp Inference and Deployment.
We use [SGLang](https://github.com/sgl-project/sglang) to speed up inference and deployment of LLaVA-NeXT. You could make LLaVA-NeXT as a backend API service with SGLang.
```bash
git clone https://github.com/sgl-project/sglang.git
cd sglang

pip install "sglang[all]"
```
And we need opencv pakage for linux environment.
```
apt-get install libgl1-mesa-glx
apt-get install libglib2.0-0
pip install opencv-python
```

#### 6. **Download fixed code in video_demo.py, video_demo.sh:**
We fix 'mlp_bias' and directory problems 
```
video_demo2.sh
video_demo2.py
```

### LLaVA-NeXT (Video)

**Launch and Run on (K) Nodes**:
- Run SGLang LLaVA-NeXT Video
    ```python
    python <ROOT PATH>/LLaVA-NeXT/sglang/examples/usage/llava_video/srt_example_llava_v.py
    ```
- Run LLaVA-NeXT Video Demo
    ```bash
    # scripts/video/demo/video_demo2.sh에서 ROOT PATH 변경하기 (현재 LLaVA-NeXT/)
    bash scripts/video/demo/video_demo2.sh lmms-lab/LLaVA-NeXT-Video-7B-DPO vicuna_v1 40 2 True ./data/UCF-crime/Abuse001_x264.mp4
    ```

## Citation

```bibtex
@misc{li2024llavanext-strong,
    title={LLaVA-NeXT: Stronger LLMs Supercharge Multimodal Capabilities in the Wild},
    url={https://llava-vl.github.io/blog/2024-05-10-llava-next-stronger-llms/},
    author={Li, Bo and Zhang, Kaichen and Zhang, Hao and Guo, Dong and Zhang, Renrui and Li, Feng and Zhang, Yuanhan and Liu, Ziwei and Li, Chunyuan},
    month={May},
    year={2024}
}

@misc{zhang2024llavanextvideo,
  title={LLaVA-NeXT: A Strong Zero-shot Video Understanding Model},
  url={https://llava-vl.github.io/blog/2024-04-30-llava-next-video/},
  author={Zhang, Yuanhan and Li, Bo and Liu, haotian and Lee, Yong jae and Gui, Liangke and Fu, Di and Feng, Jiashi and Liu, Ziwei and Li, Chunyuan},
  month={April},
  year={2024}
}

@misc{liu2024llavanext,
    title={LLaVA-NeXT: Improved reasoning, OCR, and world knowledge},
    url={https://llava-vl.github.io/blog/2024-01-30-llava-next/},
    author={Liu, Haotian and Li, Chunyuan and Li, Yuheng and Li, Bo and Zhang, Yuanhan and Shen, Sheng and Lee, Yong Jae},
    month={January},
    year={2024}
}

@misc{liu2023improvedllava,
      title={Improved Baselines with Visual Instruction Tuning}, 
      author={Liu, Haotian and Li, Chunyuan and Li, Yuheng and Lee, Yong Jae},
      publisher={arXiv:2310.03744},
      year={2023},
}

@misc{liu2023llava,
      title={Visual Instruction Tuning}, 
      author={Liu, Haotian and Li, Chunyuan and Wu, Qingyang and Lee, Yong Jae},
      publisher={NeurIPS},
      year={2023},
}
```
