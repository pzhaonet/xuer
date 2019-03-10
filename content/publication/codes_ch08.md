+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-10"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第八章 习题）"
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

## 第八章 习题

```
x <- c(1, 1, 2, 2, 3)  # 生成一个向量。
is.character(x)  # x 是字符型吗？不是。
is.numeric(x)  # x 是数值型吗？是的。
mode(x)  # 确实是数值型。

y <- c(3, 4, 4, 5, 5)
z <- c(x, y)  # 多个向量并在一起。
z
z[4]  # 向量的下标。

# 生成一个矩阵，指定行数和列数：
m <- matrix(c(2, 3, 1, 5), nrow = 2, ncol = 2)
m
# 生成一个矩阵，指定行数：
m <- matrix(c(2, 3, 1, 5), nrow = 2)
m
# 生成一个矩阵，指定行数，并按行排列：
m <- matrix(seq(1, 20, 1), nrow = 5, byrow = TRUE)
m
# 生成一个矩阵，指定行数，并按列排列：
m <- matrix(seq(1, 20, 1), nrow = 5, byrow = FALSE)
m[2, 2]  # 矩阵的下标。

a <- c(1, 2, 3, 4)
b <- seq(5, 8, by = 1)
d <- data.frame(a, b)  # 生成一个数据框。
d
is.data.frame(d)  # 是数据框吗？
str(d)  # 数据框的结构。
class(d) 
nrow(d) # 数据框的行数。
ncol(d) # 数据框的列数。
e <- c(9, 10)
f <- rbind(d, e)  # 给数据框增加一行。
f
g <- c("one", "two", "three", "four", "five")
class(g)
h <- cbind(f, g)  # 给数据框增加一列。
h
class(h)
ncol(h)
colnames(h) <- c("one", "two", "three")  # 更改列名称。
h

is.numeric(d[, 1])
is.data.frame(d[1, ])
is.numeric(d[1, ])
is.numeric(unlist(d[1, ]))
mylist <- list(x = 1:4, y = letters[3:10])
mylist
mylist[[1]]
mylist[[1]][1]
mylist[[2]]
mylist[[2]][5]
mylist$x
mylist$y[3]
```
