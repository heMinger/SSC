📁 MonoScene-master \
 ┣ 📄 .gitignore \
 ┣ 📄 LICENSE \
 ┣ 📄 README.md \
 ┣ 📄 requirements.txt \
 ┣ 📄 setup.py \
 ┣ 📁 monoscene \
   ┣ 📁 config                # 配置文件 \
   ┃ ┗ 📄 monoscene.yaml \
   ┣ 📁 data                  # 数据加载模块（支持多个数据集） \
   ┃ ┣ 📁 NYU \
   ┃ ┃ ┣ 📄 nyu_dataset.py     # 处理 NYU 数据集 \
   ┃ ┃ ┣ 📄 preprocess.py      # 数据预处理 \
   ┃ ┣ 📁 kitti_360 \
   ┃ ┣ 📁 semantic_kitti \
   ┣ 📁 models                # 深度学习模型 \
   ┃ ┣ 📄 monoscene.py         # 主模型 \
   ┃ ┣ 📄 backbone.py          # 3D 语义重建的主干网络 \
   ┃ ┣ 📄 loss.py              # 损失函数 \
   ┃ ┗ 📄 layers.py            # 计算 TSDF、点云处理等 \
   ┣ 📁 utils                 # 工具模块 \
   ┃ ┣ 📄 visualization.py     # 可视化工具 \
   ┃ ┣ 📄 metrics.py           # 计算 IoU、精度等指标 \
   ┃ ┗ 📄 common.py            # 其他通用工具 \
 ┣ 📄 train.py                 # 训练脚本 \
 ┣ 📄 eval.py                  # 评估脚本 \
 ┗ 📄 demo.py                  # 运行示例 \
