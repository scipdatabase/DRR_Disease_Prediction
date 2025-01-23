# DRR Disease Classification and Scoring Model

## Overview
This model classifies chickpea root images captured by cameras, root scanners, and microscopes into the following categories:
- **Control (Healthy)**
- **DRR (Dry Root Rot)**
- **Non-DRR (Diseases other than DRR)**

Additionally, it scores DRR images on a scale of **1 to 5**.

---

## Installation
### Clone the Repository:
```bash
git clone https://github.com/<your_repo>/your-model.git
cd your-model
```

### Download Code as ZIP:
1. Look for the green "Code" button on the repository page.
2. Click on the "Code" button.
3. Select "Download ZIP" from the dropdown.
4. Save and extract the ZIP file to access the code.

---

## Required Packages
Ensure you have **Python (version: 3.9.16)** installed. The following packages are required:
- **TensorFlow** (version: 2.10.1)
- **Keras** (version: 2.10.0)
- **Pandas**
- **NumPy**

Install the dependencies using:
```bash
pip install tensorflow==2.10.1 keras==2.10.0 pandas numpy
```

---

## Image Capture Guidelines
### Instructions:
- **Camera Images**: Ensure a red background.
- **Root Scanner Images**: Ensure a blue background.

---

## Models
### Available Models for Classification and Scoring
| MODEL                        | Camera         | Root Scanner   | Microscope      |
|------------------------------|----------------|----------------|-----------------|
| **new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR**       | Control, DRR   | Control, DRR   | Control, DRR    |
| **new_2cls_7cls_trained_ViT_E_7_eps_200_bs_32_onlyControlDRR**     | Control, DRR   | Control, DRR   | Control, DRR    |
| **new_DRR_MTL_3c_1R_200e_32BS**  | Control, DRR + Non DRR | Control, DRR + Non DRR | Control, DRR + Non DRR |
| **DRR_MTL_3c_1R_500e**  | Control, DRR, Non DRR  | Control, DRR, Non DRR  | Control, DRR, Non DRR  |
| **new_2cls_1R_trained_ViT_A2_eps_200_bs_32_onlyControlDRR**      | X              | Control, DRR   | X               |
| **new_2cls_1R_trained_ViT_A3_eps_200_bs_32_onlyControlDRR**      | X              | X              | Control, DRR    |
| **DRR_single_task_1R_200e** | X              | X              | X               |

---

### Python Script for Each Model
| MODEL                        | CODE           |
|------------------------------|----------------|
| **new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR**       | ViT 2C-1R      |
| **new_2cls_7cls_trained_ViT_E_7_eps_200_bs_32_onlyControlDRR**     | ViT 2C-7C      |
| **new_DRR_MTL_3c_1R_200e_32BS**  | Xception 2C-1R |
| **DRR_MTL_3c_1R_500e**  | Xception 3C-1R |
| **new_2cls_1R_trained_ViT_A2_eps_200_bs_32_onlyControlDRR**      | ViT 2C-1R      |
| **new_2cls_1R_trained_ViT_A3_eps_200_bs_32_onlyControlDRR**      | ViT 2C-1R      |
| **DRR_single_task_1R_200e** | Xception 1R   |

---

### Recommended Models
| Image Type      | Recommended Model          |
|-----------------|----------------------------|
| **Camera**      | new_2cls_1R_trained_ViT_E_7_eps_500_bs_32_onlyControlDRR        |
| **Root Scanner**| new_2cls_1R_trained_ViT_A2_eps_200_bs_32_onlyControlDRR    |
| **Microscope**  | new_DRR_MTL_3c_1R_200e_32BS   |

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
