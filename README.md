# 基于中文维基百科文本数据训练词向量
## 一、数据获取

本词向量利用的是中文维基百科的语料进行训练。

语料地址：[Link](https://dumps.wikimedia.org/zhwiki/latest/zhwiki-latest-pages-articles.xml.bz2)（大小1.16G）

也可以在我的网盘上下载：
链接: [Pan](https://pan.baidu.com/s/16eS2730jyIZuLvpO0ZLV_w) 提取码: ihu4

## 二、数据转换

原数据的格式是xml，我们要将其转换为txt。

这里使用的是`gensim`自带的WikiCorpus，首先读取xml文件到`input_file`中，然后其中的`get_texts`方法会生成一个迭代器，每一个迭代蕴含了一篇文章，这样我们就可以将其写入新的txt文件中了。

## 三、繁体数据转换为简体数据

该Wiki数据是繁体中文数据，我们要把他们转换为简体中文数据。

利用`zhconv`包。

## 四、分词

利用结巴分词。

## 五、去除非中文词

一些词语中会包含非中文的词，我们要利用正则表达式将该词去除。

判断是否中文词的正则表达式为：`^[\u4e00-\u9fa5]+$`

## 六、词向量训练

利用`from gensim.models import Word2Vec`训练

训练完成词向量下载地址：[Link](https://pan.baidu.com/s/13a2ZXFf7ULJ6qQ2f72N3Dg) 密码:jvhn

# 效果展示

```python
model.similar_by_word('汽车', topn=5)
```

```
[('轿车', 0.6613024473190308),
 ('卡车', 0.6038083434104919),
 ('商用车', 0.6000862717628479),
 ('摩托车', 0.599767804145813),
 ('雪佛兰', 0.5972775220870972)]
```

