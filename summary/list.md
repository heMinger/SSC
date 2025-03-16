- VoxFormer (2023): transformer-based; RGB images; temproal information (current and previous images $I_t = {I_t, I_{t-1}, ...}$); visual features on 2D images correspond only to the visible scene structures (很多人拿来批评，不利用occluded or empty spaces (Sparse Voxel Transformer for Camera-based 3D Semantic Scene Completion)
- UniOcc (2023): multi-view RGB images; Neural Field; Volume Renderding Supervision; geometry + semantic (render); without 3D annotation labels (Unifying Vision-Centric 3D Occupancy Prediction with Geometric and Semantic Rendering
- TPVFormer (2023): transformer-based; RGB images; TPV representation; 2D feature -> 3D  TPV; LiDAR-based sparse 3D occupancy (Tri-Perspective View for Vision-Based 3D Semantic Occupancy Prediction
- Symphonise (2023): transformer-based; instance query; (Symphonize 3D Semantic Scene Completion with Contextual Instance Queries
- SurroundOcc (2023): transformer-based; multi-scale multi-view RGB images; 2D-3D spatial attention;  (Multi-Camera 3D Occupancy Prediction for Autonomous Driving
- OccNet (2023): transformer-based (BEVFormer); multi-view RGB images; BEV encoder; spatial-temporal-transformer block; cascaded Voxel Decoder (Scene as Occupancy
- S4C (2023): nerual field; volumetric semantic rendering; without 3D GT(Ground Truth); self-supervised (multi-view consistency); (Self-Supervised Semantic Scene Completion with Neural Fields
- RenderOcc(2024): NeRF-style 3D volume representation; multi-view images; volume render; without 3D supervision only 2D labels; multi-camera RGB images; Semantic-Density-Field (SDF) (volume + semantic); multi-view consistency (Vision-Centric 3D Occupancy Prediction with 2D Rendering Supervision
- PointOcc (2023): Cylindrical TPV; LiDAR point clouds; FPN (Feature Pyramid Network, 2D-to-3D) (Cylindrical Tri-perspective View for Point-based 3D Semantic Occupancy Prediction
- PanoOcc (2023): transformer-based; multi-frame + multi-view images (spatiotemporal information);  (Unified Occupancy Representation for Camera-based 3D Panoptic Segmentation
- OVO (2023): open vocabulary; 2D open-vocabulary segmentation model; text encoder; knowledge distillation (Open-Vocabulary Occupancy
- OG Occupancy Grounding (2023): instance segmentation (2D instance segment model); visual grounding (Grounded-SAM); affinity field regression (Equip vision occupancy with instance segmentation and visual grounding
- OccFormer (2023): transformer-based; RGB image; depth and feature outer product (image-to-3D); Dual-path Transformer Blocks; Transformer Occupancy Decoder (Dual-oath Transformer for Vision-based 3D Semantic Occupancy Prediction
- OccDepth (2023): Stereo images(Left + right); Depth (implicit & explicit); Stereo-SFA(soft feature assignment) module(2D-to-3D); Tracher-Student; 3D Unet(for 3D volume) (A Depth-Aware Method for 3D Semantic Scene Completion
- NDC-Scene (2023): MonoScene improvement (feature/pose/ ambiguity + computation imbalance); attetion
- MonoScene (2022): single monocular RGB image; 3D context relation prior; 2D Unet + FLoSP (Feature Line of Sight Projection, 2D-to-3D) + 3D Unet(3D CRP) + completion head
- FB-BEV: transformer-based (spatial cross-attention, depth consistency); forward+backward BEV; multi-view images; (BEV Representation from Forward-Backward View Transformations
- 

- - - - - - - - - - - - - - - - - - - - - - - 
- Two Stream 3D SSC (2019): depth + semantic (two streams); 3D CNN (跟transformer-based的区别是，这里的3D CNN既用来处理3D volume提取特征，也用来最终的prediction(softmax layer), 但是transformer-based方法只有最后的MLP layer用来预测结果 ; 也有把2D 信息提取到3D 的步骤
- SSCNet (2017): single depth image; f-TSDF; 3D CNN (Semantic Scene Completion from a Single Depth Image
- SATNet (2018): SNet -> 2D information; Reprojection to 3D; TNet -> 3D feature; RGB + depth (See and Think: Disentangling Semantic Scene Completion
- S3CNet (2020): large outdoor driving scene; LiDAR point cloud; 2D (BEV) + 3D S3CNet; (A Sparse Semantic Scene Completion Network for LiDAR Point Clouds
- RGBD Based Dimensional Decomposition Residual Network for 3D SSC (2019): RGB + Depth; DDR (Dimensional Decomposition Residual network) Multi-level feature fusion; ASPP
- LMSCNet (2020): LiDAR scans; Unet (2D backbone) + 3D segmentation heads; ASPP (Lightweight Multiscale 3D Semantic Completion

- - - -  - - - - - 
- Dilated Convolution (2016): larger perspective field; contextual information (Multi-Scale Context Aggregation by Dilated Convolutions
- 

- - - - - - 
*TODO*
- SC-Diff: 3D Shape Completion With Latent Diffusion Models
- NDC-Scene
- FB-BEV
