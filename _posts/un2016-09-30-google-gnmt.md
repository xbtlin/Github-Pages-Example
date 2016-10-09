---
layout:     谷歌的神经机器翻译系统GNMT
title:      HTML/CSS/JS学习笔记
category: blog
description: 介绍谷歌的神经机器翻译系统，依据谷歌发的论文
---

## 摘要   
神经机器翻译（NMT）是自动翻译中端对端的学习方法，将克服传统基于短语翻译系统的诸多弊病。不幸的是，NMT系统的训练和翻译过程都需要大量的计算。有些学者说NMT系统缺乏鲁棒性，特别是输入句子包含生词时。这些问题阻碍了NMT的实际应用。Google的GNMT解决了这些问题。GNMT由一个包含8个编码器、8个解码器的深度LSTM网络构成。为了提高并行性，GNMT将解码器的底层和编码器的顶层连接。GNMT在翻译时使用低精度算法(low-precision arithmetic)提高速度。为了提高生词的处理能力，GNMT在输入输出中将单词分成常用子词单元（sub-word unit，又称wordpieces）集合。    


读之前先看看RNN和LSTM。