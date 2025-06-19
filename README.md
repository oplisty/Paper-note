# Paper-note
# All PPT note will be place in PPT folder
### Video inpating
* **RGVI**
  * 
### 造数据
* **DreamGen**:
  * **Latent Action Pretraining from Videos**:潜动作模型
  * **Video PreTraining (VPT): Learning to Act by Watching Unlabeled Online Videos**:逆动力模型
  * **LoRA**:微调
### 方法类型
* **R3M**:先训一个visual representation，输入RGB利用他得到state，再做模仿学习。
  * 在足够diverse的数据上训练来增强泛化性
  * 为机器人操作相关的特征提供有用的signal
* **Ag2Manip**:
  *  将视频中的人体手臂割掉再恢复视频再用R3M学习表征
     *  对于遮挡怎么办？(RGVI)
  * 对于强化学习操作，可以分为两个阶段
    * 探索阶段
      * 可交互阶段的检测
    * 可交互阶段的操作