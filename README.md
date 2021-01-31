# crea_augmented_fcns
Semantic segmentation via efficient attention augmented convolutional networks.

# Prepare Dataset
The dataset this project uses is Augmented PASCAL VOC, which is made of PASCAL VOC 2012 and Semantic Boundaries Dataset. The directory structures of these two datasets are as below:

PASCAL VOC 2012
```
+ VOCdevkit
  + VOC2012
    + Annotations
    + ImageSets
    + JPEGImages
    + SegmentationClass
    + SegmentationObject 
```
Semantic Boundaries Dataset
```
+ benchmark_RELEASE
  + cls
  + img
  + inst  
  train.txt
  val.txt
```
The annotations in PASCAL VOC 2012 are colorful images of .png type while those in Semantic Boundaries Dataset are of .mat type. So we transform all the annotations into grayscale images before combining these two datasets. We first create a folder in benchmark_RELEASE and name it as tools, then put three python files into this folder which are mat2png.py, convert_labels.py and utils.py respectively.

Use mat2png.py to transform the annotation datas in Semantic Boundaries Dataset. Entry the directory /tools and run this python file:
```
python mat2png.py cls cls_aug
```
Use convert_labels.py to transform the annotation datas in PASCAL VOC 2012. Copy convert_labels.py and utils.py to the directory /VOCdevkit/VOC2012, and run convert_labels.py:
```
python convert_labels.py SegmentationClass ImageSets/Segmentation/trainval.txt SegmentationClass_1D
```

