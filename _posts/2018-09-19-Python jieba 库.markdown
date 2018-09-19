---
layout:     post
title:      "Python jieba 库"
subtitle:   ""
date:       2018-09-19
author:     "YanSir Park"
header-img: "img/post-bg-js-version.jpg"
tags:
    - Python库
---

# Python jieba 库


## jieba库

1. 精确模式，最常用
2. 全模式，有冗余
3. 搜索模式，在精确模式的基础上，多长句进行切分

## jieba库常用函数

1. jieba.lcut(s):精确模式，返回一个列表类型的分词结果
2. jieba.lcut(s, cut_all = True): 全模式，返回一个列表类型的分词结果，存在冗余
3. jieba.lcut_for_search(s): 搜索引擎模式，返回一个列表类型的分词结果，存在冗余
4. jieba.add_word(w): 向分词词典增加新词w

```
import jieba
print(jieba.lcut("三国演义是一部很伟大的著作"))
print(jieba.lcut("三国演义是一部很伟大的著作", cut_all = True))
print(jieba.lcut_for_search("三国演义是一部很伟大的著作"))
```

## 应用示例

### 文本词频统计_hamlet

```
import jieba
def getText():
    txt = open("hamlet.txt","r").read()
    txt = txt.lower()
    for ch in '!"#$%&()*+,-./:;<=>?@[\\]^_‘{|}~':
        txt = txt.replace(ch, " ")
    return txt

hamletTxt = getText()
words = hamletTxt.split()
counts = {}
for word in words:
    counts[word] = counts.get(word, 0) + 1
items = list(counts.items())
items.sort(key=lambda x:x[1],reverse=True)
for i in range(10):
    word, count = items[i]
    print("{0:<10}{1:>5}".format(word,count))
```

### 分析三国演义中人物出场频率

```
import jieba
txt = open("threekingdoms.txt","r",encoding = "utf-8").read()
words = jieba.lcut(txt)
counts = {}
for word in words:
    if len(word) == 1:
        continue
    else:
        counts[word] = counts.get(word,0)+1
items = list(counts.items())
items.sort(key = lambda x:x[1], reverse = True)
for i in range(15):
    word, count = items[i]
    print("{0:<10}{1:>5}".format(word, count))
```

分析三国演义中人物的出场频率_plus

```
import jieba
txt = open("threekingdoms.txt","r",encoding = "utf-8").read()
excludes = {"将军","却说","荆州","二人","不可","不能","如此","商议","如何","主公","军士","军马","左右","引兵","次日"}
words = jieba.lcut(txt)
counts = {}
for word in words:
    if len(word) == 1:
        continue
    elif word == "诸葛亮" or word == "孔明曰":
        rword = "孔明"
    elif word == "关公" or word == "云长":
        reword = "关羽"
    elif word == "玄德" or word == "玄德曰":
        reword = "刘备"
    elif word == "孟德" or word == "丞相":
        rword = "曹操"
    else:
        rword = word
    counts[rword] = counts.get(rword,0)+1
for word in excludes:
    del counts[word]
items = list(counts.items())
items.sort(key = lambda x:x[1], reverse = True)
for i in range(5):
    word, count = items[i]
    print("{0:<10}{1:>5}".format(word, count))
```
