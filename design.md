# 数据集
## DEAP
  > https://www.eecs.qmul.ac.uk/mmv/datasets/deap/
### 数据维度
Array name|Array shape|Array contents
---|---|---
data|40 x 40 x 8064|40材料x(32EEG+2EOG+2EMG+1GSR+1呼吸率+1Plethysmograph+1温度)x(128Hzx63s)
labels|40 x 4|40材料xlabel(valence,arousal,dominance,liking)
> GSR: galvanic skin response 皮肤电反应  
> hEOG/vEOG: electrooculogram 眼电图,Eye Blink影响眼电图  
> zEMG: Zygomaticus Major EMG 颧大肌肌电图  
> tEMG: Trapezius EMG 斜方肌肌电图  
## COGLOAD (不好使用)
  > https://github.com/MartinGjoreski/martingjoreski.github.io/blob/master/files/CogDatasets.rar
## MOCAS
  > https://polytechnic.purdue.edu/ahmrs/mocas-dataset
> EEG
> EEG_POW(EEG band powers)
> EDA or GSR
> BVP
> EAR(Eye Aspect Ratio)
## WESAD
  > https://ubicomp.eti.uni-siegen.de/home/datasets/icmi18/
# 待选数据集
  <img src="/datasets.jpg" width="800" /> 

# 实验尝试
## Pairwise
  <img src="/result1.png" width="800" />

# 设计思路
## 1. DEAP数据集
### 可以结合CNN进行一定的特征提取降低数据维度
### ① 1个人、1首歌、2秒、128Hz、c通道  
  (1,1,2,128,c)：1个人1首歌60/2=30 -> 1个人40首歌 * 30=1200
  (256,c)进行一次transformer 也就是256个1 * 32长度的token进行注意力计算 
### ② 31个人、1首歌、1秒、128Hz、c通道
  (31,1,1,128,c): 31个人同一首歌 -> 40 
  (31 ,128 * c)进行一次transformer 31个128 * c(32~40)长度的token进行注意力计算
