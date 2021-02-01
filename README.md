# crea_augmented_fcns
This project proposes the efficient attention augmented convolution module which comprises convolution, efficient attention and column-row attention operations. We replace some convolutional layers with this augmented module in fully convolutional networks to obtain the augmented convolutional networks, and test them on semantic segmentation task.

# Prepare Dataset
The dataset this project uses is Augmented PASCAL VOC, which is made of PASCAL VOC 2012 and Semantic Boundaries Dataset. 

## Make the dataset by yourself
If you want to make the augmented dataset by yourself, you can make it following the guidance below.

You can download the PASCAL VOC 2012 from this url:
http://host.robots.ox.ac.uk/pascal/VOC/voc2012/VOCtrainval_11-May-2012.tar

You can download the Semantic Boundaries Dataset from this url:
http://www.eecs.berkeley.edu/Research/Projects/CS/vision/grouping/semantic_contours/benchmark.tgz

The directory structures of these two datasets are as below:

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

Use mat2png.py to transform the annotation datas in Semantic Boundaries Dataset. Entry the directory /tools and run mat2png.py. The transformed annotations is in the directory /cls_aug.
```
python mat2png.py cls cls_aug
```
Use convert_labels.py to transform the annotation datas in PASCAL VOC 2012. Copy convert_labels.py and utils.py to the directory /VOCdevkit/VOC2012, and run convert_labels.py.  The transformed annotations is in the directory /cls_aug.
```
python convert_labels.py SegmentationClass ImageSets/Segmentation/trainval.txt SegmentationClass_1D
```
Finally, we combine the images and annotations in both datasets to make Augmented PASCAL VOC. And put the indexed files train_aug.txt and val.txt into the directory /ImageSets/Segmentation of this augmented dataset. The directory structure of Augmented PASCAL VOC is as below:
```
+ VOC2012    
    + ImageSets
      +Segmentation
        train_aug.txt
        val.txt
    + JPEGImages
    + SegmentationClass    
```
