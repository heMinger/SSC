## 显示3D表示
1. Voxel grid
   - 规则立方体网格，每个体素存储颜色/语义/占据状态
   - 优点：直接存储，利于物理模拟，体积渲染
   - 缺点：
     - 需要大量的存储空间，分辨率受限
     - 计算复杂
3. point cloud
   - 稀疏点集合，每个点包含位置(x,y,z)以及颜色、法向量等信息
   - 优点：
     - 高效：存储密集信息不收网格拓扑限制
     - 适合扫描/重建真实世界场景(如LiDAR)
    - 缺点：
      - 没有拓扑结构，无法直接渲染（点云渲染方法）
      - 点直接缺少连接，不适合物理模拟
5. triangle mesh
   - 用顶点、边和面构建3D物体的表面
   - 优点
     - 高效存储，相比Voxel grid和point cloud更节省空间
   - 缺点
     - 仅表示表面，不适用于内部结构
     - 需要额外的拓扑信息（连接关系复杂）
7. 3D gaussian splatting
   - 高斯球表示3D场景（点云的每个点是一个高斯分布）
   - 优点
     - 比普通点云更光滑，可以直接渲染
     - 比网格更自由，没有拓扑限制
   - 缺点
     - 仍需要渲染过程，不能直接在3D引擎中使用
    
8. 可以直接3D计算方法
   - Marching Cubes(3D voxel -> 3D grid)
   - Possion Surface Reconstructure(从点云恢复光滑表面)
   - SPH(流体模拟，直接在3D空间计算物理模拟)
   - FEM(有限元分析，用于3D结构分析)
  
#### Voxel Grid & Point Cloud

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

## Structure-from-Motion (SfM)
- 通过分析多张2D图像中的特征点匹配，恢复相机位姿和3D场景结构的技术
- input: 多视角图像序列（无序or有序）
- output:
  - 相机参数（内参、外参）
  - 稀疏3D点云（scene特征点的3D坐标）
- 应用：
   - SIFT等检测图像中的关键点
   - 特征匹配：在不同图像间匹配相同特征点
   - 三角化：通过匹配点对和相机参数计算3D点位置
   - bundle adjustment: 联合优化3D点和相机参数，最小化重投影误差
- 在3D GS中： 提供初始稀疏点云，作为3D高斯球的初始化位置

## Multi-View Stereo
- 基于多视角图像的密集3D重建技术，生成稠密点云或网格模型
- input: SfM输出的相机参数+多视角图像
- output：稠密3D点云or网格模型
- 应用
   - **深度图估计**：通过立体匹配(如PatchMatch)计算图像的深度图
   - **深度图融合**：将多视角深度图融合为一致的点云or网格
- 3D GS中，作为SfM的补充，若SfM的稀疏点云不足，提供更密集的点云作为输入

## Rasterize
- 将3D几何（如三角形网格、点云、高斯椭球）转换为2D像素的过程
- 作用：
   - 将3D场景投影到2D图像平面，生成渲染图像
   - 实时性高，适合GPU加速
- 应用：
  - 传统光栅化（三角形网格）
    - 顶点处理：应用模型-视图-投影矩阵
    - 三角形遍历：确定覆盖的像素
    - 片元着色：计算像素颜色
  - GS:
    - 将3D高斯投影为2D椭圆
    - 按深度排序，逐个混合椭圆的颜色和不透明度
- 在3D GS中：在核心渲染步骤中，将3D高斯转换为2D图像（通过可微分光栅化实现梯度传播）

## anisotropic covariance
- 描述3D高斯椭球形状的协方差矩阵，允许椭球在不同方向上具有不同的缩放
- 各向异性：在不同方向上性质不同
  - 控制椭球在不同轴上不同的半径
- 在3D GS中：
  - 控制每个椭球的不同形状

## Spherical Harmonics （球谐函数，SH）
- 一组定义在球面上的正交基函数，用于紧凑表示球面函数（如光照、颜色变化）
- 作用
   - 在3D重建中表示视角无关的颜色或光照（如NeRF中的视角依赖颜色）
   - 减少参数数量，避免显示存储多视角颜色
- 数学形式
![image](https://github.com/user-attachments/assets/d8559df1-ebf7-4833-914e-6f5c42d46d94)
- 在2D GS 中的应用
  - 使用SH系数表示高斯的视角依赖颜色（例如反射高光）
  - 每个高斯存储一组SH系数，根据视角方向插值颜色
 
## Camera Calibration(相机标定)
- 确定相机的内部参数（如焦距、主点）和外部参数（如位置、朝向）
- 作用
   - 内参：焦距($f_x$, $f_y$)、主点($c_x$, $c_y$)、畸变系数（径向、切向）
   - 外参：相机在世界坐标系中的位置和旋转矩阵
- 应用方法
  - 棋盘格标定法：通过拍摄已知模式的图像（如棋盘格），计算参数
  - 自标定：通过SfM从图像序列中自动估计参数
- 在3D GS 中
  - SfM/MVS 输出的相机参数用于初始化渲染时的投影矩阵
  - 可微分渲染依赖准确的相机参数以计算梯度
