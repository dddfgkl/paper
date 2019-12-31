##  How to Fine-Tune BERT for Text Classification?  
如何在文本分类任务上fine-tune Bert  
[论文链接https://arxiv.org/pdf/1905.05583.pdf] 

-------- 
### 1、介绍  
作者介绍了一下各种可用于文本分类的方法，比如word2vec、GloVe、sentence embeding.Bert在
文本分类任务上大放异彩，但是Bert的潜力还没有被完全发掘出来，所以作者提出几种fine-turning方法
去增强Bert的性能
    
本文的贡献如下：  
- 提出一种针对Bert的通用fine-tune技术。主要包括三个步骤:   
(1)在任务相关或者领域相关的训练集上继续train Bert模型，注意此处不是fine-tuning   
(2)在相关任务上，通过多任务学习优化Bert   
(3)针对特定任务fine-tuning Bert模型    

- 研究测试上述fine-tuning技术对Bert在长文本任务、隐藏层选择、隐藏层学习率、知识遗忘、少样本学习问题上的影响  

- 在各种数据集上取得start-of-the-art的效果  

------
### 2、方法论  
#### 1）Fine-Tuning 
Bert中不相同层表示着不同的语义和句法信息，如果针对不同的任务选择不同的层作为特征？选择什么优化方法和学习率最好？  
#### 2）Further Pre-training 
Bert在pre-train阶段利用了大量无监督语料，但是这些语料往往和要预测的任务不相关。数据分布也有可能和目标任务数据分布
不同，所以在目标任务的数据集上继续pre-train,是一个很自然的想法  
#### 3）Multi-Task Fine-Tuning  
pre-train模型没有兴起之前，多任务学习已经证明了它在利用不同任务相同知识的优异性能，多任务学习显然对pre-train模型也会有帮助  

-----
### 3、策略  
针对2中列出的方法论，这部分详细描述在具体任务中该如何执行  
#### 1）Fine-Tuning  
- 神经网络不同层学习到的表示是不一样的，作者在应对目标任务时，选取不同层作为特征测试分类效果。  
- Bert最长只能输入512字符的文本，对于长文本来说，如果作出对应处理。作者提出使用文本前512个字符、后512个字符、前后拼接512个字符，文本分段取平均的sentence embeding四种方法
测试分类效果，发现取后512个字符效果最佳，具体数据可以看论文  

#### 2）Further Pre-training  
没啥好说的，利用domain data继续Bert训练，训练目标还是预测mask和下一个句子,但是继续pre-train的代价也是比较大的    

#### 3） Multi-Task Fine-Tuning  
为了更好的集成多个任务学习到的共同知识，所有任务共享Bert layer和embeding layer，但是不共享最后的分类层  

------

### 4、实验结果  
具体看论文

------

### 5、总结  
三种策略对Bert性能还是有提升的，需要关注的有以下几点：
- 对于长文本的处理  
- 多任务学习共享底层知识  
- 领域数据继续train模型  
- 针对Catastrophic Forgetting作出的优化 
- Bert各层学习的表示对任务有什么贡献   

-----  
后续Todo

