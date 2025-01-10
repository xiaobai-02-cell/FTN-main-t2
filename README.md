# Fully Transformer Network for Change Detection of Remote Sensing Images 论文复现
****

Paper Links: [Fully Transformer Network for Change Detection of Remote Sensing Images
](https://openaccess.thecvf.com/content/ACCV2022/html/Yan_Fully_Transformer_Network_for_Change_Detection_of_Remote_Sensing_Images_ACCV_2022_paper.html)

## Introduction
****
近年来，随着深度学习的发展，遥感图像的变化检测（CD）取得了长足的进步。然而，由于提取的视觉特征的表示能力有限，目前的方法通常会提供不完整的CD区域和不规则的CD边界。为了缓解这些问题，在这项工作中，我们提出了一种名为全变换网络（FTN）的遥感图像CD学习框架，该框架改进了从全局视图中提取特征的方法，并以金字塔的方式组合了多级视觉特征。更具体地说，所提出的框架首先利用了Transformer在远程依赖建模中的优势。它可以帮助学习更具判别性的全局级特征，并获得完整的CD区域。然后，我们引入金字塔结构来聚合变形金刚的多级视觉特征，以增强特征。金字塔结构嫁接了渐进式注意力模块（PAM），可以通过通道注意力来提高特征表示能力，并增加相互依赖性。最后，为了更好地训练框架，我们利用了具有多个有界感知损失函数的深度监督学习。大量实验表明，我们提出的方法在四个公共CD基准测试中取得了最新的性能。

## 复现实验环境
****
* python 3.5+
* PyTorch 1.1+
* torchvision
* Numpy
* tqdm
* OpenCV

## 准备工作
****

1.下载公开检测数据集:
* LEVIR-CD
* WHU-CD
* SYSU-CD
* Google-CD

注：因为原数据集图片大小为1024*1024，需要手动处理为224*224

2.下载在ImageNet22K上预训练好的SwinTransformer模型
* [Get models in this link](https://github.com/SwinTransformer/storage/releases/download/v1.0.0/swin_base_patch4_window7_224_22kto1k.pth): SwinB pre-trained on ImageNet22K 



### 以WHU-CD数据集为例进行论文结果复现
****
![8d114e2a7787fd707e250d19535e3a1](https://github.com/user-attachments/assets/23f7f1b2-d75f-484c-879e-94430938e394)

- For training, run:

```bash
python train_(name of the dataset).py
```

[//]: # (- If you want to use the SSIM and IOU loss function with CrossEntropy loss funtion together, you just need to remove comments in train.py &#40;below the CrossEntropy loss&#41; and add the loss operation in the loss calculation place.&#41;)
[//]: # (- Especially, when you calculate the IOU loss, you need to convert the images &#40;convert 0->1, 1->0&#41;. Because the image pixels values are mostly 0, and it will influence the IOU loss calculation &#40;Based on IOU loss characteristic&#41;.)

- For prediction, run:
```bash
python test_swin.py 
```

- For evaluation, run:
```bash
python deal_evaluation.py 
```
