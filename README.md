# Qwen Image 2.1 — Google Colab Notebooks

Ready-to-use Google Colab notebooks for **Qwen Image 2.1** covering:

- batch image editing
- multi-reference image mixing/editing
- text-to-image generation

Built around the official `Qwen/Qwen-Image-2.1` Diffusers pipeline and tested on Google Colab with an **NVIDIA A100 80 GB**.

## Notebooks

### 1. Batch Image Editing
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DikeInside/qwen-image-2.1-colab-/blob/main/Qwen_Image_2.1_Edit_Batch_Final.ipynb)

Edit all images inside a Google Drive input folder with one prompt. Every run creates a new timestamped output folder and saves the prompt/settings used.

### 2. Multi-Reference Editing
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DikeInside/qwen-image-2.1-colab-/blob/main/Qwen_Image_2.1_Multi_Reference.ipynb)

Use **2–10 reference images** in one generation.

Example:

> Put the dress from the first image on the person in the second image. Preserve the person's identity and the dress design.

Reference images are read in alphabetical order, so filenames such as `01_dress.png` and `02_person.png` make ordering explicit.

### 3. Text-to-Image
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DikeInside/qwen-image-2.1-colab-/blob/main/Qwen_Image_2.1_Text_to_Image.ipynb)

Generate images from scratch with selectable prompt, seed, variants, aspect ratio, and 1K/2K presets.

## Recommended Colab setup

For the simplest experience:

- **GPU:** NVIDIA A100
- **High RAM:** enabled when available
- **Runtime:** latest recommended Python runtime

The full BF16 model is large. Smaller GPUs may require quantization and CPU offload; these notebooks intentionally avoid that extra complexity.

## Starting a fresh Colab session

Each notebook follows the same flow:

1. select the GPU runtime;
2. run the installation cell;
3. use **Runtime → Restart session**;
4. continue from **Load Qwen Image 2.1**;
5. connect Google Drive if required;
6. set prompt/options;
7. run generation.

Do **not** manually upgrade Torch or CUDA in Colab unless you specifically need to.

## Steps and seed

Practical starting points:

| Steps | Use |
|---:|---|
| 20 | fast experiments |
| 30 | daily compromise |
| 40 | final/high-quality runs |

The **seed does not control quality**. Keep a fixed seed such as `42` for reproducibility; change it to explore variations.

## Resolution

### Image editing / multi-reference

The notebooks expose `OUTPUT_RESOLUTION`.

- `1024`: good default for experiments
- `2048`: final output when you want more resolution and have enough GPU headroom

### Text-to-image 2K presets

| Ratio | Resolution |
|---|---:|
| 1:1 | 2048×2048 |
| 4:3 | 2400×1792 |
| 3:4 | 1792×2400 |
| 3:2 | 2528×1696 |
| 2:3 | 1696×2528 |
| 16:9 | 2752×1536 |
| 9:16 | 1536×2752 |

## Google Drive folders

The batch editor uses:

```text
MyDrive/Qwen/
├── input/
└── output/
    └── YYYY-MM-DD_HH-MM-SS/
```

Each output folder also stores:

- `prompt.txt`
- `settings.json`

The multi-reference notebook uses `MyDrive/QwenMulti/`, while text-to-image uses `MyDrive/QwenT2I/`.

## Compute Units

Premium Colab GPU runtimes consume Compute Units while allocated. An A100 consumes them much faster than a T4.

When finished, disconnect/delete the runtime instead of only closing the browser tab.

## Upstream projects

- Qwen Image 2.1: https://huggingface.co/Qwen/Qwen-Image-2.1
- Diffusers: https://github.com/huggingface/diffusers
- Google Colab: https://colab.research.google.com/

## Notes

These notebooks are convenience wrappers for the upstream open-source ecosystem and are not affiliated with the Qwen team, Hugging Face, or Google.

Model use remains subject to the license and terms published with **Qwen/Qwen-Image-2.1**.
