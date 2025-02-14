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
