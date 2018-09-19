---
layout:     post
title:      "Python Random 库"
subtitle:   ""
date:       2018-09-19
author:     "YanSir Park"
header-img: "img/post-bg-js-version.jpg"
tags:
    - Python库
---

# Python Random 库


## Random库

基本随机函数: 
1. seed()，初始化随机数种子，默认为系统时间,设定种子后，得到的随机数结果一样
2. random(),生成[0,1.0]之间的随机小数

扩展随机数函数: 
1. randint(a,b): 生成[a,b]之间的整数
2. getrandbits(k): 生成k比特长的随机整数
3. uniform(a,b):生成[a,b]之间的随机小数
4. randrange(m,n,k): 生成[m,n]之间以k为步长的随机整数
5. choice([1,2,3,4]): 从列表中随机选择一个元素
6. shuffle([1,2,3,4]): 将列表随机打乱后返回序列

## 应用示例

### 圆周率的计算

使用公式计算

```
pi = 0
N = 100
for k in range(N):
    pi = pi + 1/pow(16, k)*(4/(8*k+1)-2/(8*k+4)-1/(8*k+5)-1/(8*k+6))
print('圆周率的值是: {}'.format(pi))
```

使用蒙特卡罗方法计算

```
from random import random
from time import perf_counter
DARTS = 1000*1000
hits = 0.0
start = perf_counter()
for i in range(1, DARTS+1):
    x, y = random(), random()
    dist = pow(x**2+y**2, 0.5)
    if dist <= 1.0:
        hits = hits + 1
pi = 4 * (hits/DARTS)
print('圆周率的值是：{}'.format(pi))
print('运行时间是：{:5f}'.format(perf_counter() - start))
```


