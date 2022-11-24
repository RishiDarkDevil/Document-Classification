Welcome to the Datathon@IndoML22 Repository by RISHI DEY CHOWDHURY!
It contains the notebooks, folders and files associated with the Datathon submission. 
Please go through this entire README.txt file carefully. 
(IF NOT INTERESTED IN RUNNING LOCALLY, COLAB LINKS ARE PROVIDED IN THE END REFER TO THAT)

SYSTEM INFO:

- CPU: M1 Max 32 Core GPU
- RAM: 32 GB
- OS: macOS Monterey Version 12.5.1

PREREQUISITES:

- Anaconda should be installed, preferably: conda 22.9.0

SETUP:

- Start terminal/shell/command prompt with current working directory as this folder.
- To prevent conflicts, create conda environment with `conda create --prefix ./env python=3.8`
- Activate the environment with `conda activate ./env`
- Install necessary packages with the following commands:

	- `pip install jupyter numpy pandas matplotlib scikit-learn opencv-python torch torchvision`
	- `pip install detectron2 @ git+https://github.com/facebookresearch/detectron2.git@4aca4bdaa9ad48b8e91d7520e0d0815bb8ca0fb1`
	- `pip install "layoutparser[ocr]"`
	- `conda install conda install -c apple tensorflow-deps`
	- `pip install tensorflow-macos`
	- `pip install tensorflow-metal`

- Now, your system is ready to run the notebooks.

NOTEBOOKS:

- train.ipynb: contains the code for training the model.
- test.ipynb: contains the code for inferencing the model.

FILES:

- requirements.txt: `pip freeze` output of my environment.
- README.txt: This file.

FOLDERS:

- Data: A sample folder structure you may follow with 3 subfolders:
	- labels: contains the labels for the images in the train folder.
	- train: contains the training images.
	- test: contains the testing images, no labels are present for these.
- Model: A sample folder that might be used to contain the model that is trained locally.
- Pretrained-Model: A folder that contains the pretrained model, which is submitted in the Datathon.

Note: 
- Data folder's subfolders contain some sample examples.
- Model folder contains sample examples.
- But Pretrained-Model folder contains the model that I trained for Datathon submission. Can be used directly for inference in test.ipynb

RUN NOTEBOOKS:

- In each notebooks, there are two sections titled 'SET THE PATHS' and 'SET FEW MORE PARAMETERS'.
- Read the instructions under these sections of how to set the paths to various directories.
- Make sure all the imports in the first cell runs without issues.
- Apart from that nothing more to change, run the entire notebook.

IMPORT ERROR or INSTALLATION ERROR:

- If you are not on Mac (Apple Silicon) the last 3 package installation under SETUP might not work. Please install the relevant tensorflow package that is suitable for your machine (GPU versions are preferred).
- layoutparser is available only for Linux and Mac. Not available on Windows Machine.

STILL FACING ISSUES?

- I have Colab Versions of the notebooks here which runs without any errors. Please do follow the instructions near the start of these colab notebooks before running all the cells.
- Colab train.ipynb: https://colab.research.google.com/drive/1NcL5gk40tlCUqLowMPm2h9SYcXMmZPx2?usp=sharing
- Colab test.ipynb: https://drive.google.com/file/d/1idxw4kMOELhIM5BzHnOxWSAdqgijtVwJ/view?usp=sharing
