# 基于 Transformer 的图像分类 [[English](./README_en.md)]

## 依赖模块
- os
- numpy
- opencv
- pillow
- paddlepaddle==2.0.0

## 项目介绍
'''
|-data: 存放ImageNet验证集
|-transform.py: 数据预处理脚本
|-dataset.py: 读取数据脚本
|-model.py: 该脚本中定义了ViT以及DeiT的网络结构
|-eval.py: 启动模型评估的脚本

'''

当前项目仅支持对ViT和DeiT进行模型评估，模型训练过程会在后续更新中进行支持。

## 数据集准备
- 进入 repo 目录

  ```
  cd path_to_Transformer-classification
  ```

- 下载[ImageNet验证集](https://aistudio.baidu.com/aistudio/datasetdetail/93561)到`data`目录下

- 解压数据集

  请按照如下格式组织数据集

  ```
  data/ILSVRC2012_val
  |_ val
  |_ val_list.txt
  ```

## 模型准备

- 进入 repo 目录

  ```
  cd path_to_Transformer-classification
  ```

- 下载ViT和DeiT的模型权重文件到`model_file`目录下

  ```
  cd model_file
  wget https://paddle-imagenet-models-name.bj.bcebos.com/dygraph/ViT_base_patch16_384_pretrained.pdparams
  wget https://paddle-imagenet-models-name.bj.bcebos.com/dygraph/DeiT_base_distilled_patch16_384_pretrained.pdparams
  cd ../
  ```

## 模型评估

可以通过以下方式开始模型评估过程

```bash
python3 eval.py 
    --model ViT  \
    --data data/ILSVRC2012_val
```

上述命令中，需要传入如下参数:

+ `model`: 模型名称，默认值为 `ViT`，可以更换为 `DeiT`;
+ `data`: 保存ImageNet验证集的目录, 默认值为 `data/ILSVRC2012_val`。