# 🩻 Chest X-ray Nodule Detection with YOLOv8

This project applies a fine-tuned YOLOv8 model to detect lung nodules on chest X-ray images. It includes:

- ✅ Full model training and evaluation on medical X-ray data  
- ✅ Live visual demo with Gradio on Hugging Face Spaces  
- ✅ Optional FastAPI backend (code only, not deployed)  
- ✅ Evaluation analysis with identified test set issues  
- ✅ Clear explanations of model limitations and improvements

👉 **[Live Demo on Hugging Face Spaces](https://huggingface.co/spaces/baptiste-lf-data/x-ray_Nodule_Detection)**

---

## 🎯 Project Goals

- Train a YOLOv8 model on a medical object detection task
- Enable real-time predictions through an interactive app
- Include code for production-ready inference with FastAPI
- Analyze generalization and failure points on test data

---

## 🧠 Model Summary

- **Model**: YOLOv8x (fine-tuned)
- **Dataset**: Annotated lung nodule X-rays
- **Framework**: Ultralytics YOLOv8 + PyTorch
- **Metrics** (train/val):

  ```
  mAP@0.5 ≈ 0.95
  Precision ≈ 0.96
  Recall    ≈ 0.91
  ```

---

## ⚠️ Generalization Issue on Test Set

Despite strong results on the training and validation sets, the model performs poorly on the test set. As shown at the end of `02_eval.ipynb`, predictions on test images are inaccurate and inconsistent.

### 🔍 Why?

- **Domain shift**: the test set may come from different machines or labeling styles
- **Overfitting**: YOLOv8 fits the training and validation data well but fails to generalize
- **Dataset size**: limited and not diverse enough

---

## 🔧 How to Improve

1. **Increase data diversity**  
   Use more varied X-ray sources across institutions.

2. **Use stronger data augmentation**  
   Mosaic, blur, color jitter, noise, and horizontal flipping.

3. **Cross-validation**  
   Improve robustness and reduce overfitting.

4. **Improve label consistency**  
   Standardize class definitions and check annotations.

5. **Model ensembling**  
   Combine multiple fine-tuned YOLO models.

---

## 🚀 Gradio Demo (Deployed)

Run locally:

```bash
pip install -r requirements.txt
python app.py
```

Or try the live app:

📍 **[Gradio Space](https://huggingface.co/spaces/baptiste-lf-data/x-ray_Nodule_Detection)**

- Upload your chest X-ray image
- Get predictions with red bounding boxes
- Example images included
- Ground truth only visible in dev version

---

## 🛠️ FastAPI API (Code Only)

FastAPI backend code is available in `notebooks/03_fastapi_api.ipynb`. It includes:

- `/predict` endpoint (accepts image, returns JSON)
- Runs `YOLOv8` inference under the hood
- Built for production deployment

Run it locally:

```bash
uvicorn main:app --reload
```

📌 *This backend is not deployed to Hugging Face Spaces to avoid redundancy.*

---

## 📁 Project Structure

```
xray-yolov8/
├── app.py                 # Gradio app
├── best.pt                # Trained model
├── main.py                # FastAPI backend (optional)
├── requirements.txt       # For both interfaces
├── examples/              # Sample X-ray images and labels
├── notebooks/
│   ├── 01_model_comparison_yolo_and_wandb
│   ├── 02_yolov8x_fine_tuning  
│   └── 03_model_nodule_deployment
```

---

## ✅ What This Project Shows

- Medical object detection with YOLOv8
- Model fine-tuning on limited annotated data
- Full pipeline from training → visualization → deployment
- Integration of Gradio (UI) and FastAPI (API backend)
- Analysis of overfitting and test set failure
- Clear next steps for improvement

---

## 🙋‍♂️ Author

**Baptiste Le Flem**  
Freelance Machine Learning Engineer
