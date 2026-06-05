# Computer-Vision-Project

University of Haifa computer vision lab project (Summer 2022) based on the paper **"Deep Rectangling for Image Stitching: A Learning Baseline"** (March 2022).

**Authors:** Mustafa Waked (318577921), Layan Haddad (318369709)

## Description

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

| File (in full project) | Role |
|------------------------|------|
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

## Full source code

Source code and datasets are **not stored in this GitHub repo** due to size. They are available here:

**[Google Drive — project files](https://drive.google.com/drive/folders/16HMN2rbbD8x2HcculvynC7JIss7dJhaf?usp=sharing)**

Download the Drive folder, then follow paths inside the paper codebase (`DeepRectangling/Codes/…`).

## How to run (from Drive download)

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

Use the paper’s README for full training/test steps and checkpoint paths.

### 3. Test

Follow the paper README testing instructions after training, updating model and data paths.

## Expected results

Testing metrics should be comparable to the baseline paper; the goal of our augmentation was to **reduce sample elimination** during training data preparation, not to change the core rectangling model architecture.

## Notes / limitations

- Legacy TensorFlow 1.x / Keras 2.x — may require Colab or a controlled Python 3.6–3.7 environment.
- GPU recommended for training; we used free Colab GPUs.
- This repo contains the **report PDF** and documentation only; clone/download Drive content to run code.
- Typo in original notes: script referenced as `inference.py2` in places — verify actual filename in Drive (`inference2.py`).

## Author

Mustafa Waked & Layan Haddad — University of Haifa, September 2022
