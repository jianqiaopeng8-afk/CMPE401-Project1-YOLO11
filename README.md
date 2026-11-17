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
<h2 align="center"><strong>3. Useage </strong></h2>

This project was developed and executed using Google Colab with GPU acceleration and the Ultralytics YOLO11 framework.

To reproduce the experiments, download the project files from the Google Drive link below and open the provided Jupyter Notebook (.ipynb) in Google Colab.

Install the required dependencies using `pip install ultralytics`, mount Google Drive, and configure the dataset path in `visdrone.yaml`.

Run the notebook cells in order to prepare the dataset, train the baseline YOLO11n model at 640 × 640 resolution, and conduct the controlled experiment at 960 × 960 resolution. Both models were trained for 50 epochs with a batch size of 8 and a random seed of 42.

The training results, loss curves, and trained model weights are saved in the project folders. The fine-tuned model weights can be used for further evaluation without retraining.

[Access Project Files and Trained Models](https://drive.google.com/drive/folders/1aAr7dT9nYkOKcM4v2ceVUxIML5VaRscT?usp=drive_link)

For users who only want to view the experimental results without downloading the complete project, the results can be accessed directly through the result-source branch of the GitHub repository.

[View Experimental Results (result-source branch)](https://github.com/jianqiaopeng8-afk/CMPE401-Project1-YOLO11/tree/result-source)


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

The baseline YOLO11n model showed stable convergence over 50 epochs. The training loss decreased from approximately 4.8 to 3.34, while the validation loss decreased from 4.12 to 3.41. Both curves gradually flattened, indicating that the model was approaching convergence.

No significant overfitting was observed because the validation loss continued to decrease without a sustained upward trend. However, the relatively low mAP of 0.1733, Precision of 0.4420, and Recall of 0.3222 suggest that the model's detection capability remains limited, although the loss curves alone do not confirm severe underfitting.

This may be related to the complexity of the VisDrone dataset, which contains 7,019 images, including 6,471 training images and 548 validation images. The dataset contains many small and densely distributed objects, making detection more challenging. Additionally, YOLO11n is a lightweight model with limited capacity, which may restrict its ability to learn complex visual features.

Overall, the baseline model demonstrated stable convergence without obvious overfitting, but its detection performance indicates that further improvements are needed.

<h2 align="center">6. Structured Experimental Design</h2>

A controlled experiment was conducted to investigate the effect of input image resolution on YOLO11n object detection performance using the VisDrone2019-DET dataset.

The baseline model was trained at an image resolution of 640 × 640, while the experimental model used 960 × 960. Both models used the same YOLO11n architecture, pretrained weights, dataset, 50 training epochs, batch size of 8, and random seed of 42. Input image resolution was the primary variable changed in this experiment.

The purpose of increasing the image resolution was to preserve more visual details of small objects in aerial images, potentially improving detection performance.

At Epoch 50, the baseline model achieved a Precision of 0.4420, Recall of 0.3222, and mAP50-95 of 0.1733. The experimental model achieved a Precision of 0.5187, Recall of 0.4025, and mAP50-95 of 0.2406.

Compared with the baseline, Precision increased by approximately 0.0768, Recall increased by 0.0803, and mAP50-95 increased by 0.0673. The relative improvement in mAP50-95 was approximately 38.8%.

These results suggest that increasing the input image resolution from 640 × 640 to 960 × 960 improved detection performance on the VisDrone dataset. The higher resolution may help the model preserve more information about small objects, although it also requires greater computational resources.

Overall, the controlled experiment demonstrates that input image resolution is an important factor affecting YOLO11n detection performance, particularly for aerial images containing small and densely distributed objects.
