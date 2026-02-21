# DRR Disease Classification and Scoring Model
## Introduction
Dry Root Rot (DRR), caused by the fungal pathogen Macrophomina phaseolina,
emerging as a global disease in chickpea leading to a significant yield loss and is
worsened by drought conditions. Disease symptoms include brittle tap root, brown to
black lesions on the roots, progressing to decay and devoid of lateral roots.
Development of resistant cultivars and accurate assessment and identification of the
disease is an important management strategy to overcome the disease. Various
evaluation techniques including sick plot, sick pot and blotting paper technique are
used to identify resistant cultivar and to the study the disease expression in
chickpea. Among these methods, blotting paper technique stands out as a high-
throughput technique for screening a large number of genotypes in a short span of
time. However, the manual method of disease scoring followed for disease
assessment is inaccurate, subjective to individual and prone to bias. Therefore, there
is a pressing need for improving the accuracy through recent advancements in deep
learning for augmentation and automation of images analysis for disease prediction.
Here, we used two different architectures Xception and ViT to develop a deep
learning model for early, non-invasive detection of DRR in chickpeas, providing a
valuable tool for high-throughput
## Overview
This model classifies chickpea root images captured by cameras, root scanners, and microscopes into the following categories:
- **Control (Healthy)**
- **DRR (Dry Root Rot)**
- **Non-DRR (Diseases other than DRR)**

Additionally, it scores DRR images on a scale of **1 to 5**.

---

## Image Dataset 
A total of 10,800 images were collected from the chickpea core collection (n=500). The chickpea core collection is a representative subset of global germplasm, established based on geographical origin and 13 quantitative traits to captures over 80% of diversity found in the entire collection. The collection used in this study is housed and maintained at the Genbank, International Crops Research Institute for the Semi-Arid Tropics, Patancheru, India (https://genebank.icrisat.org/IND/Core?Crop=Chickpea). Our study, utilized the mini-core collection (https://db.nipgr.ac.in/cdpdb/Germplasm.php) which is a further refined subset of the core collection, supplemented with additional accessions from the core collection (https://genebank.icrisat.org/IND/Core?Crop=Chickpea).



---

##  Clone the Repository


#### Requirements:
- [Git](https://git-scm.com/)
- [Git LFS](https://git-lfs.github.com/)

Download **all models, scripts, and folders**:

```bash
git clone https://github.com/scipdatabase/DRR_Disease_Prediction.git
cd DRR_Disease_Prediction
git lfs install
git lfs pull
```

---

Download a particular model
```bash
Install git and gitlfs and run the following code in gitbash
clone --filter=blob:none --no-checkout https://github.com/scipdatabase/DRR_Disease_Prediction.git DRR_Disease_Prediction_new
cd DRR_Disease_Prediction_new

git sparse-checkout init --cone
git sparse-checkout set new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR (replace with your desired model name)

git checkout main
git lfs pull
```
---

## Required Packages
Ensure you have **Python (version: 3.8.2)** installed. The following packages are required:
- **TensorFlow** (version: 2.10.0)
- **Keras** (version: 2.10.0)
- **Pandas** (version: 1.3.5)
- **NumPy** (version: 1.21.6)
- **Tensorflow-addons** (version 0.21.0)
- **openpyxl**


---

## Image Capture Guidelines
### Instructions:
- **Camera Images**: Ensure a red background.
- **Root Scanner Images**: Ensure a blue background.

---

## Models
### Available Models for Classification
| S.No | Model               | Dataset | Model File                                               | Camera                 | Root Scanner            | Microscope             |
|:----:|---------------------|:--------:|----------------------------------------------------------|------------------------|-------------------------|------------------------|
| 1 | ViT MTL 2Cls 1R | E | **new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR** | Control, DRR | Control, DRR | Control, DRR |
| 2 | ViT MTL 2Cls 6Cls | E | **new_2cls_7cls_trained_ViT_E_7_eps_200_bs_32_onlyControlDRR** | Control, DRR | Control, DRR | Control, DRR |
| 3 | Xception MTL 2Cls 1R | E | **new_DRR_MTL_3c_1R_200e_32BS** | Control, DRR + Non DRR | Control, DRR + Non DRR | Control, DRR + Non DRR |
| 4 | Xception MTL 3Cls 1R | E | **DRR_MTL_3c_1R_500e** | Control, DRR, Non DRR | Control, DRR, Non DRR | Control, DRR, Non DRR |
| 5 | ViT MTL 2Cls 1R | A2 | **new_2cls_1R_trained_ViT_A2_eps_200_bs_32_onlyControlDRR** | X | Control, DRR | X |
| 6 | ViT MTL 2Cls 1R | A3 | **new_2cls_1R_trained_ViT_A3_eps_200_bs_32_onlyControlDRR** | X | X | Control, DRR |
| 7 | Xception STL 1R | D | **DRR_single_task_1R_200e** | X | X | X |

---

### Available Models for Scoring
| S.No | Model | Dataset | Model File | Camera | Root Scanner | Microscope |
|:----:|--------|:--------:|-------------|:--------:|:--------------:|:-------------:|
| 1 | ViT MTL 2Cls 1R | E | **new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR** | 0–5 | 0–5 | 0–5 |
| 2 | ViT MTL 2Cls 6Cls | E | **new_2cls_7cls_trained_ViT_E_7_eps_200_bs_32_onlyControlDRR** | 0–5 | 0–5 | 0–5 |
| 3 | Xception MTL 2Cls 1R | E | **new_DRR_MTL_3c_1R_200e_32BS** | 0–6 | 0–6 | 0–6 |
| 4 | Xception MTL 3Cls 1R | E | **DRR_MTL_3c_1R_500e** | 0–6 | 0–6 | 0–6 |
| 5 | ViT MTL 2Cls 1R | A2 | **new_2cls_1R_trained_ViT_A2_eps_200_bs_32_onlyControlDRR** | X | 0–5 | X |
| 6 | ViT MTL 2Cls 1R | A3 | **new_2cls_1R_trained_ViT_A3_eps_200_bs_32_onlyControlDRR** | X | X | 0–5 |
| 7 | Xception STL 1R | D | **DRR_single_task_1R_200e** | 0–6 | X | 0–6 |

---

### Python Script for Each Model
| S.No | Model | Dataset | Model File | Code |
|:----:|--------|:--------:|-------------|:------:|
| 1 | ViT MTL 2Cls 1R | E | **new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR** | ViT 2C-1R |
| 2 | ViT MTL 2Cls 6Cls | E | **new_2cls_7cls_trained_ViT_E_7_eps_200_bs_32_onlyControlDRR** | ViT 2C-7C |
| 3 | Xception MTL 2Cls 1R | E | **new_DRR_MTL_3c_1R_200e_32BS** | Xception 2C-1R |
| 4 | Xception MTL 3Cls 1R | E | **DRR_MTL_3c_1R_500e** | Xception 3C-1R |
| 5 | ViT MTL 2Cls 1R | A2 | **new_2cls_1R_trained_ViT_A2_eps_200_bs_32_onlyControlDRR** | ViT 2C-1R |
| 6 | ViT MTL 2Cls 1R | A3 | **new_2cls_1R_trained_ViT_A3_eps_200_bs_32_onlyControlDRR** | ViT 2C-1R |
| 7 | Xception STL 1R | D | **DRR_single_task_1R_200e** | Xception 1R |


### Recommended Models
| Image Type      | Model               | Dataset | Model File |
|:----------------|:--------------------|:--------:|:------------|
| **Camera**      | ViT MTL 2Cls 1R     | E  | **new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR** |
| **Root Scanner**| ViT MTL 2Cls 1R     | E | **new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR**|
| **Microscope**  | ViT MTL 2Cls 1R     | A3 | **new_2cls_1R_trained_ViT_A3_eps_200_bs_32_onlyControlDRR** |


---

## Running the Model
1. Provide the following paths:
   - **Model Path**: Location of the model file.
   - **Base Path**: Folder containing the image files.
   - **Output Path**: Excel file location to store the results.
2. Ensure the base path contains folders of images, and all images are in `.png` format.

Run the code to execute the model.

---

## Output
- The results will be displayed in the program window.
- Data will be saved to the specified Excel file.
  - **Control Images**: Assigned a score of 0.
  - **Non-DRR Images**: Assigned a score of 6.
