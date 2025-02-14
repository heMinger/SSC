3D representation
- Genova, K., Cole, F., Sud, A., Sarna, A., Funkhouser, T.: **Local deep implicit functions** for 3d shape. In: CVPR (2020)
- Mescheder, L., Oechsle, M., Niemeyer, M., Nowozin, S., Geiger, A.: Occupancy networks: Learning 3D reconstruction in function space. In: CVPR (2019)
- Jiang, C., Sud, A., Makadia, A., Huang, J., Nießner, M., Funkhouser, T.: **Local implicit grid representations** for 3d scenes. In: CVPR (2020)
- Park, J.J., Florence, P., Straub, J., Newcombe, R., Lovegrove, S.: DeepSDF: Learning continuous signed distance functions for shape representation. In: CVPR (2019)

volume rendering technique:
- 体积渲染技术
- 作用：从3D体积数据生成2D图像
- 核心思想：沿摄像机出发的光线对场景中的体积进行采样，将每个采样点处的颜色和密度信息按照一定的光学模型（如吸收、发射和散射）进行积分累加，最终计算出射线对应的像素颜色。

BTF: Bidirectional Texture Function
- 双向纹理函数
- 作用：描述物体表面外观如何随观察方向和光照方向的变化而变化。捕捉了表面在不同视角下的细微纹理和光照效果。
- 与NeRF：NeRF 通过 MLP 学习一个连续的场景表示，也能够捕捉视角依赖的颜色变化。BTF是一种传统的方法，NeRF利用神经网络实现了类似功能紧凑的表示。

**Range image** 和 **signed distance image** 都是将空间中的距离信息以图像形式表示的方式，但它们有以下区别：

- **Range Image：**
  - **数据来源：** 通常由传感器（如 LiDAR）直接生成，每个像素记录传感器到物体表面的距离。
  - **距离性质：** 数值一般是绝对值（正数），只反映距离的大小，没有表示内部或外部的区分。
  - **应用场景：** 常用于实时感知、目标检测和场景理解等任务，因为它能快速提供从传感器视角看到的深度信息。

- **Signed Distance Image：**
  - **计算方式：** 由已知的场景或物体的几何信息计算得到，每个像素记录到最近表面的距离，并附有符号。
  - **距离符号：** 数值的符号通常用于指示位置关系——负值表示该点位于物体内部，正值表示在物体外部，这对于精细描述形状和边界非常有用。
  - **应用场景：** 常用于3D重建、形状优化、碰撞检测和形状表示等任务，因为其连续且有符号的特性可以提供丰富的几何信息。

简单来说，**Range image** 主要关注从传感器视角直接测量的距离，而 **signed distance image** 则在此基础上增加了符号信息，用于更精确地描述空间中点与物体表面的关系。

应用组件
- Minkowski Engine. C. Choy, J. Gwak, and S. Savarese. 4d spatio-temporal convnets: Minkowski convolutional neural networks. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 3075–3084, 2019.
- sparse convolution.
- a squeeze re-weight (SR) layer. Y. Wang, T. Shi, P. Yun, L. Tai, and M. Liu. Pointseg: Real-time semantic segmentation based on 3d lidar point cloud. arXiv preprint arXiv:1807.06288, 2018
- context aggreagation module(CAM): B. Wu, X. Zhou, S. Zhao, X. Yue, and K. Keutzer. Squeezesegv2: Improved model structure and unsupervised domain adaptation for road-object segmentation from a lidar point cloud. In 2019 International Conference on Robotics and Automation (ICRA), pages 4376–4382. IEEE, 2019.
- atrous spatial pyramid pooling(ASPP) pooling
