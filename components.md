## 应用组件
- a squeeze re-weight (SR) layer. Y. Wang, T. Shi, P. Yun, L. Tai, and M. Liu. Pointseg: Real-time semantic segmentation based on 3d lidar point cloud. arXiv preprint arXiv:1807.06288, 2018
- context aggreagation module(CAM): B. Wu, X. Zhou, S. Zhao, X. Yue, and K. Keutzer. Squeezesegv2: Improved model structure and unsupervised domain adaptation for road-object segmentation from a lidar point cloud. In 2019 International Conference on Robotics and Automation (ICRA), pages 4376–4382. IEEE, 2019.
- **dilated convolution**: F. Yu and V. Koltun. Multi-scale context aggregation by dilated convolutions. In ICLR, 2016.

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

## Generalized Sparse CNNs
## dilated convolution

- F. Yu and V. Koltun. Multi-scale context aggregation by dilated convolutions. In ICLR, 2016.

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

## Fusion of 2D and 3D Features

## Different Scene
- Although RGB-D cameras can provide depth geometric information, they are not suitable for outdoor scenes.
- Ordinary cameras are suitable for outdoor scenes and have lower costs.

## Contextual information
- 感觉是更后面一点的方法了，（不，好像SSCNet就考虑了）
- 感觉跟**prior knowlwdge**也有关系

## feature aggression
- Additionally, some research explores different methods for feature aggregation, such as orthogonal tri-perspective view aggregation [26], non-parametric interpolation for 3D feature aggregation without depth estimation [27], and a combination of forward and backward projection for 3D feature aggregation
  - from 《3D SSC and Occupancy Survey》
  
