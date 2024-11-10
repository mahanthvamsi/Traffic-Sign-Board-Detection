# Traffic-Sign-Recognition-Using-YOLO

This repository contains model and training notebook for traffic sign recognition

## Dataset
The dataset used for training is [German Traffic Sign Recognition Benchmark (GTSRB)](https://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset) containing 43 classes of traffic signs. The training set contains 39209 labeled images and the test set contains 12630 unlabelled images.

![image](https://user-images.githubusercontent.com/35000278/116809754-50276780-ab5d-11eb-87fa-1f513be1f876.png)

## Model

Using and YOLOv5 for training and achieved >93% mAP on the dataset.

![image](https://user-images.githubusercontent.com/35000278/116809984-cd071100-ab5e-11eb-8789-29afd40c0094.png)

## Report

Used [WandB](https://wandb.ai/mdhamani/YOLOv5) to log hyperparameters and output metrics from runs. 

## TO RUN THE PROJECT

1. **Clone the Repository :**
    git clone https://github.com/mahanthvamsi/Traffic-Sign-Board-Detection.git
   
2. **Download the Model**
Download the [model](https://mega.nz/file/rV4HDQ5b#UfgDAMlVHvfzSr7PquE8HWx_6jhRmDUGBS-qyfIn_oE) and place it in the Traffic-Sign-Board-Detection folder.

3. **Download YOLOv5 :**
Clone the YOLOv5 repository:
git clone https://github.com/ultralytics/yolov5.git
Move the yolov5 folder into Traffic-Sign-Board-Detection.

4. **Replace detect.py :**
Replace the detect.py file in the yolov5 folder with your custom detect.py file from this repository.

5. **Run the Project :**
Navigate to the yolov5 folder and run the detection:
cd yolov5
python detect.py --weights ../best93.pt --source 0
