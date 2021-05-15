# Object Detection with Yolov5

First install the requirements in new environment:

pip install -r yolov5/requirements.txt


The dataset must contain the images and annotations in yolo format


## The Data Config file:
Create new .yaml file inside src/data following the example:

```
train: ./data/images/train/ 
val:  ./data/images/val/
test: ./data/images/test/

# number of classes
nc: 1

# class names
names: ["head"]
```

The realted yolov5(network size).yaml needs to be adapted to the number os classes or any other chance in the architecture. The file is in the src/models.

To train:
```bash
python train.py --img 640 --cfg yolov5s.yaml --hyp hyp.scratch.yaml --batch 32 --epochs 100 --data road_sign_data.yaml --weights yolov5s.pt --workers 24 --name yolo_road_det
```






