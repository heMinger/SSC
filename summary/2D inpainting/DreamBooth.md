## 3.1 Text-to-Image Diffusion Models

1. conditioned DM
- pre-trained diffusion model generate a image $x_gen$
- $x_gen = x_θ(ε, c)$
  - c: text encoder encode a text prompt

## 3.2 Personalization of Text-to-Image Models

### Design prompts for few-shot personalization

1. label subject "a [identifier] [class noun]"
- identifier: unique identifier linked to subject
- class noun: coarse class descriptor of subject -> **tether the prior of the clas to unique subject**

### Rare-token Identifiers
1. existing english words: has original meaning -> prior (不想要这些prior) -> rare tokens
2. rare token identifiers -> use detokenizer to obtain a sequence of characters (unique identifier)

## Class-specific Prior Preservation Loss
1. to encourage diversity and counter language drift

# 与SSC的关联
1. Dreambooth：面向SSC的少样本数据增强
SSC痛点：真实场景中某些语义类别（如稀有物体、特定建筑）标注数据稀缺。

Dreambooth的价值：

生成特定主体：用3-5张目标物体（如“消防栓”）图片微调模型，生成该物体在不同场景（街道、公园）下的多样化图像，扩充训练数据。

保留细节：通过罕见词绑定保留物体细粒度特征（如纹理），提升分割模型对细节的敏感性。

潜在应用：

生成罕见物体（工地机械、特殊植被）的合成数据，解决长尾分布问题。

模拟不同光照/天气下的场景，增强分割模型鲁棒性。
