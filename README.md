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
source venv/bin/activate
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
