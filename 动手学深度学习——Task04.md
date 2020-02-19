#### 一.机器翻译及相关技术
机器翻译（MT）主要特征：输出是单词序列而不是单个单词。 输出序列的长度可能与源序列的长度不同。
#### 二.注意力机制与Seq2seq模型
待续
#### 三.Transformer
Transformer同样基于编码器-解码器架构，其区别主要在于以下三点：
Transformer blocks：将seq2seq模型重的循环网络替换为了Transformer Blocks，该模块包含一个多头注意力层（Multi-head Attention Layers）以及两个position-wise feed-forward networks（FFN）。对于解码器来说，另一个多头注意力层被用于接受编码器的隐藏状态。
Add and norm：多头注意力层和前馈网络的输出被送到两个“add and norm”层进行处理，该层包含残差结构以及层归一化。
Position encoding：由于自注意力层并没有区分元素的顺序，所以一个位置编码层被用于向序列元素里添加位置信息。
