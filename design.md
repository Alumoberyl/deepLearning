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
### MOSEI数据集
  <img src="/result1.png" width="800" /> 

### IEMOCAP数据集
#### Neutral/Happy/Sad/Angry Epoch 20
|类型|F1|Acc|F1|Acc|F1|Acc|F1|Acc|
|:---:|---|---|---|---|---|---|---|---|
|对齐|0.6965|0.7100|0.8327|0.8603|0.8322|0.8272|0.8630|0.8582|
|非对齐|0.4742|0.5970|0.7896|0.8560|0.7031|0.7942|0.6570|0.7569|

#### Neutral/Happy/Sad/Angry Epoch 40
|类型|F1|Acc|F1|Acc|F1|Acc|F1|Acc|
|:---:|---|---|---|---|---|---|---|---|
|对齐|0.6689|0.6886|0.8327|0.8603|0.8322|0.8272|0.8630|0.8582|
|非对齐|||||||||
### MOSI数据集

# 设计思路
## 1.Private数据集
||3~11|30~38|0:53~1:01|1:19~1:27|
|---|---|---|---|---|
|时长|9s|9s|9s|9s|
|类型|伤心|紧张|紧张|愤怒|
|标签|0|1|1|2|
### EEG数据(9,128,14)
4个9秒长 以一秒为单位128Hz 14个通道 
### 面部点位坐标(9,30,134/201)(9,30,45)
4个9秒长 每秒30帧
270份 面部点位xyz轴 每个轴有67个参数 2D：134个 3D：201个
ActionUnit 45个

## 2.DEAP数据集
### 可以结合CNN进行一定的特征提取降低数据维度
40材料x(32EEG+2EOG+2EMG+1GSR+1呼吸率+1Plethysmograph+1温度)x(128Hzx63s)
40首歌 * (128Hz * 63秒) * 40C
##观察一下数据标签问题，四个标签怎么处理
### ① 1个人、1首歌、2秒、128Hz、c通道  
  必须先获知输入到网络里的数据是什么样子的，确定最终所需要的数据形状
  (1,1,2,128,c)：1个人1首歌60/2=30 -> 1个人40首歌 * 30=1200
  (256,c)进行一次transformer 也就是256个1 * 32长度的token进行注意力计算 
### ② 31个人、1首歌、1秒、128Hz、c通道
  (31,1,1,128,c): 31个人同一首歌 -> 40 
  (31 ,128 * c)进行一次transformer 31个128 * c(32~40)长度的token进行注意力计算
