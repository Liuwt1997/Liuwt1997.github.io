---
layout: post
title: TensorFlow安装配置调试
---

### 安装

    1. 查看版本
    2. 下载对应版本的 CUDA，默认安装
    3. 将路径添加到系统环境变量的Path中
    C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\
    C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\lib\x64
    4. 下载cuDNN，将解压的lib、bin、include文件夹中的文件分别复制到 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2 的对应文件夹中
    5. 安装对应版本的TensorFlow和TensorFlow-gpu

### 测试GPU

    import tensorflow as tf
    print('GPU', tf.test.if_gpu_available())
    出现GPU True代表成功

### 缺少DLL的问题

    搜索对应的dll，复制到C:\Windows\System32中
