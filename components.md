## 应用组件
- a squeeze re-weight (SR) layer. Y. Wang, T. Shi, P. Yun, L. Tai, and M. Liu. Pointseg: Real-time semantic segmentation based on 3d lidar point cloud. arXiv preprint arXiv:1807.06288, 2018
- context aggreagation module(CAM): B. Wu, X. Zhou, S. Zhao, X. Yue, and K. Keutzer. Squeezesegv2: Improved model structure and unsupervised domain adaptation for road-object segmentation from a lidar point cloud. In 2019 International Conference on Robotics and Automation (ICRA), pages 4376–4382. IEEE, 2019.
- **dilated convolution**: F. Yu and V. Koltun. Multi-scale context aggregation by dilated convolutions. In ICLR, 2016.

## cylindrical tri-perspective view
- point cloud representation
- Sicheng Zuo, Wenzhao Zheng, Yuanhui Huang, Jie Zhou, and Jiwen Lu. Pointocc: Cylindrical tri-perspective view for point-based 3d semantic occupancy prediction. arXiv preprint arXiv:2308.16896, 2023

## contextual information
1. skip connection
2. dilated information
3. ASPP
4. self-attention
5. global pooling
6. 3D CRP(Context Relation Prior) - MonoScene

## 2D 信息如何用
- 使用2 conv进行feature extration, Project to 3D
- 2D & 3D feature fusion

## 感受野
- dilated convolution
- ASPP: Moreover, an ASPP [20] module in the final encoder layer extends the receptive field and preserves details, leading to an enhancement in SSC accuracy. (from survey)

# CNNs 

## Minkowski CNNs
- C. Choy, J. Gwak, and S. Savarese. 4d spatio-temporal convnets: Minkowski convolutional neural networks. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 3075–3084, 2019.
- Minkowski Engine. C. Choy, J. Gwak, and S. Savarese. 4d spatio-temporal convnets: Minkowski convolutional neural networks. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 3075–3084, 2019.
1. adopt sparse CNNs

## Sparse CNNs
- Benjamin Graham. Spatially-sparse convolutional neural networks. arXiv preprint arXiv:1409.6070, 2014. 1, 3
- Ben Graham. Sparse 3d convolutional neural networks. British Machine Vision Conference, 2015. 1, 2, 3, 8

## AIC (Anisotropic Convolution)
- 可以使计算高效（幕布）

## Generalized Sparse CNNs
## dilated convolution

- F. Yu and V. Koltun. Multi-scale context aggregation by dilated convolutions. In ICLR, 2016.

## Spatio-Temporal
- 4D Spatio-Temporal ConvNets: Minkowski Convolutional Neural Networks
- MotionSC(使用了Spatio-Temporal Pyramid Network)
## dense or sparse convolutional
## whether computionally expensive(intensive)

## Feature projection
- However, MonoScene uses a dense 2D-to-3D feature projection, which may result in blurred 3D features. In contrast, VoxFormer [21] employs a different projection approach. (from 3D SSC and Occupancy Survey)
- 2D-to-3D projection

## Dataset
- RGB-D image
- RGB-only
- LiDAR
- prior information

## ASPP(atrous spatial pyramid pooling pooling)
1. 多尺度空洞卷积+全局平均池化+特征融合
2. ASPP的工作流程
- 输入特征图：假设输入特征图尺寸为 H×W×C。
- 多尺度卷积：
  - 分支1：空洞率=6 的 3x3 卷积 → 输出尺寸 H×W×C'
  - 分支2：空洞率=12 的 3x3 卷积 → 输出尺寸 H×W×C'
  - 分支3：空洞率=18 的 3x3 卷积 → 输出尺寸 H×W×C'
  - 分支4：1x1 卷积（空洞率=1，等效普通卷积） → 输出尺寸 H×W×C'
  - 分支5：全局平均池化 → 1x1xC' → 上采样恢复至 H×W×C'
- 特征融合：将所有分支的输出沿通道拼接，得到 H×W×(5*C')，再用 1x1 卷积降维至 H×W×C''。
2. ASPP的优势
- 多尺度感知：通过不同空洞率覆盖不同大小的物体。
- 保持分辨率：空洞卷积不降低特征图分辨率（相比池化操作）。
- 全局-局部结合：全局平均池化补充整体场景信息。

## Fusion of 2D and 3D Features
- 1*1 Conv 可以进行跨通道信息融合

## Different Scene
- Although RGB-D cameras can provide depth geometric information, they are not suitable for outdoor scenes.
- Ordinary cameras are suitable for outdoor scenes and have lower costs.

## Contextual information
- 感觉是更后面一点的方法了，（不，好像SSCNet就考虑了）
- 感觉跟**prior knowlwdge**也有关系

## feature aggression
- Additionally, some research explores different methods for feature aggregation, such as orthogonal tri-perspective view aggregation [26], non-parametric interpolation for 3D feature aggregation without depth estimation [27], and a combination of forward and backward projection for 3D feature aggregation
  - from 《3D SSC and Occupancy Survey》
  
