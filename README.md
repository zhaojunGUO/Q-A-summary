# Q-A-summary 汽车大师问答与推理任务
详情请见百度千言https://aistudio.baidu.com/aistudio/competition/detail/3

## Data processing
1.导入数据，处理空值   
2.去除无用符号  
3.使用jieba分词，然后去除停用词  
4.使用word2vec训练  
5.merge数据，只使用问答部分的数据，然后padding  
6.填充字段：填充< unk > ,判断是否在vocab中, 不在填充 < unk >；填充< start > < end >； 判断长度，填充　< pad >  
7.再次词表更新，需要再训练一次word2vec model后重新获取embedding matrix  
8.sentence的数值转换  
![wordcloud](https://user-images.githubusercontent.com/64532223/153080109-88c05b0c-78d8-4106-9ba2-36e5f5e4a3b2.png)

## Modeling
### Seq-Seq model（simple）
模型笔记如下
[Sequence to Sequence 模型笔记.md](https://github.com/zhaojunGUO/Q-A-summary/files/8043408/Sequence.to.Sequence.md)

### Seq-Seq model with attention
[Sequence to Sequence 模型笔记.md](https://github.com/zhaojunGUO/Q-A-summary/files/8043408/Sequence.to.Sequence.md)

### Seq-Seq model with Pointer-Generator Networks
