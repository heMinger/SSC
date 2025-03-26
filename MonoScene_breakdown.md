📁 monoscene/ - 代码主目录
┣ 📂 scripts/ - 存放深度学习模型
┣ 📂 models/ - 存放深度学习模型
┣ 📂 config/ - 存放深度学习模型
┃ ┣ 📄 monoscene.py - MonoScene 主模型
┃ ┣ 📄 backbone.py - 3D 语义重建的骨干网络
┃ ┗ 📄 loss.py - 损失函数定义
┣ 📂 data/ - 数据加载模块
┃ ┣ 📄 scannet.py - ScanNet 数据集解析
┃ ┣ 📄 transforms.py - 预处理与数据增强
┃ ┗ 📄 collate.py - 组合 batch 数据
┣ 📂 loss/ - 工具函数
┃ ┣ 📄 visualization.py - 可视化工具
┃ ┗ 📄 metrics.py - 评估指标计算
┣ 📂 trained_models/ - 
┣ 📂 output/ - 
┣ 📄 train.py - 训练主脚本
┣ 📄 eval.py - 评估脚本
┣ 📄 config.py - 配置文件
┗ 📄 README.md - 项目文档
