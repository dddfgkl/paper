## Transformer-XL: Attentive Language Models
Beyond a Fixed-Length Context    
Transformer-XL作为Transformer的改进版本，对长文本处理有更好的效果，速度精度都有所提升  
论文链接:https://arxiv.org/pdf/1901.02860.pdf  

### 1、介绍     
LSTM的提出极大缓和了RNN网络的梯度弥散和爆炸问题，但是在处理长依赖问题上表现能力有限。Transformer的提出可以更好的抽取长期依赖的问题，在多项任务上达到state of the art的效果，
但是Transformer固有的形式是面对固定长度约几百个字符的段落语句，在不同段落语句之间是没有直接的信息传递的。这样的缺陷导致原始Transformer在面对更长的信息依赖的时候表现能力依旧不足。段落之间的信息沟壑论文中称作context fragmentation。
此外，vanilla Transformer在evaluation阶段，输入一个segment产出一个predict，当下一句evaluation，需要重新计算所有隐藏层，造成计算量很大。为了克服种种限制，作者提出Transformer-XL来解决相关问题。  

-----

### 2、方法&策略  
#### 1）training阶段  
- 骨架还是vanilla Transformer，但是在train的过程种缓存上一个segment的隐藏层，在对当前segment进行处理的时候，可以在self attention
计算过程种添加上一个缓存的隐藏层进行attention，这样就整合了多个segment的信息，attention在保证计算量的前提下，可以有更大的视野  

- 针对多个segment的attention，继续复用vanilla Transformer的position embeding机制就不合适了，论文提出使用relative position来代替absolute position，这样可以区分segment之间的位置信息  
  
#### 2）evaluation阶段  
前一segment的计算结果可以复用在当前segment的计算上，省去部分重复计算，减少计算量  



----


### 3、实验结果  
参看论文  

----

### 4、总结  
Transformer-XL相比vanilla Transformer提出的优化中，segment level的attention在保证了效率的前提小，减小了信息沟壑。后续可以用XLNet来做些实验  