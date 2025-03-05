记录在其他文章中对这些文章的评价
# SSCNet

## See and Think: Disentangling Semantic Scene Completion

*However, they not only exploit few semantic features, but are highly customized for a specific sensor.*
*However, it takes a single depth image as input and does not take advantage of rich features of RGB.*
*In SSCNet [1], the scene surface without semantic information is encoded into a volume for completion and all the convolutions have fixed receptive fields*

## LMSCNet

*It is thus common to encode the latter as voxel grids processed by 3D Convolutional Neural Networks (CNNs) [11, 36, 12, 26]. *
*This shows good results but also requires heavy computation, as the memory requirement grows cubically with the input voxel resolution [28].*
*Consequently, most of the literature limits the predicted resolution and network depth, being incapable to perform the task at the same spatial resolution as the input [36, 15, 41].*
*This drawback has limited the deployment of such methods for real time applications i.e. augmented and virtual reality [38], robotics perception and navigation [23], scene understanding*

# ESSCNet

## LMSCNet

*Consequently, most of the literature limits the predicted resolution and network depth, being incapable to perform the task at the same spatial resolution as the input [36, 15, 41].*
*This drawback has limited the deployment of such methods for real time applications i.e. augmented and virtual reality [38], robotics perception and navigation [23], scene understanding*

# Semantic Scene Completion Combining Colour and Depth: Preliminary Experiments

## See and Think: Disentangling Semantic Scene Completion
Afterwards, [6, 24] attempt to add RGB features into the network. Overall, in the aspect of task solving, these networks introduce a tight coupling between RGB and depth so that their extensibility and evolvability are constrained.

# Two Stream 3D Semantic Scene Completion. arXiv preprint arXiv:1804.03550, 2018.

## See and Think: Disentangling Semantic Scene Completion
Afterwards, [6, 24] attempt to add RGB features into the network. Overall, in the aspect of task solving, these networks introduce a tight coupling between RGB and depth so that their extensibility and evolvability are constrained.

## StereoScene 2024
*employ 3D geometric signals, in the form of occupancy grids, point clouds, or distance fields, as their model inputs. Although they provide insightful geometric cues, it requires costly sensors (e.g. LiDAR) alongside considerable manual labor entailed in their deployment.*

## LMSCNet
*This shows good results but also requires heavy computation, as the memory requirement grows cubically with the input voxel resolution [28].*
*Consequently, most of the literature limits the predicted resolution and network depth, being incapable to perform the task at the same spatial resolution as the input [36, 15, 41].*
*This drawback has limited the deployment of such methods for real time applications i.e. augmented and virtual reality [38], robotics perception and navigation [23], scene understanding*

# LMSCNet 2020

## StereoScene 2024
*employ 3D geometric signals, in the form of occupancy grids, point clouds, or distance fields, as their model inputs. Although they provide insightful geometric cues, it requires costly sensors (e.g. LiDAR) alongside considerable manual labor entailed in their deployment.*

# Scfusion: Real-time incremental scene reconstruction with semantic completion. 2020

## StereoScene 2024
*employ 3D geometric signals, in the form of occupancy grids, point clouds, or distance fields, as their model inputs. Although they provide insightful geometric cues, it requires costly sensors (e.g. LiDAR) alongside considerable manual labor entailed in their deployment.*

# MonoScene 2022

## StereoScene 2024
*the absence of explicit 3D geometric information and incomplete observation pose large challenges to accurate geometry acquisition and reasonable hallucination in invisible regions*
*Thus, previous camera-based SSC solutions [Cao and de Charette, 2022; Huang et al., 2023] tend to utilize learning-based projection techniques to convert 2D image features into a 3D dense space, but their predictions inevitably fall short of capturing accurate geometry without explicit constraints.*
*But their results still struggle to hallucinate reasonable invisible regions without ensembling global semantic context*

## VoxFormer
*However, LiDAR sensors are expensive and less portable, while cameras are cheaper and provide richer visual cues of the driving scenes. This motivated the study of camera-based SSC solutions, as first proposed in the pioneering work of MonoScene [4]. MonoScene lifts 2D image inputs to 3D using dense feature projection. However, such a projection inevitably assigns 2D features of visible regions to the empty or occluded voxels.*

*It proposes 2D-3D feature projections and uses successive 2D and 3D UNets to achieve camera-only 3D semantic scene completion. However, 2D-to-3D feature projection is prone to introduce false features for unoccupied 3D positions, and the heavy 3D convolution will lower the system’s efficiency.*

## TPVFormer 2023
*MonoScene [5] first backprojects image features to all possible positions in the 3D space along the optical ray to obtain the initial voxel representation and further processes it using a 3D UNet. However, it is still challenging to generalize it to 3D perception with multi-view images due to the inefficiency of voxel representations*

## OccDepth 2023

*MonoScene [Cao and de Charette, 2022a] infers dense 3D voxelized semantic indoor and outdoor scenes from a single RGB image.*
*we choose to project each voxel to the corresponding image pixel as done in MonoScene [Cao and de Charette, 2022a], which establishes a full feature mapping for all voxels*

## OccFormer 2023

*The seminar work MonoScene [4] proposed the first monocular framework for 3D semantic occupancy prediction. It first constructs the 3D feature with sight projection and then processes it with a classical 3D UNet. However, the 3D convolution suffers from several limitations. First, it reasons the semantics within a relatively fixed receptive field, while different semantic classes may distribute following various patterns. Also, its spatial invariance cannot well process the sparse and discontinuous 3D features, generated from the state-of-the-art practices for image-to-3D transformation*

# Tri-perspective view for vision-based 3d semantic occupancy prediction 2023

## StereoScene 2024
*the absence of explicit 3D geometric information and incomplete observation pose large challenges to accurate geometry acquisition and reasonable hallucination in invisible regions*
*Thus, previous camera-based SSC solutions [Cao and de Charette, 2022; Huang et al., 2023] tend to utilize learning-based projection techniques to convert 2D image features into a 3D dense space, but their predictions inevitably fall short of capturing accurate geometry without explicit constraints.*
*But their results still struggle to hallucinate reasonable invisible regions without ensembling global semantic context*

# Voxformer: Sparse voxel transformer for camera-based 3d semantic scene completion 2023

## StereoScene 2024
*the absence of explicit 3D geometric information and incomplete observation pose large challenges to accurate geometry acquisition and reasonable hallucination in invisible regions*
*Later studies [Li et al., 2023a] attempt to introduce depth information to augment query for reliable geometry prediction.*
*But their results still struggle to hallucinate reasonable invisible regions without ensembling global semantic context*

# NeRF

## TPVFormer
*They learn a continuous function that takes as input the 3D coordinate of a point and outputs the representation of this point [34, 35, 37]. Compared with explicit representations like voxel and BEV, implicit representations usually share the advantage of arbitrary-resolution modeling and computation-efficient architectures. These advantages enable them to scale to larger and more complex scenes with more fine-grained descriptions*
