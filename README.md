# Signature Verification Using Siamese Neural Network

This project implements a signature verification system using a **Siamese Neural Network**. The model learns to verify whether two input signature images belong to the same person by comparing their feature embeddings. This can be used in applications such as fraud detection, access control, and document authentication.

---

## Features

- Siamese Neural Network architecture for one-shot learning.
- Custom dataset loader for genuine and forged signatures.
- Image preprocessing using OpenCV and TensorFlow.
- Streamlit-based user interface for uploading and comparing signatures.
- Deployable on AWS EC2 for live use.

---

## Tech Stack

- **Python**
- **TensorFlow / Keras**
- **OpenCV**
- **NumPy / Pandas**
- **Streamlit** – for frontend interface
- **AWS EC2** – for cloud deployment

---

## Project Structure

```
├── signverification.ipynb        # Main Jupyter notebook with model code
├── siamese_model.h5              # Trained model file (save after training)
├── app.py                        # Streamlit app for signature comparison
├── images/
│   ├── genuine/
│   └── forged/
├── utils.py                      # Preprocessing and utility functions
└── requirements.txt              # Dependencies
```

---

## Model Overview

- **Input**: Pair of signature images (Genuine or Forged)
- **Architecture**: Two identical CNN branches extract features → Combined with contrastive loss.
- **Output**: Binary classification — same or different person.


---

## Deployment on AWS EC2

### 1. Launch EC2 Instance

- Go to AWS Console → EC2 → Launch Instance
- Choose:
  - Ubuntu 20.04
  - t2.micro (Free Tier)
- Add security group rule:
  - **Custom TCP** → Port: `8501` or `8502` (or open to all TCP if testing)

### 2. SSH into the Instance

```bash
ssh -i "your-key.pem" ubuntu@your-ec2-ip
```

### 3. Install Required Packages

```bash
sudo apt update
sudo apt install python3-pip
pip3 install streamlit tensorflow opencv-python
```

### 4. Transfer Project Files

From your local terminal:

```bash
scp -i "your-key.pem" -r ./Signature-Verification-SiameseNN ubuntu@your-ec2-ip:~
```

### 5. Run the Streamlit App on EC2

```bash
cd Signature-Verification-SiameseNN
streamlit run app.py --server.port 8501 --server.enableCORS false --server.enableXsrfProtection false
```


---



