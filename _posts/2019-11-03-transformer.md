---
title: attention与transformer的一些细节问题
layout: post
categories: 'Machine Learning'
tags: ''
---

初衷是先写个seq2seq+attention，其实很简单，大家都[整理过](https://zhuanlan.zhihu.com/p/40920384)，所以决定开这篇查缺补漏性质的博文，和transformer一起写了。<br>

### seq2seq解码器的求解方法<br>
1.贪心法，每次输出概率最大的那个单词，但这样无法保证最终整体概率最大。<br>

2.Beam Search，每一步都选取概率最大的k个结果，在下一步结合上一步的不同结果继续选出k个最高得分。最后，选取概率最高的序列作为输出序列。也无法保证最终整体结果为最优，但保证了效率。

### 为何提出transformer
RNN特点：每一时刻依赖上一时刻的输出，可以捕获较远距离的关系但无法并行<br>

CNN：每一层中可以并行，但是在浅层只能捕捉到较临近的元素之间的关系<br>