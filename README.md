# 🩻 Chest X-ray Nodule Detection with YOLOv8

> Detecting pulmonary nodules from chest X-ray images using a fine-tuned YOLOv8 model  
> Built for medical imaging evaluation, prototyping, and freelance delivery

[🚀 Live Demo on Hugging Face](https://huggingface.co/spaces/baptiste-lf-data/x-ray_Nodule_Detection)

---

## 🧠 Project Overview

This project demonstrates a real-world deployment of an object detection model for **pulmonary nodule detection** on chest X-rays.

The model is fine-tuned on a custom X-ray dataset and deployed with an interactive Gradio interface, allowing anyone to test the system, see predictions vs ground truth, and evaluate detection accuracy.

This is part of a professional portfolio to demonstrate:

- Real medical imaging use case handling
- Model training & evaluation
- Deployment (Gradio + HF Spaces)
- Software engineering: reproducibility, versioning, packaging, inference APIs

---

## 🎯 Goal

- Detect suspicious nodules in chest X-ray scans
- Help clinicians quickly verify if an image requires further analysis
- Serve as a starting point for radiology AI solutions

---

## 🛠️ Tech Stack

| Area              | Stack                        |
|-------------------|------------------------------|
| Model             | [Ultralytics YOLOv8](https://docs.ultralytics.com/) |
| Programming       | Python, PIL                  |
| Training          | YOLOv8 + custom dataset      |
| Evaluation        | mAP@50, mAP@50-95, recall    |
| Deployment        | [Gradio](https://gradio.app/) + Hugging Face Spaces |
| Optimization      | Label parsing, bounding box overlay |
| Versioning        | Git + Git LFS                |

---

## 📊 Model Details

- Model: `YOLOv8x` fine-tuned on a labeled X-ray dataset
- Classes: `nodule`
- Training: Custom Roboflow-format dataset with validation & test splits
- Evaluation: `mAP50`, `mAP50-95`, precision, recall

> 📈 Achieved strong performance on validation set — model performance monitored using Weights & Biases

---

## 🖼️ Features

- 🖼️ Upload your own X-ray or use predefined examples
- 🔴 Predictions shown in **red**
- ✅ Ground truth (if available) shown in **green**
- 📊 JSON output via FastAPI version (optional)

---

## 🚀 Try it Live

You can try the deployed app [here](https://huggingface.co/spaces/baptiste-lf-data/x-ray_Nodule_Detection).

Simply:
1. Upload a chest X-ray image
2. See model predictions
3. Compare with ground truth annotations

---

## 🧪 Local Setup

```bash
git clone https://huggingface.co/spaces/baptiste-lf-data/x-ray_Nodule_Detection
cd x-ray_Nodule_Detection

# Create virtual environment (optional)
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Install dependencies
pip install -r requirements.txt

# Run Gradio app
python app.py
