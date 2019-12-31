## Multi-passage BERT: A Globally Normalized BERT Model for Open-domain Question Answering  
主要为了借鉴其中对长文本的处理  
论文连接https://arxiv.org/pdf/1908.08167.pdf  

-----

### 1、介绍  
Bert在reading comprehension(RC)领域霸榜，RC是简化版本的Question Answering(QA)，RC只需要从一个给定的段落、片段出给问题答案即可，但是现实中，
开放域QA系统需用从大量文章中准确抽取出问题的答案，比如从整个wiki资料库或者因特网中寻求答案    

------

### 2、方案论&策略  
#### 1）问题定义  
给定question Q，召回方法召回数个候选passage P，从P中抽取问题答案a，问题可以分解为预测答案a的start position和end postion概率问题  

#### 2）方案  
- 原始的方法是将Q和P构建多个pair对，利用encode每一个vector representation输入到独立的两个全连接层分别预测Ps(开始位置概率)和Pe(结束位置概率)。这样的构造形式有个问题是对应同一个question Q,多个answer是独立的，通过网络生成的scores很有可能不具备可比性，因为模型没有学习到passage之间关联。对应这样的问题，作者提出使用global normalization method来处理。前期处理都是独立的，只有到最后通过一个normalization来规范针对同一个question Q的多个P
之间的关系  
- 关于对整个article的处理，作者使用滑动窗口来split整个article来提升模型性能    
- passage ranker的做法类似上面的做法，只不过预测一个score，具体看论文   
- inference阶段选择得分最高的作为answer  


----

### 3、总结    
针对文本分类任务中，对于长文本的处理能够借鉴的地方:  
- 对长文本进行滑窗split多个passage,但是也有可能存在对于同一个文本出来的passage分数分布不能直接对比，可以考虑global normalization，inference阶段选最高的  
- 但是有个问题是按照论文方法来做，这个给网络训练带来了比较大的问题，如何进行GN    


-----

### Reference  
[1 https://arxiv.org/pdf/1908.08167.pdf   



