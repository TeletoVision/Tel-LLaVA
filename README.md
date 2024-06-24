## Models & Scripts

### Installation

#### 1. **Clone this repository and navigate to the LLaVA folder:**
```bash
git clone https://github.com/LLaVA-VL/LLaVA-NeXT
cd LLaVA-NeXT
```

#### 2. **Install the inference package:**
```bash
conda create -n llava python=3.10 -y
conda activate llava
pip install --upgrade pip  # Enable PEP 660 support.
pip install -e ".[train]"
```

### Project Navigation
Please checkout the following page for more inference & evaluation details.

#### - **LLaVA-NeXT: Stronger LLMs Supercharge Multimodal Capabilities in the Wild**
- [LLaVA-NeXT-Image](./docs/LLaVA-NeXT.md): for image demo inference and evaluation of stronger LMMs using [lmms-eval](https://github.com/EvolvingLMMs-Lab/lmms-eval).


#### - LLaVA-NeXT: A Strong Zero-shot Video Understanding Model
- [LLaVA-NeXT-Video](./docs/LLaVA-NeXT-Video.md): for video inference and evaluation scripts.

#### - LLaVA-NeXT: Tackling Multi-image, Video, and 3D in Large Multimodal Models
- [LLaVA-NeXT-Interleave](./docs/LLaVA-NeXT-Interleave.md): for multi-image demo and evaluation scripts.

## SGLang for SpeedUp Inference and Deployment

We use [SGLang](https://github.com/sgl-project/sglang) to speed up inference and deployment of LLaVA-NeXT. You could make LLaVA-NeXT as a backend API service with SGLang.

**Prepare Environment**:
    Following the instruction in the [sglang](https://github.com/sgl-project/sglang?tab=readme-ov-file#install)

### LLaVA-NeXT (Image)

Checkout the HTTP Post/Get and SRT usage at [sglang/examples/usage/llava](https://github.com/sgl-project/sglang/blob/main/examples/usage/llava)

### LLaVA-NeXT (Video)

**Launch and Run on (K) Nodes**:
- Go to sglang project
    ```
    cd PATH_TO/sglang
    ```
- First node:
    ```sh
    bash examples/usage/llava_video/srt_example_llava_v.sh K 0 YOUR_VIDEO_PATH YOUR_MODEL_PATH FRAMES_PER_VIDEO
    (e.g. bash examples/usage/llava_video/srt_example_llava_v.sh K 0 examples/usage/llava_video/videos/Q98Z4OTh8RwmDonc.mp4 lmms-lab/LLaVA-NeXT-Video-7B-DPO 16)
    ```
- Second node:
    ```sh
    bash examples/usage/llava_video/srt_example_llava_v.sh K 1 YOUR_VIDEO_PATH YOUR_MODEL_PATH FRAMES_PER_VIDEO
    ```
- The K node:
    ```sh
    bash examples/usage/llava_video/srt_example_llava_v.sh K K-1 YOUR_VIDEO_PATH YOUR_MODEL_PATH FRAMES_PER_VIDEO
    ```


## Citation

If you find it useful for your research and applications, please cite related papers/blogs using this BibTeX:
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
