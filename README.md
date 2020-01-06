# Simplified-Yolo

## Task
Object detection using a Simplified Version of Yolo-v1

## Simplified Yolo Features
* Image shape = 128x128x3
* Image is split into 8x8 patches. Each patch represents a 16x16 grid
* Single anchor box of same size as the grid cell
* Each grid is responsible for detecting the object whose center falls into the grid
* For each anchor, there are 8 channels, which encode Pr(Objectness), x, y, w, h, P(class=pedestrian),
P(class=traffic light), and P(class=car).

## Loss Function
![equation](https://latex.codecogs.com/gif.latex?\begin{aligned}&space;\text&space;{Loss}&space;&=\lambda_{\text&space;{coord}}&space;\sum_{i=0}^{S^{2}}&space;\sum_{j=0}^{B}&space;\mathbb{1}_{i&space;j}^{o&space;b&space;j}\left[\left(x_{i}-\hat{x}_{i}\right)^{2}\right]&plus;\lambda_{\text&space;{coord}}&space;\sum_{i=0}^{S^{2}}&space;\sum_{j=0}^{B}&space;\mathbb{1}_{i&space;j}^{o&space;b&space;j}\left[(\sqrt{w_{i}}-\sqrt{\hat{w}_{i}})^{2}&plus;(\sqrt{h_{i}}-\sqrt{\hat{h}_{i}})^{2}\right]&space;\\&space;&&plus;\sum_{i=0}^{S^{2}}&space;\sum_{j=0}^{B}&space;\mathbb{1}_{i&space;j}^{o&space;b&space;j}\left(C_{i}-\hat{C}_{i}\right)^{2}&plus;\lambda_{n&space;o&space;o&space;b&space;j}&space;\sum_{i=0}^{S^{2}}&space;\sum_{j=0}^{B}&space;\mathbb{1}_{i&space;j}^{n&space;o&space;b&space;b&space;j}\left(C_{i}-\hat{C}_{i}\right)^{2}&plus;\sum_{i=0}^{S^{2}}&space;\mathbb{1}_{i&space;j}^{o&space;b&space;j}&space;\sum_{c&space;\in&space;\text&space;{classes}}\left(p_{i}(c)-\hat{p}_{i}(c)\right)^{2}&space;\end{aligned})

## Postprocessing
Nms is performed to remove overlapping boxes

## Results
