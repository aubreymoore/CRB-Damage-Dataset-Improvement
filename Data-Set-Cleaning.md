# ANNOTATION RULES

1. No bounding boxes can touch the top, left or right edge of the image.
2. A **vcut** object must overlap a **live** object.

# PLAN

Train a subset of the data (GUAM07) on the original 3 class model trained on images were (1920x1080px). 

Looks like this is already done.

**Model:** /home/aubrey/Desktop/Guam07-training-set/datasets/3class-no-symlinks/runs/detect/train5/weights/best.pt October 10

Step 1 is to put the dataset in [YOLOv5 format](https://docs.voxel51.com/user_guide/dataset_creation/datasets.html#yolov5dataset-import). Used a [Jupyter notebook](/home/aubrey/datasets/dataset5/code/create_new_dataset.ipynb) to do this.

Step 2 is to read the new dataset into FiftyOne. [Jupyter Notebook](code/create_new_dataset.ipynb)

Then use FiftyOne to clean dataset as follows and retrain (using best.pt as starting point?)

# Data Set Cleaning

## Remove each image which is a duplicate or near-duplicate of the preceding images

Assuming images are sorted by time.

## Remove Ground Truth Bounding Boxes Touching Left, Right or Top Edges of Image

## Finding Detection Mistakes with FifyOne

[Finding Detection Mistakes with FifyOne](https://docs.voxel51.com/tutorials/detection_mistakes.html)