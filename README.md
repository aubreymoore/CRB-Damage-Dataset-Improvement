# CRB-Damage-Dataset-Improvement

This repo contains Jupyter notebooks used to improve a dataset of annotated images used for training
YOLOv8 models which detect damage to coconut palms caused by coconut rhinoceros beetle (CRB).  

# Installation
Clone the repo
```
git clone https://github.com/aubreymoore/CRB-Damage-Dataset-Improvement
```
Move to the new folder
```
cd CRB-Damage-Dataset-Improvement
```
Create a virtual environment
```
python3 -m venv .venv
```
Activate the new virtual environment
```
source .venv/bin/activate
```
Install required python modules
```
pip install -r code/requirements.txt
```
Create a .gitignore file and add .venv to the list of files and folders to be ignored.
Adding a virtual environmant to a repository is bad practice.
```
echo \".venv\" >> .gitignore
```
# Technical Notes

## Data storage
* Datasets in YOLOv5 format are stored in /home/aubrey/crb_damage_detector_data (ROOT)
* Each dataset, in YOLOv5 format, is stored in {ROOT}/datasets in a folder named using a timestamp indicating when the dataset was created. (Example: {ROOT}/datasets/20241128_1648)
* Each trained model is stored in {ROOT}/runs in a folder named using a timestamp indicating when the model training was started. (Example:{ROOT}/runs/20241128_1657)

## Retraining after dataset improvement
Instead of training from scratch, using weights from ```yolo11n.pt``` for example, it is preferable to retrain from the latest state of the custom model.
According to [this post](https://github.com/ultralytics/yolov5/issues/12883), retraining a custom model after dataset improvement can be done using:
```
python train.py --data path_to/my_yaml.yaml --weights myTrainedModel.pt --img 640
```
where ```data``` is the path to the most recent version of the improved dataset and ```weights``` is the path to  weights from the most recent training run for the custom model.

Let's try using this code within a Jupyter notebook:
```
from ultralytics import YOLO
import glob

model = YOLO(latest_weights_path)
results = model.train(
        data = latest_yaml_path,
        imgsz=1920,
        rect=True,
        epochs=1000,
        batch=-1,
        patience=20,
        name=updated_model_name
    )


```

