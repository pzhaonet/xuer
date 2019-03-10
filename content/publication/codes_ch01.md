+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-16"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第一章 初见）"
url_pdf = ""

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = "My caption :smile:"

# 0 = Uncategorized
# 1 = Conference proceedings
# 2 = Journal
# 3 = Work in progress
# 4 = Technical report
# 5 = Book
# 6 = Book chapter
+++

## 第一章 初见

```
co2
summary(co2)

3 * (2 + 2)
9 ^ 0.5 # 开平方
sqrt(9)  # 也是开平方

pi

options(digits = 22)  # 最大支持 22 位
pi

options(digits = 7) 
pi

exp(1)  # 计算 e
e = exp(1) 
e <- exp(1)  
exp(1) -> e
e

x <- round(e)^2
x

x <- c(61, 45, 55, 46, 56, 79, 86, 57, 56, 56, 57, 71)
x

x[4]

y <- co2 # 转存
y[10] # 看看第十个数据

x + 100

plot(y)  # 作图

(x[1] + x[2] + x[3] + x[4] + x[5] + x[6] + x[7] + x[8] + 
   x[9] + x[10] + x[11] + x[12]) / 12  # 计算平均值
sum(x) / length(x)
mean(x)
summary(x)
```
