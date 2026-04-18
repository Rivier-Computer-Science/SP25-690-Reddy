Deep Learning for Pneumonia Localization in Chest X-Ray
Problem Statement 
Pneumonia is a leading cause of mortality globally, requiring rapid and accurate interpretation of chest X-rays. While simple classification can identify the presence of infection, it lacks the spatial reasoning necessary for clinical decision-making.
Question: -
How does a dedicated Object Detection architecture (like YOLO) compared to a traditional CNN Classification model (ResNet-50) with Grad-CAM heatmaps in accurately localizing pulmonary opacities.
Proposed Methodology & Dataset
•	Dataset: The RSNA Pneumonia Detection Challenge dataset (30,000 images). I will utilize a stratified subset of 2,000 images for initial prototyping.
https://www.kaggle.com/competitions/rsna-pneumonia-detection-challenge/data
•	Preprocessing: DICOM conversion to JPEG with Histogram Equalization to standardize contrast.
•	Establishing a rigorous data split (70/15/15) with stratification and patient-de-identification to prevent data leakage.
•	Utilizing Residual Connections via a pre-trained ResNet-18 as a baseline and moving to an object detection framework.
•	Baseline Model: A ResNet-18 binary classifier trained on "Normal" vs. "Opacity." I will use Grad-CAM to generate saliency maps for comparison.
•	Proposed Model: YOLOv8 (You Only Look Once), a one-stage detector that maps images directly to bounding box coordinates and class probabilities.
•	Evaluating models using beyond-accuracy metrics IoU (Intersection over Union), and Recall
•	Ethics & Practice: Addressing the interpretability of "black-box" models by comparing explicit bounding boxes against attention-based heatmaps.
Evaluation Plan & Baselines
•	Controls: The ResNet-50 classifier acts as the control. I will measure if the specialized detection loss in YOLOv26 yields significantly better localization than the classification-derived heatmaps.
•	Metrics:
1.	Classification: Precision, Recall, and F1-Score.
2.	Localization: mean Average Precision (mAP) at various IoU thresholds (0.5 to 0.95).

