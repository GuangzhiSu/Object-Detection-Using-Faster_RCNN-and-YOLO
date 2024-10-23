# Object Detection Using Faster R-CNN and YOLO

This repository contains code and datasets for comparing two popular object detection models: **YOLOv8** and **Faster R-CNN**. The goal of this project is to evaluate both models' performance on a custom dataset with four object categories: **laptop**, **mouse**, **keyboard**, and **utensils**. The models were trained, evaluated, and compared in terms of detection accuracy, inference speed, and model size.

---

## Dataset

- **Total Images**: 362
- **Classes**: 
  - Laptop
  - Mouse
  - Keyboard
  - Utensils
- **Annotation Tool**: [CVAT](https://cvat.org) for manual labeling.

The dataset was collected and annotated by three individuals, each responsible for labeling different categories. Special care was taken to ensure consistency between annotations for both YOLOv8 and Faster R-CNN. For YOLO, class identifiers were adjusted in the first column of each annotation file. In Faster R-CNN, the `category_id` field in the JSON files was updated to maintain consistent class labels.

---

## Models Used

### YOLOv8
YOLOv8 is a real-time, single-stage object detector known for its fast inference speed and computational efficiency. It treats object detection as a regression task by predicting bounding boxes and class labels simultaneously. 

**Key Features:**
- **Training:** 30 epochs with updates every 5 epochs to monitor progress.
- **Batch Size:** 8
- **Input Image Size:** 640 × 640 pixels.
- **Performance:** mAP@0.5: 0.858, mAP@0.5:0.95: 0.641.
- **Inference Speed:** ~3.5 ms per image (including preprocessing and postprocessing).
- **Model Size:** 5.26 MB.
- **Deployment:** Exported to ONNX format for cross-platform compatibility.

### Faster R-CNN
Faster R-CNN is a two-stage object detection model known for its high accuracy. It first generates region proposals and then refines them for classification and bounding box regression.

**Key Features:**
- **Configuration:** Faster R-CNN with a ResNet-50 backbone and Feature Pyramid Network (FPN).
- **Training:** 3000 iterations with a batch size of 2 and a learning rate of 0.001.
- **Gradient Clipping:** Enabled to stabilize training with a maximum value of 1.0.
- **Performance:** mAP@0.5: 0.709, mAP@0.5:0.95: 0.521.
- **Inference Speed:** ~60 ms per image (0.0604 seconds per iteration).
- **Model Size:** 314.85 MB.

---
