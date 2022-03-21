Title: python3 nltk chapter 1
Date: 2018-11-10 18:17:07
Category: nltk
Tags: python, nltk
Slug: python-nltk-chapter1

# 语言处理与Python

### 1.语言计算：文本和单词

##### 1.2 NLTK 入门
```
import nltk
nltk.download()
```

##### 1.3 搜索文本
```
text1.concordance("monstrous")  # 搜索文本

text1.similar("monstrous")  # 查看相识上下文出现的单词

text2.common_contexts(["monstrous", "very"])  # 查找两个词的共同上下文

text4.dispersion_plot(["citizens", "democracy", "freedom", "duties", "America"])  # 词汇分布图

len(set(text3)) / len(text3)  # 文本词汇丰富度
```

##### 1.3 布朗语料库
```
from nltk.corpus import brown
brown.categories()
brown.words(categories='news')
brown.words(fileids=['cg22'])
brown.sents(categories=['news', 'editorial', 'reviews'])
```
##### 1.4 路透社语料库
```
from nltk.corpus import reuters
reuters.fileids()
reuters.categories()
reuters.categories('training/9865')
reuters.categories(['training/9865', 'training/9880'])
reuters.fileids('barley')
reuters.fileids(['barley', 'corn'])
```
##### 1.5 就职演说语料库
```
from nltk.corpus import inaugural
inaugural.fileids()
```

##### 1.6 标注文本语料库
http://nltk.org/data
http://nltk.org/howto


##### 1.7 其他语言的语料库
nltk.corpus.udhr  # 超过300种语言的世界人权宣言

##### 1.8 文本语料库的结构

###### NLTK 中定义的基本语料库函数, 使用help(nltk.corpus.reader)可以找到更多的文档
```
示例                       描述                          
fileids()                  语料库中的文件                
fileids([categories])      这些分类对应的语料库中的文件  
categories()               语料库中的分类                
categories([fileids])      这些文件对应的语料库中的分类  
raw()                      语料库的原始内容              
raw(fileids=[f1,f2,f3])    指定文件的原始内容            
raw(categories=[c1,c2])    指定分类的原始内容            
words()                    整个语料库中的词汇            
words(fileids=[f1,f2,f3])  指定文件中的词汇              
words(categories=[c1,c2])  指定分类中的词汇              
sents()                    整个语料库中的句子            
sents(fileids=[f1,f2,f3])  指定文件中的句子              
sents(categories=[c1,c2])  指定分类中的句子              
abspath(fileid)            指定文件在磁盘上的位置        
encoding(fileid)           文件的编码（如果知道的话）    
open(fileid)               打开指定语料库文件的文件流    
root                       本地安装的语料库根目录的路径  
readme()                   语料库的README文件的内容
```
##### 1.9 加载你自己的语料库
```
from nltk.corpus import PlaintextCorpusReader
corpus_root = '/usr/share/dict' [1]
wordlists = PlaintextCorpusReader(corpus_root, '.*') [2]
wordlists.fileids()
```

```
from nltk.corpus import BracketParseCorpusReader
corpus_root = r"C:\corpora\penntreebank\parsed\mrg\wsj" [1]
file_pattern = r".*/wsj_.*\.mrg" [2]
ptb = BracketParseCorpusReader(corpus_root, file_pattern)
ptb.fileids()
```

### 2 条件频率分布

##### 2.1 条件和事件
##### 2.2 按文体计数词汇
```
from nltk.corpus import brown
cfd = nltk.ConditionalFreqDist(
          (genre, word)
          for genre in brown.categories()
          for word in brown.words(categories=genre))

cfd  # <ConditionalFreqDist with 2 conditions>
cfd.conditions()  # ['news', 'romance']

print(cfd['news'])
# <FreqDist with 14394 samples and 100554 outcomes>

print(cfd['romance'])
<FreqDist with 8452 samples and 70022 outcomes>

cfd['romance'].most_common(20)

cfd['romance']['could']
# 193
```

##### 2.3 绘制分布图和分布表
```
cfd.tabulate(conditions=['English', 'German_Deutsch'],
             samples=range(10), cumulative=True)

cfd.plot(conditions=['English', 'German_Deutsch'],
         samples=range(10), cumulative=True)
```


##### 2.4 使用双连词生成随机文本
条件频率分布是一个对许多NLP 任务都有用的数据结构。2.1总结了它们常用的方法。
```
示例                                 描述
cfdist=ConditionalFreqDist(pairs)    从配对列表中创建条件频率分布                       
cfdist.conditions()                  条件
cfdist[condition]                    此条件下的频率分布
cfdist[condition][sample]            此条件下给定样本的频率
cfdist.tabulate()                    为条件频率分布制表
cfdist.tabulate(samples,conditions)  指定样本和条件限制下制表
cfdist.plot()                        为条件频率分布绘图
cfdist.plot(samples,conditions)      指定样本和条件限制下绘图
cfdist1<cfdist2                      测试样本在cfdist1中出现次数是否小于在cfdist2中出现次数
```

### 3 更多关于Python：代码重用
### 4 词汇资源

