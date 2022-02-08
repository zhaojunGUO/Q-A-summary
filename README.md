# Q-A-summary 汽车大师问答与推理任务
详情请见百度千言https://aistudio.baidu.com/aistudio/competition/detail/3

## Data processing
1.导入数据，处理空值 \n
2.去除无用符号 \n
3.使用jieba分词，然后去除停用词 \n
4.使用word2vec训练 \n
5.merge数据，只使用问答部分的数据，然后padding \n
6.填充字段：填充< unk > ,判断是否在vocab中, 不在填充 < unk >；填充< start > < end >； 判断长度，填充　< pad > \n
7.再次词表更新，需要再训练一次word2vec model后重新获取embedding matrix \n
8.sentence的数值转换 \n
## Modeling
### Seq-Seq model（simple）
### Seq-Seq model with attention
### Seq-Seq model with Pointer-Generator Networks
