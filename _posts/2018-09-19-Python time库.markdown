---
layout:     post
title:      "Python time 库"
subtitle:   ""
date:       2018-09-19
author:     "YanSir Park"
header-img: "img/post-bg-js-version.jpg"
tags:
    - Python库
---

# Python time 库


## 计算机的时间

```
import time
a = time.time()  #时间戳
b = time.ctime()
c = time.gmtime()
d = time.strftime("%Y-%m-%d %H:%M:%S",c)
timestr = '2018-07-08 12:55:20'
e = time.strptime(timestr, "%Y-%m-%d %H:%M:%S")
print(a)
print(b)
print(c)
print(d)
print(e)
```

## 计时操作

```
import time
start = time.perf_counter()
end = time.perf_counter()
inter = end - start
print(start)
print(end)
print(inter)
```

## 延时操作

```
import time
def wait():
    time.sleep(3.3)
wait()
print("时间的延时操作")
```

## 应用示例

### 文本进度条


```
import time
scale = 10
print('------执行开始------')
for i in range(scale+1):
    a = '*'*i
    b = '.'*(scale-i)
    c = (i/scale)*100
    print("{:^3.0f}%[{}->{}]".format(c, a, b))
    time.sleep(0.1)
print('------执行结束------')
```

### 单行动态刷新

```
import time
for i in range(101):
    print("\r{:3}%".format(i), end = "")
    time.sleep(0.1)
```
