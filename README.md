# hm2
## Introduction
本项目使用YOLOV5实现自动驾驶目标检测以及目标分类功能。
## YOLOV5
项目使用预训练通用目标检测模型YOLOV5，可通过如下方式安装
```bash
git clone https://github.com/ultralytics/yolov5.git
```

## Prerequisites
####
1.Libraries (Python3.83-based)
```bash
pip3 install -r requirements.txt
pip3 install ultralytics
```
2.Dataset: https://pan.baidu.com/s/1T7wbUGKKMZMG5UiOqH2UrQ   psw：vtj3

包含训练集2390张图片，验证集600张图片，图像分辨率为1024*1024。共21个类别。

创建 traffic_vehicle.yaml,其内容如下：
```bash
path: ../datasets/traffic_vehicle 	# dataset root dir
train: images/train 				# train images (relative to 'path')
val: images/train					# val images (relative to 'path')
test: # test images (optional)

# Classes
names: 
  0: ambulance
  1: auto rickshaw
  2: bicycle
  3: bus
  4: car
  5: garbagevan
  6: human hauler
  7: minibus
  8: minivan
  9: motorbike
  10: Pickup
  11: army vehicle
  12: policecar
  13: rickshaw
  14: scooter
  15: suv
  16: taxi
  17: three wheelers (CNG)
  18: truck
  19: van
  20: wheelbarrow
```

## Getting Start
### Training
```bash
python3 ./train.py --data YOU/PATH/traffic_vehicle.yaml --cfg YOU/PATH/yolov5s_traffic_vehicle.yaml --weights YOU/PATH/yolov5s.pt --batch-size 32 --epochs 50 --name YOU NAME --project yolo_traffic_vehicle
```
### Testing
修改下面地址，以及图片名，选择其中一张图片，查看效果。
```bash
python3 detect.py --source YOU/PATH/images/val/PICNAME.JPG --weights YOU/PATH/weights/best.pt --conf-thres 0.4
```
![image](https://github.com/user-attachments/assets/a259dbba-8a6b-4320-9863-eae2d477b311)

```bash
python3 val.py --data  ./data/traffic_vehicle.yaml  --weights ./yolo_traffic_vehicle/epochs300_1/weights/best.pt --batch-size 32
```
```
YOLOv5s summary: 157 layers, 7066762 parameters, 0 gradients, 15.9 GFLOPs
val: Scanning /tmp/pycharm_project_841/datasets/labels/val.cache... 600 images, 
                 Class     Images  Instances          P          R      mAP50   
                   all        600       5090      0.728      0.408      0.438      0.291
             ambulance        600         22          1          0     0.0808      0.054
         auto rickshaw        600         70      0.755      0.586      0.688      0.455
               bicycle        600         97      0.716      0.361      0.376      0.164
                   bus        600        698      0.808      0.685      0.739      0.512
                   car        600       1097      0.741      0.727      0.738      0.512
            garbagevan        600          1          1          0   0.000257   5.14e-05
          human hauler        600         40      0.851      0.375      0.479      0.341
               minibus        600         18      0.322      0.333      0.261      0.132
               minivan        600        158      0.402        0.5      0.401      0.277
             motorbike        600        466      0.723      0.618      0.628      0.318
                Pickup        600        238      0.559      0.445      0.473      0.313
          army vehicle        600          6      0.806        0.5      0.631       0.53
             policecar        600          6          1          0    0.00993    0.00718
              rickshaw        600        851      0.748      0.593      0.627      0.375
               scooter        600          7          1          0    0.00106   0.000362
                   suv        600        182      0.546      0.396      0.431      0.313
                  taxi        600          7       0.61      0.286      0.388      0.298
  three wheelers (CNG)        600        680      0.836      0.762      0.801       0.53
                 truck        600        275      0.753      0.643      0.686      0.465
                   van        600        148        0.6      0.547      0.517      0.344
           wheelbarrow        600         23      0.506      0.217      0.231      0.178
Speed: 0.1ms pre-process, 1.5ms inference, 8.3ms NMS per image at shape (128, 3, 640, 640)
```
