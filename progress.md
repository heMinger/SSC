## 综述
1. seen:
- 3D Semantic Scene Completion: A Survey （2022）
- 3D Semantic Scene Completion and Occupancy Prediction for Autonomous Driving: A Survey (2023)
2. notes
- [幕布上的思维导图](https://mubu.com/app/edit/home/6B6jLJxUr97#m)
- 3D SSC survey
- 3D SSC and occupancy survey.pdf

## 2D Inpainting
1. seen
- High-Resolution Image Synthesis with Latent Diffusion Models (2022)
- RePaint: Inpainting using Denoising Diffusion Probabilistic Models (2022)

2. todo
- DreamBooth: Fine Tuning Text-to-Image Diffusion Models for Subject-Driven Generation (2023)
- Adding Conditional Control to Text-to-Image Diffusion Models (2023)
- LeftRefill: Filling Right Canvas based on Left Reference through Generalized Text-to-Image Diffusion Model (2024)
- BrushNet: A Plug-and-Play Image Inpainting Model with Decomposed Dual-Branch Diffusion (2024)
- A Task is Worth One Word: Learning with Task Prompts for High-Quality Versatile Image Inpainting (2024)

**$\color{red}{\text{在看综述的时候也看到了dual branches}}$**

3. notes
- 总.pdf : 整体看&对比了这些论文
- Latent Diffusion Model.pdf

4. 小的总结（特点合并）
- 都用FM (Fusion Model)
- 都是 text-to-image
- 好像都在调整Control的方式

## NeRF
1. seen
- NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis (2020)
  - 已知缺点：
    - 在RF上建模，用MLP的参数表示场景，连续但是隐式表示，没法edit -> GS: editable
    - sample 的时候好像有点慢
- 
2. todo
- NeRF-In: Free-Form NeRF Inpainting with RGB-D Priors (2022)
- SPIn-NeRF: Multiview Segmentation and Perceptual Inpainting with Neural Radiance Fields (2023)
- Removing Objects From Neural Radiance Fields (2023)
- Reference-guided Controllable Inpainting of Neural Radiance Fields (2023)
- Taming Latent Diffusion Model for Neural Radiance Field Inpainting (2024)
- NeRFiller: Completing Scenes via Generative 3D Inpainting (2024)
- NeRF Inpainting with Geometric Diffusion Prior and Balanced Score Distillation (2024)
- MVIP-NeRF: Multi-View 3D Inpainting on NeRF Scenes via Diffusion Prior (2024)

3. notes
- NeRF.pdf: 记录了 NeRF还有NeRF几个应用的简单记录

5. 特点归类
- 大致看了下，有跟inpainting的结合 or 跟diffusion Model的结合
- 利用一些 prior knowledge

## 3D GS
1. seen
- 3D Gaussian Splatting for Real-Time Radiance Field Rendering (2023)
- 

2. todo
- InFusion: Inpainting 3D Gaussians via Learning Depth Completion from Diffusion Prior (2024)
- RefFusion: Reference Adapted Diffusion Models for 3D Scene Inpainting (2024)
- Gaussian Grouping: Segment and Edit Anything in 3D Scenes (2024)
- GaussCtrl: Multi-View Consistent Text-Driven 3D Gaussian Splatting Editing (2024)

3. notes
- 3D GS.pdf
- 

4. 特点归类

$\color{red}{\text{看到这我终于知道需要看inpainting了}}$

## SSC
1. seen
- Semantic Scene Completion from a Single Depth Image (2017)
- LMSCNet: Lightweight Multiscale 3D Semantic Completion (2020)
- S3CNet: A Sparse Semantic Scene Completion Network for LiDAR Point Clouds (2020)
- 4D Spatio-Temporal ConvNets: Minkowski Convolutional Neural Networks (2019)
2. todo
  
[这里剩一堆呢](https://oceanechy.github.io/2023/10/29/ssc/)

3. notes

- SSCNet
- LMSCNet
- 4D Spatio-Temporal ConvNet.pdf
- S3CNet.pdf
  
## 问题总结

### SSC

*SSCNet*
1. 深度图像不能直接得到voxel representation
2. dilation-based 3D context module
3. 用到了3D contextual information
*LMSCNet*
1. 3D segmentation head （目的？位置？）
*3D SSC and occupancy prediction survey*
1. SSC 适合indoor static scene? 还适合自动驾驶汽车的场景吗？
2. multimodal 是什么？怎么才算？

*S3CNet*
1. Bird-Eye View: BEV
2. Minkowski Engine
3. generalized convolution: 可以任意尺度？ -> 利于多尺度融合？ 多维空间

### NeRF
*NeRF.pdf*
2. alpha compositing (blending)
3. LLFF
4. 2D & 3D inpainting
- 2D inpainting: 进行补全
- 3D inpainting: remove不想要的object(mask)

### 3D GS

*3D GS.pdf*
1. NeRF是volumetric representation, 跟meshes/point cloud什么区别？什么关系？
2. 怎么根据一些指标（梯度等）发现有没有问题 & 如何解决问题？
3. PDF的作用到底是什么？能反映什么问题？物理意义？

## 跑过的模型
- DDPM
- NeRF
- SSCNet

## 总结过的知识点

1. 显示3D表示：voxel grid; point cloud; triangle mesh; 3D gaussian splatting;
2. volume rendering technique
3. BTF (Bidirectional Texture Function)
4. LiDAR (Range Image & Point Cloud)
5. Depth Image & Range Image & signed distance image
6. IMU sensors
7. SfM (Structure-from-Motion)
8. MVS (Multi View Stereo)
9. Rasterize
10. anisotropic convariance
11. SH, Spherical Harmonics (表示颜色)
12. Camera Calibration: 确定相机(内外)参数
- - - - - - - -

### 应用的组件 or 网络架构 要考虑的一些问题等
1. cylindrical tri-perspective view
2. 2D 信息的利用
- 2D conv进行feature extraction -> project to 3D
- 2D & 3D feature fusion
3. feature projection
- 2D-to-3D projection
- render应该也算是一种吧
3. 感受野的大小
4. contextual information
5. prior knowledge
4. Convolution
- minkowski Conv
- sparse CNNs
- generalized sparse CNNs
- dilated convolution
- spatio-Temporal CNN
- ASPP (atrous spatial pyramid pooling)
5. fusion of 2D & 3D features
6. feature aggression
