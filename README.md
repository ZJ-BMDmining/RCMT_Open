# RCMT_Open
The overview of the multi-scale learning based RCMT method. The primary purpose of cross-scale consensus(CMC) fusion module is to capture cross-modal interactions between MRI samples and transcriptomics data. Meanwhile, the modal modulation rebalancing(MMR) module aims to pursue a trade-off between modality-specific and modality-shared components between two modalities.

## Architecture

![Architecture](./figures/Fig1_RCMT-Framework.png)

## Install

We train the RCMT model under the Ubuntu22.04, and graphics card is RTx4090.

```bash
conda create -n RCMT python==3.8
conda activate RCMT
```

## Requirements

```bash
pip install -r requirements.txt
```

## Data availability

Whole-blood RNA-seq datasets that are related with PD were downloaded from the AMP-PD platform({https://amp-pd.org/}) and is subject to access control. Individuals are required to register in order to access the benchmark datasets. Two group of MRI image data were obtained from Parkinson's Progression Markers Initiative (PPMI)({https://www.ppmi-info.org/}) and Parkinson's Disease Biomarkers Program (PDBP)({https://pdbp.ninds.nih.gov/}), respectively.

## Usage

First, download the required data sets from the PPMI, PDBP, and AMP-PD platforms respectively. Place the files in the corresponding folder.

### MRI-processing

1. Using FSL tools to decranialize MRI brain images.

2. Run MRI-preprocessing/datasets/process_MRI_nobrain.ipynb

### Data-processing

1. Run the processing/datasets/over_aligned.ipynb file to generate a sample-aligned data set and split the training set, validation set, and test set.

2. Run the processing/datasets/process_transpot.ipynb file to make full use of the data set that cannot be sample aligned as a single-modal training set.

3. Run the processing/datasets/split_imagedata_nobrain.ipynb file to make full use of the data set that cannot be sample aligned as a single-modal training set.

The obtained files are located under processed_data/datasets/

### Training

1. Run the training/datasets/evaluation_transpot.ipynb file to get the blood transcriptomics model.

2. Run the training/datasets/evaluation_2D_3slice.ipynb file to get the MRI model.

3. Run the training/datasets/evaluation_aligned_balanced.ipynb file to get the Multi-modal model.

The obtained files are located under models/datasets/
