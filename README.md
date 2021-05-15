# Object Detection with Yolov5

First install the requirements in new environment:

pip install -r yolov5/requirements.txt


The dataset must contain the images and annotations in yolo format


## The Data Config file:
Create new .yaml file inside src/data following the example:

```
train: ../data/images/train/ 
val:  ../data/images/val/
test: ../data/images/test/

# number of classes
nc: 1

# class names
names: ["head"]
```

The realted yolov5(network size).yaml needs to be adapted to the number os classes or any other chance in the architecture. The file is in the src/models.

To train:
```bash
python train.py --img 640 --cfg yolov5s.yaml --hyp hyp.scratch.yaml --batch 16 --epochs 100 --data wheat_train.yaml --weights yolov5s.pt --workers 4 --name wheat_custom --device 0
```

For inference: ( Check the save_txt flag on inference )
```bash
python detect.py --source ../data/images/test/ --weights runs/train/wheat_custom/weights/best.pt --conf 0.50 --save-txt --save-conf --name wheat_custom
```

For metrics on test set:
```bash
python test.py --weights runs/train/wheat_custom/weights/best.pt --data wheat_train.yaml --task test --name wheat_custom
```




