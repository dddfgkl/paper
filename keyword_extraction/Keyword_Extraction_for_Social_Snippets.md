## Keyword Extraction for Social Snippets  
[LINK:]http://ramb.ethz.ch/CDstore/www2010/www/p1143.pdf  
[Desc:]2010的一篇文章，比较老了而且很短简单看看各种方法之间的比较，论文里面并没有直接阐述方法细节  

-----

### 一、介绍  

- 强调关键词抽取应用广很重要云云，略  

- 以前提出的keyword extraction方法更多的应用在传统文章中，但是今天的主角是很短的文本，例如twitter、微博等，
在这种短文本中提取关键词，对于广告、推荐等任务还是有很大用处的，同时，短文本的处理也带来了很多挑战    

---- 


### 二、方法 & 策略  
首先对短文本进行切分，通过unigram和bigram来生成候选的keyword集合。然后计算候选词的特征参数通过
一个分类器来提出得分最高的关键词候选  

通常来说有一下特征可选：  
#### 1、TFIDF   
这个是最常用的，但是在短文本中，这个feature效果有限，主要是因为短文本中的词频多为1    

#### 2、lin(linguistic feature)
多数情况下，名词相比其他词来说更可能是关键词，这个feature怎么计算论文中有自己查   
 
#### 3、pos(relative position)  
候选词在短文本中的相对位置  

#### 4、lenText(length of social snippet)  
词数，即为短文本长度  

#### 5、DF(document frequency)  
一个流行的词更可能是一个关键词    

#### 6、capital(capitalization)  
是够是大小写，是个二值特征，有可能全大写的更重要，看数据集  


###  

直接对候选集选top，对于短文本来说不太合理，因为有些短文本根本就没有关键词，所以这里
将top-p%候选词的最小值当作阀值来过滤   


-----

### 三、实验结果  
- TFTDF是一个很强的baseline  
- GBM效果很好  
具体看论文  

  


    