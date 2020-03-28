# detectron2_example_PCBdata
Using detectron2 to detect PCB data.
You can get to the demo by [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/a8252525/detectron2_example_PCBdata/blob/master/PCBdata_fasterRCNN_colab.ipynb)

## Troubleshooting
The most wired bug I faced is using evaluator and **get -1 in AP value**. I had checked prediction image which had well performance in many image. Got right prediction, but wrong AP value. In the help of my friend, I realize that original point is at top left while I set it in bottom left. I set wrong bounding box for sure. However, it could train anyway and predicted well. Review the dataset you create if you get -1 in AP value.
Moreover, **remember to delete the file used to evaluate**. I save it at path “./output” in the demo. We have to delete it since file can’t be overwrited. In my demo, the file used to evaluate is called PCB_test_coco_format.json.
[Other bug record](https://hackmd.io/r56cKd8mQXmkt9HjAec7Og?both)
