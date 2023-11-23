# GS-Msa

> GS-Msa AI/ML Object detection service

GS-msa is a microservice-based object detection deep learning service. By reconstructing the existing monolithic deep learning model, scalability is enhanced and flexible deployment is possible. It also shows improved inference accuracy by applying different networks according to the information in the image.

## Contents
<hr/>
* Requirements
* Architecture
* Installation

### Requirements
<hr/>
| | version  (Recommended)|
|-----|-----|
|Python|3.8|
|Cuda|11.4|
|Kubernetes|1.22|
|Opencv|4.4.0|
|Flask|2.0.2|


### Architecture
<hr/>

![msa-architecture1](./images/%EA%B7%B8%EB%A6%BC1.png)
![msa-architecture2](./images/%EA%B7%B8%EB%A6%BC2.png)



### Installation
<hr/>

For Training
```bash
python3 train.py --batch-size 4 --img 640 640 --data data/person.yaml --cfg yolov4-csp-medium-edit2.yaml --weights '' --sync-bn --device 0 --name yolov4-csp-small2 --epochs 200
```

For Inferencing

```bash
kubectl apply -f ./yaml/persistant_volume.yaml
kubectl apply -f ./yaml/persistant_volume_claim.yaml
kubectl apply -f ./yaml/yolo_preprocess_220411.yaml
kubectl apply -f ./yaml/preprocess-svc.yaml
kubectl apply -f ./inference_220411.yaml
kubectl apply -f ./postprocess_220411.yaml
```

Inferred after accessing the web by entering the IP specified to perform the webpage and the port number specified by the service.
