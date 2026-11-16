# CMPE401-Project1-YOLO11
<h2 align="center"><strong>1. Introduction</strong></h2>

Object detection is an important application of deep learning and computer vision, widely used in autonomous driving, intelligent transportation, robotics, and surveillance systems.

This project investigates the performance of YOLO11 on the VisDrone2019-DET dataset, which contains aerial images with small objects, dense scenes, and complex backgrounds.

The project focuses on training a baseline model, analyzing training behavior, conducting controlled experiments, and evaluating whether changes in image resolution improve object detection performance.

<h2 align="center"><strong>2. Model and data </strong></h2>
This project uses YOLO11n, a lightweight object detection model developed by Ultralytics. It provides efficient object detection with relatively low computational requirements.

The model was initialized with pretrained weights (yolo11n.pt) and fine-tuned on the VisDrone dataset.

Two configurations were tested:

Baseline: Image size 640 × 640.

Experiment: Image size 960 × 960.

Both models were trained for 50 epochs with a batch size of 8.
This project uses the VisDrone2019-DET dataset recommended by the course instructor. The dataset contains aerial images of pedestrians, vehicles, and other objects captured by drones.

It presents challenges such as small objects, crowded scenes, and complex backgrounds.

The dataset contains 10 object categories and was prepared for YOLO11 training by converting the original annotations into YOLO format.


Training 6,471

Validation 548

Total 7,019
<h2 align="center"><strong>3. useage </strong></h2>
<h2 align="center"><strong>4. Baseline Model </strong></h2>

The baseline model uses YOLO11n with pretrained weights (`yolo11n.pt`) and is fine-tuned on the VisDrone2019-DET dataset.

The model was trained using an input image resolution of 640 × 640 with 50 epochs, a batch size of 8, and a random seed of 42. Training was performed on Google Colab using GPU acceleration.

The purpose of the baseline model is to establish a reference for evaluating subsequent model improvements.

At Epoch 50, the baseline model achieved an mAP of 0.1733 (17.33%), a Precision of 0.4420 (44.20%), and a Recall of 0.3222 (32.22%).

These results provide a reference for evaluating whether increasing the input image resolution improves object detection performance.
<p align="center">
  <img src="401%20project%201%20baseline.png" width="750">
</p>

<p align="center">
  <strong>Figure 1. Baseline Model Training Results</strong>
</p>
<h2 align="center">5. Loss Curve and Fitting Analysis</h2>

The training and validation loss curves of the baseline YOLO11n model were analyzed over 50 epochs.

Convergence Analysis: Both training and validation losses decreased steadily. Training loss decreased from approximately 4.8 to 3.34, while validation loss decreased from approximately 4.12 to 3.41. The curves gradually flattened, indicating that the model was approaching convergence.

Overfitting Analysis: No significant overfitting was observed because the validation loss continued to decrease rather than increase. Although training loss became slightly lower than validation loss near the end, the difference remained small.

Underfitting Analysis: The relatively low detection performance (mAP = 0.1733, Precision = 0.4420, Recall = 0.3222) suggests that the model may still have limited detection capability. However, the loss curves alone do not establish severe underfitting.

Possible Causes: The dataset contains 7,019 images, including many small and densely distributed objects. Additionally, YOLO11n has a lightweight architecture with limited model capacity, which may restrict its ability to learn complex visual features.

Overall, the baseline model demonstrated stable convergence without clear evidence of severe overfitting, but its detection performance indicates room for improvement.
