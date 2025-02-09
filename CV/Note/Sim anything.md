不懂的直接看相关工作有贴一些introduction的链接

### Work Flow
* 场景重建和物体级3D开放词汇分割
* 多视角图像修补
* 预测物体平均物理属性(MLLM-P3)
* 基于平均值和物体的几何形状，估计完整物理属性分布(MPDP)
* 问题重新表述为概率分布估计，然后采取物理自适应采样策略(PGAS)，在开放世界场景中模拟物体中的运动
* 利用粒子采样高效捕捉复杂变形。
### 贡献
* 对于3D重建的物理模拟中避免物理参数的手动设置的方法提出改进,**降低成本**
* 提高了泛化性，**改进了对于刚性物体的适应能力**
### 方法详细说明
#### 场景重建
* 对给定位置和给定的图片训一个3DGS 模型
* 集成2D open-vacabulary models(取长补短)，从而自动分割物体
* radiance field rendering渲到3D里
* Lama技术还原从3DGM扣物体产生的空洞
#### 物理参数估计
* 用**VQA**模型(视觉问答)对渲出的3D对象生成文本描述
* 连同图像一起传递给一个多模态大语言模型（MLLM），例如GPT-4V [41]，提示它返回一个包含K个候选材料及其是否为刚性物体（与第4.3节中的采样方法相关）信息的字典
* 计算CLIP相似度来选择材料
* 材料名称、图像和文本描述传递给MLLM，返回该对象的一系列物理属性。
#### 物理属性分布(对于细节的物理属性模拟)
* 训一个网络，接收点云和平均值，输出粒子的预测物理性质，并用Physics3D进行监督，输出一个概率分布
* 将分布放缩成平均值(逐元素乘法)
#### 物理自适应仿真
* 自适应调整物体采样的半径和曲率
* 用MLS-MPM算法做模拟
  
### 数据集使用
* LERF:
* Instruct-NeRF2NeRF:
### 相关工作(顺手看一看)
* PhysDreamer:用视频生成模型来估计物理参数
* [DreamPhysics]()
* Physics3D :与上面一样
* PhysGaussian:
* (3DGS)Radience Fields rendering:[链接](https://zhuanlan.zhihu.com/p/12633430919)
* open-vocabulary models:[综述](https://github.com/jianzongwu/Awesome-Open-Vocabulary)
* RAM:
* Grounding DINO
* SAM：
* LAMA:
* BLIP:
* [计算机图形学中的抽样技术](https://zhuanlan.zhihu.com/p/433247664)
* [MLS-MPM](https://github.com/yuanming-hu/taichi_mpm)
* Blendernerf: