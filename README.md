## Introduction
A deep learning model for predicting interactions between nucleic acids and small molecules

## System Requirements
### Operating System
- Tested on: **Ubutun 24.04.2 LTS** 

### Hardware Requirements

- An NVIDIA GPU with CUDA support is required.
- Tested on: **NVIDIA GeForce RTX 2080Ti (12 GB VRAM)**.
- Recommended minimum: GPU with ≥ 8 GB VRAM.
- No other non-standard hardware is required.

### Software Dependencies

- **Python** 3.8
- **CUDA** 11.3 (the GPU driver must support CUDA ≥ 11.3); tested with NVIDIA driver supporting CUDA 12.2)
- Key Python packages (full list in `requirements.txt`):
    - `torch==1.12.1+cu113`
    - `dgl-cu113==0.9.1.post1`
    - `dgllife==0.3.2`
    - `rekit==2024.3.5`
    - `numpy==1.24.4`
    - `scikit-learn==1.3.2`
    - `pandas==2.0.3`
    - `matplotlib==3.5.5`

### Tested Version;

The code has been tested on:

- Ubuntu 24.04.2 LTS
- Python 3.8
- Pytorch 1.12.1 + CUDA 11.3
- NVIDIA GeForce RTX 2080 Ti

---

## Installation Guide

### Step 1: Clone the repository

```bash
git clone https://github.com/LuChen-JN/FNA-SpeEvo.git
cd FNA-SpeEvo
```

### Step 2: Create the conda enviroment

```bash
conda create -n FNA-SpeEvo python=3.8 -y
conda activate FAN-SpeEvo
```

### Step 3: Install Pytorch (CUDA 11.3)

```bash
pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 --extra-index-url https://download.pytorch.org/whl/cu113
```

### Step 4：Install DGL (CUDA 11.3)

```bash
pip install dgl-cu113 -f https://data.dgl.ai/wheels/repo.html
```

### Step 5: Install RDKit

```bash
conda install -c conda-forge rdkit -y
```

### Step 6: Install remaining dependencies

```bash
pip install -r requirements.txt
```

### Verify installation
```bash
python -c "import torch; print('Pytorch:', torch.__version__); print('CUDA available:', torch.cuda.is_available()); print('GPU:', torch.cuda.get_device_name(0))"
python -c "import dgl; print('DGL:', dgl.__version__)"
python -c "imoprt dellife, rdkit; print('dgllife:', dgllife.__version__, '| rdkit:', rdkit.__version__)"
```

**Typocall install time**: approximately **15-20 minutes** on a normal desktop computer with a stable internet connection.

---

## Demo for train

A small demonstration dataset is provided at `/demo/fold_1/`, containing `train.csv`, `val.csv`, and `test.csv`.

### Run the demo

```bash
python main.py --data /demo/fold_1/
```

### Expected output

- `test_results.txt`
- `train_results.txt`
- `dev_results.txt`
- `model.pt`

### Execpted runtime

- Approximately **30-60 minutes** on a desktop with NVIDIA RTX 2080 Ti.

---
## Demo for predict

A small demonstration dataset is provided at `/demo/`, containing `predict.csv`.

### Run the demo

```bash
python application.py --data /demo/
```

### Expected output

- `predict.txt`

### Execpted runtime

- Approximately **30-60 minutes** on a desktop with NVIDIA RTX 2080 Ti.

---

### Instructions for Use

### Input data format

The input CSV files must contain the following columns:

| Column      | Type    | Description                                                  | 
| ----------- | ------- | ------------------------------------------------------------ |
| `ID`        | string  | Unique identifier for each sanmple                           |
| `Sequence`  | string  | Nucleic acid sequence (DNA / RNA)                            |
| `SMILES`    | string  | SMILES representation of the small molecule                  |
| `Y`         | numeric | Interaction lable / value (binary label or continuous score) |

Place your data under `/datasets/<your_folder_name>/` with the three files:

- `train.csv`
- `test.csv`
- `val.csv`

### Running on your own data

```bash
python main.py --data /datasets/<your_folder_name>
```

The `--data` argument is the **folder name** under `datasets/`. Default: `Model-guided evolution of riboswitch activity`.

---

## License
This project is licensed under the **MIT Licese** - see the [LICENSE](LICENSE) file for details.

---

## Data Sources
Our data contain aptamer and riboswitch datasets. For aptamers, the data were collected from numerous literature collections and websites, including the following websites involved in the article:
1. https://www.aptamer.org/
2. https://www.aptagen.com/
3. https://sites.utexas.edu/aptamerdatabase/
Note: The aptamer database has been updated once since the work involved in the model was completed.

Riboswitch data from：
https://riboswitch.ribocentre.org/

