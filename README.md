# hm2
## Prerequisites
####
1.Libraries (Python3.83-based)
```bash
pip3 install -r requirements.txt
pip3 install ultralytics
```
2.Dataset: https://pan.baidu.com/s/1T7wbUGKKMZMG5UiOqH2UrQ   psw：vtj3

## Getting Start
### Training
```bash
python3 ./train.py --data YOU/PATH/traffic_vehicle.yaml --cfg YOU/PATH/yolov5s_traffic_vehicle.yaml --weights YOU/PATH/yolov5s.pt --batch-size 32 --epochs 50 --name YOU NAME --project yolo_traffic_vehicle
```
### Testing
```bash
python3 detect.py --source YOU/PATH/images/val/PICNAME.JPG --weights YOU/PATH/weights/best.pt --conf-thres 0.4
```
