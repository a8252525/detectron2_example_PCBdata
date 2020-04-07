# detectron2_example_PCBdata
Using detectron2 to detect PCB data.
You can get to the demo by [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/a8252525/detectron2_example_PCBdata/blob/master/PCBdata_fasterRCNN_colab.ipynb)

## Environment
```
Linux or macOS
Python ≥ 3.6
PyTorch ≥ 1.3
torchvision that matches the PyTorch installation. You can install them together at pytorch.org to make sure of this.
OpenCV, optional, needed by demo and visualization
pycocotools: pip install cython; pip install ‘git+https://github.com/cocodataset/cocoapi.git#subdirectory=PythonAPI'
gcc & g++ ≥ 4.9
```
Check the environment and then
```
git clone https://github.com/facebookresearch/detectron2.git
cd detectron2 && pip install -e .
```
You can also get PCB data I use in here. Following the format of dataset, we can easily use it. It is a dict with path of the data, width, height, information of bounding box. You will need to add segmentation if you are using mask-rcnn. Here is my example:
```
{‘file_name’: ‘../DeepPCB/PCBData/group20085/20085/20085000_test.jpg’,
‘image_id’: 0,
‘height’: 640,
‘width’: 640,
‘annotations’: [
{‘bbox’: [409.0, 394.0, 435.0, 422.0], ‘bbox_mode’: <BoxMode.XYXY_ABS: 0>, ‘category_id’: 2, ‘iscrowd’: 0},
 {‘bbox’: [275.0, 383.0, 319.0, 417.0], ‘bbox_mode’: <BoxMode.XYXY_ABS: 0>, ‘category_id’: 2, ‘iscrowd’: 0},
 {‘bbox’: [8.0, 163.0, 36.0, 191.0], ‘bbox_mode’: 
<BoxMode.XYXY_ABS: 0>, ‘category_id’: 3, ‘iscrowd’: 0}, 
{‘bbox’: [244.0, 151.0, 270.0, 182.0], ‘bbox_mode’: <BoxMode.XYXY_ABS: 0>, ‘category_id’: 4, ‘iscrowd’: 0},
 {‘bbox’: [338.0, 519.0, 364.0, 543.0], ‘bbox_mode’: <BoxMode.XYXY_ABS: 0>, ‘category_id’: 5, ‘iscrowd’: 0},
 {‘bbox’: [476.0, 460.0, 502.0, 481.0], ‘bbox_mode’: <BoxMode.XYXY_ABS: 0>, ‘category_id’: 3, ‘iscrowd’: 0}
]}
```
## Troubleshooting
The most wired bug I faced is using evaluator and **get -1 in AP value**. I had checked prediction image which had well performance in many image. Got right prediction, but wrong AP value. In the help of my friend, I realize that original point is at top left while I set it in bottom left. I set wrong bounding box for sure. However, it could train anyway and predicted well. Review the dataset you create if you get -1 in AP value.
Moreover, **remember to delete the file used to evaluate**. I save it at path “./output” in the demo. We have to delete it since file can’t be overwrited. In my demo, the file used to evaluate is called PCB_test_coco_format.json.
[Other bug record](https://hackmd.io/r56cKd8mQXmkt9HjAec7Og?both)
