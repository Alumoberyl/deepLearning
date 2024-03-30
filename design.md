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
## COGLOAD
  > https://github.com/MartinGjoreski/martingjoreski.github.io/blob/master/files/CogDatasets.rar
## MOCAS
  > https://polytechnic.purdue.edu/ahmrs/mocas-dataset
## WESAD
  > https://ubicomp.eti.uni-siegen.de/home/datasets/icmi18/
# 待选数据集
<div>
  <img src="/datasets.jpg" width="800" /> 
</div align=center>
# 设计思路 
## 1. 样本为1个人、1首歌、2秒、128Hz、c通道  
  (1,1,2,128,c)：1个人1首歌60/2=30个样本->1个人40 * 30=1200个样本
  (256,32)进行一次transformer 也就是256个1 * 32长度的token进行注意力计算
## 2. 
