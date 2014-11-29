---
layout: post
title: Text Similarity
excerpt: "A note in several natural language processing methods"
modified: 2014-8-8
tags: [LSA, VSM]
comments: true
---
<section id="table-of-contents" class="toc">
  <header>
    <h3>Overview</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->

##分词基本方法

###最大匹配法

先设定最大词长，从原预料中左边依次选择候选词集，判断是否在词典中，若在则加入输出，若不在，则重复删除该词的右一位置，重复进行，直到其成为单字或者在语料库存在时候为止。(是一种从maxlength to 0的步骤)

- 正向最大匹配法
- 逆向最大匹配法（对汉语来说更加有效）
- 双向匹配法（Bi-direction matching method，比较前两者的结果再决定怎么办）
- 最佳匹配法（OM法）

	将词典中的单词按照在文本中出现频率大小排列，提高匹配速度。
- 联想-回溯法

###最大概率法

将一个待切分的汉字串中概率最大的分词结果作为总结果，相当于是查询语料库里面的频率数，然后利用贝叶斯独立分布的累加性质得到出现概率，并进行比较。

###最短路径法

选择词数最少的分词方法。

###分词歧义分类

- 交集型（不同分法分出来的都是词典中的词）
- 组合型（总和和个别都是词典中的词汇）
- 混合型（人才能）

最大匹配法能发现部分交集型歧义，但无法发现组合型歧义

	分词歧义的四个层级（何克抗 等1991，50883字语料）
	词法歧义（84.1%）句法（10.8%）词义（3.4%）语用（1.7%）
	真假歧义
	真歧义（6%确实能在真实语料库中发现多重切法）假歧义（94%虽然有多种切分可能，但在真实语料库中往往只取其中一种切分形式）



###未登录词识别方法

	人名，地名，机构名，专业术语|数字识别（正则表达）|形式词，离合词
	一般用规则或是概率统计的方法解决
	基于标注的方法	

	对汉字进行标注，由字构词
	学习方法包括：
	支持向量机（SVM）最大熵（Maximum Entropy）隐马模型（HMM）最大熵隐马模型（MEMM）条件随机场（CRFs）

###词性标注

基于概率统计和基于规则

##停用词与词形变化


##文档模型与相似度计算

###布尔模型

非0即1的权重分配
扩展为p-norm模型（Salton et al. 1983）

###向量空间模型(VSM)

将文档表示为向量空间中的一个矢量或一个点
空间维（坐标轴）-> 词
权重表示了重要性

- 存在反例，没用的词出现的词数太多，有用无用无法在一个文档中被明确区分
- 引入了**term frequency（tf）** 其基本理念为，当一个词汇在一份文档中出现的词数越多，那么这个词汇将更能够比较好的区分这份文档的内容

		T=tf/doc_length	T=tf/maxtfa

- 引入了**inverse document frequency（idf）**的概念，当某个词汇在文档集中的多个文档中都出现了，则说明这个词汇的分辨性能力并不算优。

- Document frequency（df）：包含某个词汇的文档的数目

		idf=I=log（N/df）+1
		一般会正规化到[0..1]的范围内，即
		I=log(N+0.5/df)/log(N+1.0)

- 总的在一起来看
		TDIDF=TF*IDF

####相关度的度量

相关度可以用来表示文档间，问句间，或者是文档和问句间的相关度。相似度衡量即是用以计算成对文本对象相似度的函数。

####基于VSM的相关度计算方法

空间两点间的欧式距离（少用）

向量内积相似度

余弦相似度（在大量计算相似度时，应先对文档向量进行单位化）

- 余弦相似度的应用

		Smart retrieval system

		G. Salton, C. Buckley, Term weighting approaches in automatic text retrieval. InformationProcessing and Management 24(5):513–523, 1988

Jaccard相似度

####对VSM的总结

- 仅仅建立在出现频率数目上
- 考虑了局部和全局的出现频率
- **优点**

		简单
		可处理带权重的检索词
		容易修改检索词向量

- **缺点**

		其假设是检索词之间都是互相独立的
		缺乏对布尔模型的控制（检索词必须要出现在对应的文档中才能有效工作）


###概率模型

待补充

##特征变换

###隐语意分析（LSA）

问题提出：一词多义和同义词

中心思想：用概念（或特征）代替词

基本方法：利用矩阵理论中的『奇异值分解』技术将**词频矩阵转化为奇异矩阵**（K*K）

	Introduced in 1990; improved in 1995
	S. Deerwester, S. Dumas, G. Furnas, T. Landauer, R. Harsman: Indexing by latent semantic analysis, J. American Society for Information Science, 41, 1990, pp. 391-407
	M. W. Berry, S.T. Dumas, G.W. O’Brien: Using linear algebra for intelligent information retrieval, SIAM Review, 37, 1995, pp. 573-595
	Based on spectral analysis of term-document matrix

- 输入： term-by-document matrix

- 输出： 

	U:concept-by-term matrix
	V:concept-by-document matrix
	S:elements assign weights to concepts(SVD分解的对角矩阵 K*K)

对于每一个文档d，用排除了SVD中消除后的词的新的向量替换原有的向量

用转换后的文档索引和相似度计算

基本思想的背后逻辑：直接选维度进行计算，在一维或者二维的层面上，最近的值是不一样的。而若是对坐标轴进行过了旋转之后，进行选维，可以达到比较统一的相似度rank


Rows of Uk = terms
Rows of Vk = documents
<!-- create time: 2014-08-02 18:44:05  -->

