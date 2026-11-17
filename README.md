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
  <img src="https://github.com/jianqiaopeng8-afk/CMPE401-Project1-YOLO11/blob/result-pictures/401%20project%201%20baseline.png?raw=true" width="750">
</p>

<p align="center">
  Figure 1. Baseline Model Training Results
</p>

<h2 align="center">5. Loss Curve and Fitting Analysis</h2>

The baseline YOLO11n model showed stable convergence over 50 epochs, with training loss decreasing from approximately 4.8 to 3.34 and validation loss decreasing from 4.12 to 3.41. Both curves gradually flattened, indicating that the model was approaching convergence. No significant overfitting was observed because validation loss continued to decrease without a sustained upward trend. However, the relatively low mAP of 0.1733, Precision of 0.4420, and Recall of 0.3222 suggest that the model's detection capability remains limited, although the loss curves alone do not confirm severe underfitting. This may be related to the complexity of the VisDrone dataset, which contains 7,019 images with many small and densely distributed objects, as well as the limited model capacity of the lightweight YOLO11n architecture. Overall, the baseline model converged steadily without obvious overfitting, but further improvement is needed to achieve better detection performance.
