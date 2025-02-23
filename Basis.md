## 3D representation
- Genova, K., Cole, F., Sud, A., Sarna, A., Funkhouser, T.: **Local deep implicit functions** for 3d shape. In: CVPR (2020)
- Mescheder, L., Oechsle, M., Niemeyer, M., Nowozin, S., Geiger, A.: Occupancy networks: Learning 3D reconstruction in function space. In: CVPR (2019)
- Jiang, C., Sud, A., Makadia, A., Huang, J., Nießner, M., Funkhouser, T.: **Local implicit grid representations** for 3d scenes. In: CVPR (2020)
- Park, J.J., Florence, P., Straub, J., Newcombe, R., Lovegrove, S.: DeepSDF: Learning continuous signed distance functions for shape representation. In: CVPR (2019)

## volume rendering technique:
- 体积渲染技术
- 作用：从3D体积数据生成2D图像
- 核心思想：沿摄像机出发的光线对场景中的体积进行采样，将每个采样点处的颜色和密度信息按照一定的光学模型（如吸收、发射和散射）进行积分累加，最终计算出射线对应的像素颜色。

## BTF: Bidirectional Texture Function
- 双向纹理函数
- 作用：描述物体表面外观如何随观察方向和光照方向的变化而变化。捕捉了表面在不同视角下的细微纹理和光照效果。
- 与NeRF：NeRF 通过 MLP 学习一个连续的场景表示，也能够捕捉视角依赖的颜色变化。BTF是一种传统的方法，NeRF利用神经网络实现了类似功能紧凑的表示。

## Bied Eye View (BEV)

## LiDAR (Range Image & Point Cloud)

- LiDAR 是可以采集数据的一种传感器
- Range Image可以有LiDAR采集到的数据直接构成
- Range image经过投影计算可以得到Point Cloud, 二者是同一组传感器数据的不同表示形式，可以相互转换

## Depth Image \ Range image \ singned distance image
三者都是将空间中的距离信息以图像形式表示的方式，但它们有以下区别：

- **Depth Image**
  - 通常指每个像素表示从相机平面（光学中心）沿光轴（通常为z轴）的距离。
  - 常见于RGB-D相机
  - 受相机投影模型和视角的影响，准确度小于range image

- **Range Image：**
  - **数据来源：** 通常由传感器（如 LiDAR）直接生成，每个像素记录传感器到物体表面的距离。
  - **距离性质：** 数值一般是绝对值（正数），只反映距离的大小，没有表示内部或外部的区分。
  - **应用场景：** 常用于实时感知、目标检测和场景理解等任务，因为它能快速提供从传感器视角看到的深度信息。

- **Signed Distance Image：**
  - **计算方式：** 由已知的场景或物体的几何信息计算得到，每个像素记录到最近表面的距离，并附有符号。
  - **距离符号：** 数值的符号通常用于指示位置关系——负值表示该点位于物体内部，正值表示在物体外部，这对于精细描述形状和边界非常有用。
  - **应用场景：** 常用于3D重建、形状优化、碰撞检测和形状表示等任务，因为其连续且有符号的特性可以提供丰富的几何信息。

简单来说，**Depth Image**的距离是从相机光学中心沿视线方向测得， **Range image** 主要关注从传感器视角直接测量的距离，而 **signed distance image** 则在此基础上增加了符号信息，用于更精确地描述空间中点与物体表面的关系。

## Voxel Grid & Point Cloud

- **Voxel Grid**
  - 将3D空间划分为**规则的立方体单元（体素）**
  - 是规则的3D结构，大小固定
  - 可以对Point Cloud等进行体素化生成。
  - 可以高效地进行3D卷积操作
 
- **Point Cloud**
  - 一组在3D空间中的离散点，每个点通常具有(x,y,z)坐标，并可能带有额外的信息，如反射强度等。
  - 通常由3D传感器(LiDAR、深度相机)生成
  - 稀疏，没有固定的拓扑结构；分布不规则
  - 难以直接处理

 Voxel Grid是为了方便数据处理，由点云等数据voxelization而来

## Sparse Tensor

- 3D和更高维的空间中，dense representation is inefficient
- normally, only save the non-empty part of the space as its coordinates and the associated features.
- coordinates and associated features: N-dimensional extension of a sparse matrix -> sparse tensor
- 有很多种存储形式：An investigation of sparse tensor formats for tensor libraries

## RADAR vs LiDAR
雷达 & 激光雷达

## IMU sensors

- 主要收集
  - 加速度数据
  - 角速度数据
  - 磁场数据
 
- 可以计算
  - 姿态（Orientation）：俯仰角（Pitch）、横滚角（Roll）、偏航角（Yaw）。
  - 运动轨迹（Motion Tracking）：速度、位移、倾斜、旋转等信息。
  - 航向（Heading）：结合磁力计进行方位估计。

## Render

**NeRF、3D GS、SSC都是在3D空间中进行计算&建模，处理的都是3D 的问题，但最终结果都通常都是渲染成2D图像**
因为
1. 2D好呈现好观察
2. 相机的建模
  - 通常有虚拟相机在场景中采集图像，现实中相机只能捕捉2D画面，想让3D场景可视化，必须把它转换成2D试图模拟相机的成像过程。
3. 训练和评估方便
  - 监督信号通常是2D信号，最终结果转换成2D易于与ground truth进行对比
