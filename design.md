# 数据集
## DEAP
  > https://www.eecs.qmul.ac.uk/mmv/datasets/deap/
### 数据维度
|Array name|Array shape|Array contents|
|data|40 x 40 x 8064|video/trial x channel x data|
|labels|40 x 4|video/trial x label (valence, arousal, dominance, liking)|
## COGLOAD
  > https://github.com/MartinGjoreski/martingjoreski.github.io/blob/master/files/CogDatasets.rar
## MOCAS
  > https://polytechnic.purdue.edu/ahmrs/mocas-dataset
## WESAD
  > https://ubicomp.eti.uni-siegen.de/home/datasets/icmi18/
# 设计思路
## 1. 样本为1个人、1首歌、2秒、128Hz、c通道  
  (1,1,2,128,c)：1个人1首歌60/2=30个样本->1个人40 * 30=1200个样本
  (256,32)进行一次transformer 也就是256个1 * 32长度的token进行注意力计算
## 2. 
