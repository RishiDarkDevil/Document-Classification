# Scanned Document Classification

We take lots of scanned images of documents of various type some taken on handheld devices, some using scanners, etc. So, it becomes increasingly important to organize these scanned documents, which requires reliable and high quality classification of these scanned document images into several categories like letter, form, etc.

This is a part of [IndoML22(Indian Symposium of Machine Learning-2022)](https://indoml.in/) [Datathon](https://sites.google.com/view/datathonindoml/home) Challenge.

## Data

The training and validation data is provided in the Datathon which is a subset of 16000 grayscale images from the [RVL-CDIP dataset](https://adamharley.com/rvl-cdip/) with 1000 images belonging to each of the 16 categories in which the images are classified. The competition and the data is released in its [Kaggle Competition](https://www.kaggle.com/competitions/datathonindoml-2022).

Images span across 16 different categories(with their corresponding labels) from the training set as shown below:

Letter(0)|Form(1)|Email(2)|Handwritten(3)
--|--|--|--
![letter](Samples/train/letter.png)|![form](Samples/train/form.png)|![email](Samples/train/email.png)|![handwritten](Samples/train/handwritten.png)
Advertisement(4)|Scientific Report(5)|Scientific Publication(6)|Specification(7)
![advertisement](Samples/train/advertisement.png)|![report](Samples/train/report.png)|![publication](Samples/train/publication.png)|![specification](Samples/train/specification.png)
File Folder(8)|News Article(9)|Budget(10)|Invoice(11)
![filefolder](Samples/train/filefolder.png)|![newsarticle](Samples/train/newsarticle.png)|![budget](Samples/train/budget.png)|![invoice](Samples/train/invoice.png)
Presentation(12)|Questionnaire(13)|Resume(14)|Memo(15)
![presentation](Samples/train/presentation.png)|![questionnaire](Samples/train/questionnaire.png)|![resume](Samples/train/resume.png)|![memo](Samples/train/memo.png)

A discussion about the data with few more images from both training and validation set displayed can be seen in the [data overview notebook](Data-Overview.ipynb)

## Task

The task is to build a model to classify the images correctly into it's respective category and the performance will be evaluated using the Mean F1-Score. The F1 score, commonly used in information retrieval, measures accuracy using the statistics precision $(\text{p})$ and recall $(\text{r})$.

Precision is the ratio of true positives $(\text{tp})$ to all predicted positives $(\text{tp} + \text{fp})$. Recall is the ratio of true positives $(\text{tp})$ to all actual positives $(\text{tp} + \text{fn})$. The F1 score is given by:

$$ \text{F1} = 2\frac{\text{p} \cdot \text{r}}{\text{p}+\text{r}}\ \ \mathrm{where}\ \ \text{p} = \frac{\text{tp}}{\text{tp}+\text{fp}},\ \ \text{r} = \frac{\text{tp}}{\text{tp}+\text{fn}} $$

The F1 metric weights recall and precision equally, and a good retrieval algorithm will maximize both precision and recall simultaneously. Thus, moderately good performance on both will be favored over extremely good performance on one and poor performance on the other.

## Method

Various visual feature extraction based methods were applied using EfficientNetV2L pretrained model(trained on ImageNet). Two of them are:
- EfficientNet followed by FFN (EffNet)
- Partioned Image based EfficientNet followed by FFN (EffNet-4Piece)
- InceptionResNetV2 along with RoI based Vision Transformer Network (IncResNet-RoI-ViT) [[Model Report](Report/Datathon-22-Report.pdf)]
- ResNet-VGG-InceptionResNetV2 along with PCA followed by FFN (ResVGGInc-PCA-4Piece) [[Model Report](Report/Datathon-22-Report.pdf)]

The results of clustering of the learnt penultimate layer feature vector for the above two models for the training set is shown below:

EffNet (Mean-F1: 0.6)|EffNet-4Piece (Mean-F1: 0.68)
--|--
![EffNet](Visualizations/EffNet.png)|![EffNet-4Piece](Visualizations/EffNet-4Piece.png)

IncResNet-RoI-ViT (Mean-F1: 0.755)|ResVGGInc-PCA-4Piece (Mean-F1: 0.785)
--|--
![IncResNet-RoI-ViT](Visualizations/IncResNet-kPiece-ViT.png)|![ResVGGInc-PCA-4Piece](Visualizations/ResVGGInc-PCA-4Piece.png)

Further Work is ongoing to utilize the multi-modal information present in the document images.
