## Simple Applications of BERT for Ad Hoc Document Retrieval  
这是一篇将Bert应用在信息检索(IR)领域的文章，主要为了借鉴里面对长文本的处理     
论文链接[https://arxiv.org/pdf/1903.10972.pdf]  

-----
### 1、介绍  
首先科普一下IR领域的两个名词:  
- Ad Hoc : Ad Hoc类似图书馆书籍检索，数据库相对稳定，但是用户查询千变万化。  
- routing : 与Ad Hoc相反，用户查询相对稳定，数据库动态变化。  

文章贡献:  
- 首次将Bert应用在IR领域，并取得start-of-the-art效果  
- 针对Bert如何处理长文本提出一些值得借鉴的方法  

Benchmark:   
- 数据集是 TREC Microblog Tracks  
- 评价指标为 AP  

-----  
### 2、方法论&策略  
- 由于大多数数据只有document-level的相关性标注，所以文章不讨论长文本在pre-train和fine-tuning阶段的利用，只关注inference阶段对长文本的处理  
- 针对短文本，对比QA，构造pair对来fine tuning模型，提高模型学习query和document之间的关系以及深层语义    
- 针对长文本，在inference阶段，选取得分top k的sentence来表征整个document，因为有研究任务整个document其实可以用数个内部sentence来表述   

---- 

### 3、总结  
值得借鉴的地方:  
- 对长文本的处理，选取top k sentence来描述整个document  
- todo  

问题:  
- 没想明白为啥需要插值求得分，如果选择插值求得分的话有点像ensemble，这样无法准备衡量Bert效果？  
- 








----

### Reference  
[1] https://blog.csdn.net/memray/article/details/41149633  
[2] https://www.jiqizhixin.com/articles/2019-06-10-7?from=synced&keyword=Bert  
[3] https://arxiv.org/pdf/1903.10972.pdf  



