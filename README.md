# Srilanka_Vehicle_NumberPlate_detection_System# Sri Lanka Vehicle Number Plate Detection System

## Step 1: Dataset Preparation and Initial Model Training

### Overview
This project aims to develop an Automatic Number Plate Recognition (ANPR) system for detecting vehicle front number plates in Sri Lanka using YOLOv5. The first step involved preparing a custom dataset and training an initial model to establish a baseline for number plate detection.

### What We Did
1. **Dataset Collection and Annotation**:
   - Collected 482 images of vehicle front number plates from various sources (e.g., real-world captures, online images).
   - Uploaded the images to [Roboflow](https://roboflow.com/), a platform for dataset management and annotation.
   - Annotated all images with the "plate" class to mark number plate regions, generating bounding box labels in YOLO format (`.txt` files).
   - Split the dataset into:
     - **Train**: 337 images (70%)
     - **Validation**: 97 images (20%)
     - **Test**: 48 images (10%)
   - Exported the dataset as `anpr_482.zip` in YOLOv5 PyTorch format, including a `data.yaml` configuration file.

2. **Initial Model Training**:
   - Cloned the [YOLOv5 repository](https://github.com/ultralytics/yolov5) to set up the training environment.
   - Used the pre-trained `yolov5s.pt` (small variant) as the starting weights for transfer learning, suitable for moderate hardware (16GB RAM).
   - Trained the model with the following command:
     ```bash
     python train.py --img 640 --batch 16 --epochs 50 --data data.yaml --weights yolov5s.pt