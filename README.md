# Computer-Vision-Project

University of Haifa computer vision lab project (Summer 2022) based on the paper **"Deep Rectangling for Image Stitching: A Learning Baseline"** (March 2022).

**Authors:** Mustafa Waked (318577921), Layan Haddad (318369709)

## What this project does

The paper addresses image rectangling for stitched panoramas using a learning-based mesh deformation approach. Our coursework extended the training pipeline by applying **geometric augmentation** (crop + scale) to increase usable training samples instead of discarding ~95% of generated data.

## Technologies

- Python
- TensorFlow 1.13.1, Keras 2.2.3 (paper baseline versions)
- Google Colab (GPU training)
- NumPy 1.18.1

## What we implemented

**Chosen modification:** edit the training set with standard geometric augmentations (not seam carving).

**Augmentation approach — crop and scale:**

1. Crop a region from an image.
2. Resize the crop back to the original image dimensions.

| File (in full project on Drive) | Role |
|-----------------------------------|------|
| `DeepRectangling/Codes/inference2.py` | Generates augmented dataset |
| `DeepRectangling/Codes/Data/DIR-D/final_res` | Saved augmentation outputs |

Training and testing follow the original paper README, with paths adjusted for Colab.

## Project structure (this repository)

```
Computer-Vision-Project/
├── README.md
├── Project Report.pdf      # Written report (Hebrew/English coursework doc)
└── .gitignore
```

## Prerequisites

- Python 3.6–3.7 (for legacy TensorFlow 1.x compatibility)
- GPU recommended (we used Google Colab free tier)
- Full codebase and datasets from Google Drive (see below)

## Installation

1. Clone this repository for the report and documentation:

   ```bash
   git clone https://github.com/Mustafa-Waked/Computer-Vision-Project.git
   cd Computer-Vision-Project
   ```

2. Download the full project from Google Drive:

   **[Google Drive — project files](https://drive.google.com/drive/folders/16HMN2rbbD8x2HcculvynC7JIss7dJhaf?usp=sharing)**

3. Extract the Drive folder and follow paths inside the paper codebase (`DeepRectangling/Codes/…`).

## Build

There is no build step in this GitHub repo. After downloading Drive content, install dependencies inside the paper codebase environment (see **Run** below).

## Run

### 1. Generate augmented data

```bash
cd DeepRectangling/Codes
python inference2.py
```

Update input/output paths inside the script for your machine. Results are saved under `Data/DIR-D/final_res`.

### 2. Train on Google Colab (example)

```bash
cd drive/MyDrive/DeepRectangling/Codes
pip install tensorflow==1.13.1
pip uninstall keras -y && pip install keras==2.2.3
pip install numpy==1.18.1
python train.py
```

Use the paper's README for full training/test steps and checkpoint paths.

### 3. Test

Follow the paper README testing instructions after training, updating model and data paths.

## Example workflow

```text
Download Drive → inference2.py (augmentation) → train.py (Colab) → paper test scripts
```

## Expected output

- Augmented images under `Data/DIR-D/final_res`
- Training checkpoints per the paper README
- Testing metrics comparable to the baseline paper; our augmentation aimed to **reduce sample elimination** during data prep, not to change the core rectangling architecture

## Troubleshooting

| Problem | Likely cause | Fix |
|---------|--------------|-----|
| `No module named tensorflow` | Wrong Python version | Use Python 3.6–3.7 and TF 1.13.1 as in the paper. |
| CUDA / GPU errors on Colab | Runtime disconnected or TF version mismatch | Reconnect runtime; reinstall pinned versions above. |
| `inference.py2` not found | Typo in old notes | Use `inference2.py` from the Drive folder. |
| Empty repo after clone | Code lives on Drive | Download the linked Drive folder — this repo is report + docs only. |
| Path errors in scripts | Hard-coded Colab paths | Edit paths in `inference2.py` / `train.py` for your local or Drive layout. |

## Notes / limitations

- Legacy TensorFlow 1.x / Keras 2.x — may require Colab or a controlled Python 3.6–3.7 environment.
- GPU recommended for training; we used free Colab GPUs.
- This repo contains the **report PDF** and documentation only; clone/download Drive content to run code.

## Author

Mustafa Waked & Layan Haddad — University of Haifa, September 2022
