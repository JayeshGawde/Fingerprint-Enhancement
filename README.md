# 🧠 Biometric Palmprint & Fingerprint Segmentation using Image Processing + U-Net

This project presents a hybrid pipeline combining classical image processing with deep learning (U-Net) to segment **palmprints** and **fingerprints** from biometric images. The goal is to generate high-quality 3-class segmentation masks (background, palm, fingerprint) and train a robust segmentation model for real-world biometric applications.

---

## 🌍 Dataset Used

### 🗃️ Birjand University Biometric Dataset (BMPD)
This project is built using the publicly available **Birjand Mobile Palmprint Dataset (BMPD)** from **Birjand University**, Iran.

- The dataset includes grayscale palmprint and fingerprint images captured using mobile devices.
- Used for both training and evaluating palm/fingerprint segmentation.
- Each image was preprocessed and labeled using a custom Gabor + GrabCut pipeline.

## 📌 Project Highlights

- ✅ Generates masks using **CLAHE**, **Gabor filters**, and **GrabCut**
- 🧠 Trains a **U-Net model** for 3-class segmentation
- 📊 Evaluates performance using **IoU** and **Dice Score**
- 🧪 Simulates **image degradation** (blur + noise) for robustness testing

---

## 🖼️ Segmentation Classes

| Class        | Label | Description          |
|--------------|-------|----------------------|
| Background   | 0     | Non-biometric area   |
| Palm Region  | 1     | Palmprint portion    |
| Fingerprint  | 2     | Ridge-rich fingerprint zone |

---

## 🗂️ Project Structure

├── preprocessing/
│ ├── CLAHE + Gabor filter
│ ├── Palm segmentation (GrabCut)
│ └── Combined mask generator (3-class)
│
├── model/
│ ├── U-Net architecture with Dropout & BatchNorm
│ ├── Dice + Categorical Crossentropy Loss
│ └── Multi-dataset training support
│
├── evaluation/
│ ├── Loads trained model
│ ├── Predicts masks on test images
│ └── Computes IoU and Dice scores
│
├── data/
│ ├── /001, /002, /003, /004 - Training datasets
│ └── /005 - Testing dataset
│
└── degradation/
└── Applies blur + Gaussian noise to test image copies


---

## 🛠️ Key Technologies Used

- **Python**
- **OpenCV** (CLAHE, Gabor, GrabCut)
- **TensorFlow / Keras**
- **Matplotlib / NumPy**
- **Sklearn Metrics** (IoU, F1)

---

## 🏗️ How It Works

### 🔹 Preprocessing & Mask Generation

python
1. Read grayscale biometric image
2. Apply CLAHE for contrast enhancement
3. Apply Gabor filters to enhance fingerprint ridges
4. Use GrabCut to segment palm region
5. Combine results into a 3-class labeled mask
6. Save as *_gabor_mask.png
   
U Net Model Training
1. Load images and masks from multiple datasets (001–004)
2. Train a custom U-Net model
3. Use Dice + Categorical Crossentropy loss
4. Save best model based on validation loss

Evaluation
1. Load model and test images from dataset 005
2. Predict segmentation masks
3. Compare with ground truth masks
4. Compute IoU and Dice for each sample
5. Visualize results

🎯 Results
✅ Model trained on multiple datasets
✅ Quantitative metrics (IoU, Dice) computed
✅ Visual comparison of ground truth vs prediction
✅ Handles degraded images with good generalization

Mask
![image](https://github.com/user-attachments/assets/89d7b2c5-3a79-4b3a-903c-09f886da5e25)
Predictions
![image](https://github.com/user-attachments/assets/16332a90-7f86-4269-90c4-4c4670a78cd1)



📊 Sample Evaluation Output

📄 001_F_L_01.JPG — IoU: 0.8654, Dice: 0.9128
📄 001_F_L_02.JPG — IoU: 0.8471, Dice: 0.8997
...
✅ Mean IoU:  0.8543
✅ Mean Dice: 0.9032

📁 Datasets Used
001, 002, 003, 004: Training sets from the BMPD dataset
005: Testing dataset (also from BMPD)
Masks are auto-generated using Gabor + GrabCut pipeline

✍️ Authors & Contributors
Jayesh Gawde
GitHub: @JayeshGawde
Vansh Doshi
Github: @Vanshdoshi10
Jeet Jain



Project: BM_proj_A103, A104, A108
📫 Contact
Jayesh Gawde
GitHub: @JayeshGawde
Email:jayeshgawde2113@gmail.com
