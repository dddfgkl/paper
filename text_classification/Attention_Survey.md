# An Attentive Survey of Attention Models  
一个关于Attention机制的survey，内容比较全面，在这里简单整理一下  
下面的内容按照Attention的种类来进行划分  


## 一、Number of sequences  
按照sequence的数量来划分，因为我们经常见到的seq2seq模型都是1对1的，当然也是存在1对多，多对1的情况  


### 1、Distinctive   

### 2、Co-attention  


## 二、Number of abstraction levels   
按照信息抽取的层数来划分，多层Attention每一层都能抽到不同的信息   

### 1、Single-level   

### 2、Multi-level   


## 三、Number of positions   
按照Attention的位置来划分，Attention本身就是对多个位置的信息进行加权，但是也是有多种位置选择方式的  

### 1、Soft attention   
* NEURAL MACHINE TRANSLATION BY JOINTLY LEARNING TO ALIGN AND TRANSLATE  
首次将Attention机制应用于机器翻译，由此开启Attention在NLP领域的火热    
[LINK:] https://arxiv.org/pdf/1409.0473.pdf  


### 2、Hard attention  
* Show, Attend and Tell: Neural Image Caption Generation with Visual Attention  
这篇论文主要关注的是Image caption Generation，需要一些背景知识  
[LINK:]  https://arxiv.org/pdf/1502.03044.pdf  

### 3、