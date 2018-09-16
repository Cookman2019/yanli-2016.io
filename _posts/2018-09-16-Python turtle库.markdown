---
layout:     post
title:      "Python turtle 库"
subtitle:   ""
date:       2018-09-16
author:     "YanSir Park"
header-img: "img/post-bg-js-version.jpg"
tags:
    - Python
    - Python库
---

# Python turtle 库

## 基本操作

### turtle.goto

```
import turtle
turtle.goto(100, 100)
turtle.goto(100, -100)
turtle.goto(-100, -100)
turtle.goto(-100, 100)
turtlr.goto(0,0)
turtle.done
```

## 应用示例

### 绘制蟒蛇

```
import turtle
turtle.setup(650, 350, 200, 200)
turtle.penup()
turtle.fd(-250)
turtle.pendown()
turtle.pensize(25)
turtle.pencolor("purple")
turtle.seth(-40)
for i in range(4):
    turtle.circle(40, 80)
    turtle.circle(-40, 80)
turtle.circle(40, 80/2)
turtle.fd(40)
turtle.circle(16, 180)
turtle.fd(40 * 2/3)
turtle.done
```

### 绘制正方形

```
import turtle
turtle.setup(500, 500, 10, 10)
turtle.penup()
turtle.goto(0, -200)
turtle.pendown()
turtle.pensize(10)
for i in range(4):
    turtle.fd(400)
    turtle.left(90)
turtle.done
```

### 绘制叠边形

```
import turtle
turtle.setup(500, 500, 10, 10)
turtle.penup()
turtle.goto(-100, -100)
turtle.pendown()
turtle.pensize(10)
for i in range(9):
    turtle.fd(100)
    turtle.left(80)
turtle.done

```

### 绘制同心圆

```
import turtle
turtle.setup(500, 500, 10, 10)
turtle.penup()
turtle.goto(0, -100)
turtle.pendown()
turtle.pensize(10)
for i in range(1,5):
    turtle.circle(i * 25, 360)
turtle.done
```

### 绘制同切圆

```
import turtle

turtle.pensize(2)
turtle.circle(10)
turtle.circle(40)
turtle.circle(80)
turtle.circle(160)
```
### 绘制五角星

```
from turtle import *
color('red','red')
begin_fill()
for i in range(5):
    fd(200)
    rt(144)
end_fill()
done()
```






