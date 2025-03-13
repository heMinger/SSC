## UniOcc
2D feature encoder -> 2D-3D transformer -> 3D encoder -> occupancy head
- $\color{red}{最后接的是occupancy head 不是SSC  head, 可以直接拿来用？？？}$

## survey
1. 我能找到的综述都是21年的了，好几年没有综述了，最近技术又发展了，真的可以写篇综述
- 3D Semantic Scene Completion and Occupancy Prediction for Autonomous Driving: A Survey - 23年的文章

## 组成
- fusion model: 这是一个改进方向？

## 2D inpainting & SSC
1. 2D inpainting 既可以补全一部分区域，也可以根据mask删除一些object
2. 二者都是一些补全工作，Image的补全&scene的补全。
   - 为什么2D inpainting有那么多工作用diffusion Model 但SSC没怎么有？
3. SSC 可不可以是以下两个工作的结合？
   - multi-view inpainting
   - multi-view consistent

## 效率问题
1. 对3D scene中free space的表示 important
2. dense 之后就 sparse
3. sparse之后就加一些之前没用过的信息
4. hierarchical
5. variation of CNNs
- dimensional decomposition residual network: Rgbd based dimensional decomposition residual network for 3d semantic scene completion.(2019)
- spatial group conv: Efficient semantic scene completion network with spatial group convolution. (2018)
6. 跟使用的数据也有关系
- 比如，在DDR中，说SSCNet和TS3D使用的TSDF计算密集

## Inpaint 和 SSC的区别是什么呢？
1. based on my knowledges
- inpainting 是修复图像masked region，既是补全，又是object removal
- SSC 像是多视角 各自的inpainting， 以及视角间的consistent
2. 区别 (deepseek)

|维度	   | Inpainting               |	   SSC                     |
|--------|--------------------------|-----------------------------|
|数据模态	|2D图像（RGB）   	         |3D数据（点云、深度图、体素）    |
|输出形式	|修复后的2D图像	            |3D体素网格（几何+语义）        |
|任务重点	|局部纹理和结构的连贯性      |全局场景的几何完整性和语义一致性|
|应用场景	|图像编辑、旧照片修复      	|自动驾驶、机器人导航、AR/VR    |
|方法类型 |生成模型（如GAN、扩散模型）	|3D卷积网络、体素分割网络       |

3. 联系 (deepseek)
- 共同目标：补全缺失信息，基于上下文推理生成合理内容。
- 技术重叠：
  - 均依赖上下文理解（如使用注意力机制或3D卷积）。
  - 生成模型（如GAN、VAE）在两者中均有应用。
  - 可能需要处理遮挡或噪声输入。
4. 如何利用Inpainting方法解决SSC问题？(deepseek) -思想借鉴
- 基于生成模型的补全
  - 方法迁移：
    - 将2D图像生成模型（如扩散模型、GAN）扩展至3D，生成缺失的体素或点云。
    - 例如，使用3D-GAN生成完整场景的几何结构，再结合语义分割网络分配类别标签。
- 上下文感知的补全
  - 注意力机制：
    - 在SSC网络中引入类似Inpainting中的注意力模块（如Transformer），增强对长距离依赖的建模能力，推理被遮挡区域的可能内容。
  - 多尺度补全：
    - 借鉴Inpainting中的多尺度生成策略（如由粗到细），先补全全局结构，再细化局部细节
  - thinking
    - SSC 需要long-term contextual information吗？比如桌子之类的不会以来门口的信息进行推断。or，有一个trade-off
- 联合优化几何与语义
  - 端到端框架：
    - 将Inpainting中的联合优化策略（如同时修复纹理和结构）引入SSC，设计网络同时输出几何补全和语义分割结果。
    - 例如，使用双分支网络：一支预测几何占用，另一支预测语义标签，共享底层特征。
- 数据增强与合成
  - 遮挡模拟：
    - 在训练SSC模型时，借鉴Inpainting的数据增强方法，人为生成遮挡（随机擦除部分体素或点云），提升模型对缺失数据的鲁棒性。
    - 优势：生成高保真度的细节，适用于复杂场景的补全。
5. SSC问题为什么不用DMs? (DeepSeek)
(1) 数据维度与计算成本
- 3D数据的复杂性：
  - SSC处理的输入和输出是3D体素网格或点云，数据维度远高于2D图像（如256³体素 vs. 512x512像素）。扩散模型需要对高维数据逐步去噪，计算成本极高（显存和训练时间）。
  - 举例：一张512x512图像的扩散模型训练需要数天，而3D体素网格（如128³）的扩散模型训练可能需数周，且显存需求呈立方增长。
- 实时性需求：
  - SSC常应用于自动驾驶或机器人导航，需实时推理（如30 FPS以上）。扩散模型的迭代采样过程（通常需50~100步）难以满足实时性要求。

(2) 语义约束的挑战
- 几何与语义的强耦合：
  - SSC需同时补全几何（体素是否占用）和语义（物体类别）。扩散模型擅长生成“合理”内容，但难以直接控制生成结果的语义标签与几何结构的严格匹配。
  - 例如：扩散模型可能生成形状合理但语义错误的物体（如将“桌子”补全为“椅子”）。

(3) 已有方法的成熟度
- 3D卷积网络的高效性：
  - 现有SSC方法（如TSDF融合+3D UNet）已能有效提取多尺度3D特征，并联合优化几何与语义。这些方法在速度和精度上更成熟，且易于部署。

(4) 数据稀疏性问题
- 输入数据的稀疏性：
  - SSC的输入常为单视角深度图或稀疏点云，扩散模型在极稀疏数据下的生成稳定性较差（易产生模糊或错误结构）
6. SSC 为什么不用NeRF或者Gaussian Splatting？ (DeepSeek)
- NeRF（Neural Radiance Fields）的局限性
  - 输入依赖多视角图像：
    - NeRF需大量多视角图像（或密集点云）才能重建高质量3D场景，而SSC的输入通常是单视角或稀疏数据（如单目深度图），无法满足NeRF的数据需求。
  - 缺乏显式语义输出：
    - NeRF输出的是辐射场（颜色和密度），而非直接的几何占用或语义标签。将NeRF与语义分割结合需要额外设计（如Semantic-NeRF），复杂度高。
  - 计算效率低：
    - NeRF渲染单张图像需数秒，无法满足SSC的实时性需求。
- Gaussian Splatting的局限性
- 侧重实时渲染，而非补全：
  - Gaussian Splatting是一种高效的点云渲染技术，擅长将点云快速投影到2D屏幕，但本身不解决3D补全或语义推理问题。
- 缺乏结构化表示：
  - Gaussian Splatting以点云为基础，难以直接支持密集的体素级语义分割。

7. SSC的未来方向：能否融合NeRF或扩散模型？(DeepSeek)
(1) 扩散模型与SSC的初步探索
- 3D扩散模型：
  - 方法：将扩散模型扩展至3D数据（如扩散点云生成）。
  - 挑战：需设计轻量化的3D扩散架构（如Diffusion-S3，2023），并解决语义控制问题。
  - 潜力：生成更合理的遮挡区域几何。

(2) NeRF与SSC的结合
- NeRF辅助的SSC：
  - 方法：用NeRF生成多视角深度图，再输入至SSC网络（如NeRF-SSC，2023）。
  - 优势：提升单目输入下的几何补全质量。
  - 局限：依赖NeRF的渲染速度，难以实时运行。

(3) Gaussian Splatting的潜在应用
- 动态场景表达：
  - 方法：用Gaussian Splatting表示动态场景，结合时序信息进行补全（如自动驾驶中的运动物体预测）。
  - 挑战：需解决动态点云的语义一致性。
