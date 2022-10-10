The Datathon-IndoML22-Submission folder contains the following files and folder:
- RoI-Extraction.ipynb
- inception-resnet50v2-4piece-feature-extraction.ipynb
- inceptionresnet50v2-roi-feature-extraction.ipynb
- Inception-ResNet-kPiece-ViT-Model.ipynb
- Data Folder
- README.txt (this file)

The Data folder should contain the IndoML22 dataset unzipped such that ./Data/train/train is the folder containing all training images 
and ./Data/validation/validation is the folder containing all validation images

The Data Folder contains two files:
- train_labels_1.csv
- test_labels_1.csv
- train_labels.csv

where the first two files in Data Folder is the part of the training set used for training containing 15200 images(train_labels_1.csv),
 and the rest 800 images in the test_labels_1.csv are used for evaluation

The notebooks are named above in the order they should be run.
- The RoI-Extraction.ipynb extracts RoIs from the documents both train and validation images.
- inception-resnet50v2-4piece-feature-extraction.ipynb generates the Feature Vector from InceptionResNetV2 for 4 + 1 pieces of the image.
- inceptionresnet50v2-roi-feature-extraction.ipynb generates the Feature Vector from InceptionResNetV2 for each RoI extracted from the image.
- Inception-ResNet-kPiece-ViT-Model.ipynb trains the RoI Vision Transformer Model.