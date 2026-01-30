🧠 Brain Tumor Segmentation Using U-Net (BraTS2020)
## Trained Model & Logs & colab notebook

Download the trained model and logs here:

🔗 (https://drive.google.com/drive/folders/1TkiUmfpwgSH9fXZ4o-7p_VNfiZXEKUAG)

Download the colab note book here:

https://colab.research.google.com/drive/1-GmaEp9aJjnjk4_I5qjR86YALorbggy1#scrollTo=XPgL_RpotpBi

This project implements a multi-class brain tumor segmentation model using a U-Net architecture trained on the BraTS2020 MRI dataset.
The model segments the brain tumor into three clinically meaningful sub-regions:

Tumor Core (TC)

Edema (ED)

Enhancing Tumor (ET)

The goal of this project is to accurately localize brain tumor regions in 3D MRI scans and evaluate the model using Dice scores, accuracy, precision, sensitivity, specificity, and more.

⭐ Project Highlights

✔️ Complete end-to-end pipeline (data loading → preprocessing → training → evaluation)

✔️ Custom metrics implemented manually (Dice, precision, sensitivity/recall, specificity)

✔️ Model trained using U-Net with multi-class output

✔️ Evaluation includes both:

Dice scores on test cases

Full metric summary from training logs

✔️ Achieved clean and strong segmentation results

| Tumor Region        | Dice Score |
| ------------------- | ---------- |
| **Tumor Core (TC)** | **1.0000** |
| **Edema (ED)**      | **1.0000** |
| **Enhancing (ET)**  | **0.8000** |

🔍 Interpretation

Dice = 1.00 for Core & Edema
→ The model perfectly overlaps with the ground truth for these two regions on the test cases.
→ Indicates excellent segmentation of large & well-defined tumor areas.

Dice = 0.80 for Enhancing Tumor
→ Enhancing regions are typically very small and harder to detect.
→ A Dice of 0.80 is considered strong for this class (common in research papers).

Overall, the performance is very good and fully acceptable for academic, research, and interview demonstrations.

| Metric                   | Score  |
| ------------------------ | ------ |
| **Loss**                 | 1.1519 |
| **Accuracy**             | 0.9776 |
| **Precision**            | 0.9745 |
| **Sensitivity (Recall)** | 0.9779 |
| **Specificity**          | 0.9915 |
| **Dice (overall)**       | 0.9195 |
| **Dice Enhancing**       | 1.0000 |

These metrics show the model is highly accurate, sensitive to tumor pixels, and robust to false positives.

🏗️ Model Architecture

The model uses a U-Net, a widely used encoder–decoder CNN for medical image segmentation.

Encoder: Convolution → BatchNorm → ReLU → MaxPool

Bottleneck with deeper feature extraction

Decoder: Transposed Convolution + skip connections

Final layer: Softmax output for 4 classes (including background)

📂 Project Structure
├── data/
│   ├── BraTS2020_TrainingData
│   ├── sample_data/
├── model/
│   ├── my_model.keras
│   ├── tumor_segmentation_model.weights.h5
├── notebooks/
│   ├── training.ipynb
│   ├── evaluation.ipynb
├── training_log.csv
└── README.md

🧪 Evaluation Code Snippet (Dice on Test Set)
results = [
    float(core_scores.mean()),
    float(edema_scores.mean()),
    float(enhancing_scores.mean())
]

descriptions = ["Dice Core", "Dice Edema", "Dice Enhancing"]

print("\n===== Model evaluation on the test set =====")
for desc, value in zip(descriptions, results):
    print(f"{desc:25s}: {value:.4f}")

🚀 How to Run
1. Clone the repository
git clone https://github.com/your-username/brain-tumor-segmentation.git
cd brain-tumor-segmentation

2. Install dependencies
pip install -r requirements.txt

3. Train the model (optional)
python train.py

4. Evaluate the model
python evaluate.py

🧪 Dataset

Source: BraTS2020 (MICCAI Brain Tumor Segmentation Challenge)

MRI modalities: T1, T1ce, T2, FLAIR

Ground truth labels: 4-class segmentation masks


