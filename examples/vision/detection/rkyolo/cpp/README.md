English | [简体中文](README_CN.md)
# RKYOLO C++ Deployment Example

This directory provides examples that `infer_xxxxx.cc` fast finishes the deployment of RKYOLO models on Rockchip board through 2-nd generation NPU

Two steps before deployment

1. Software and hardware should meet the requirements.
2. Download the precompiled deployment library or deploy FastDeploy repository from scratch according to your development environment.

Refer to [RK2 generation NPU deployment repository compilation](../../../../../docs/cn/build_and_install/rknpu2.md)

```bash
wget https://gitee.com/paddlepaddle/PaddleDetection/raw/release/2.4/demo/000000014439.jpg
cd build
cmake .. -DFASTDEPLOY_INSTALL_DIR=${PWD}/fastdeploy-linux-x64-x.x.x
make -j8
./infer_rkyolo /path/to/model 000000014439.jpg
```

## common problem

If you use the YOLOv5 model you have trained, you may encounter the problem of 'segmentation fault' after running the demo of FastDeploy. It is likely that the number of labels is inconsistent. You can use the following solution:

```c++
model.GetPostprocessor().SetClassNum(3);
```


- [Model Description](../../)
- [Python Deployment](../python)
- [Vision Model Prediction Results](../../../../../docs/api/vision_results/)
