# hm2
## 

## Prerequisites
####
1.Libraries (Python3.83-based)
```bash
pip3 install -r requirements.txt
pip3 install ultralytics
```
2.Dataset: https://pan.baidu.com/s/1T7wbUGKKMZMG5UiOqH2UrQ   psw：vtj3

创建 traffic_vehicle.yaml,其内容如下,：
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
```bash
python3 detect.py --source YOU/PATH/images/val/PICNAME.JPG --weights YOU/PATH/weights/best.pt --conf-thres 0.4
```
