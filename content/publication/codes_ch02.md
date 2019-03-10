+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-15"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第二章 数据）"
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

## 第二章 数据

```
dir.create('c:/r4r')
write.csv(as.data.frame(t(matrix(
  co2, 12, dimnames = list(
    month.abb, unique(floor(time(co2))))))),
   file = 'c:/r4r/co2.csv')

mydata1 <- read.table(file = "clipboard", header = TRUE)
mydata1

myfile1 <- file.choose()

myfile1 <- "c:/r4r/co2.csv"
myfile1
myfile2 <- "c:/r4r/co2.csv"
myfile2

file.show(myfile2) # 查看文件

mydata2 <- read.table(file = myfile2, 
                      header = TRUE, sep = ",")
mydata2

mydata2 <- read.csv(file = myfile2)

mydata2 <- read.csv(file = "c:/r4r/co2.csv")

plot(mydata2)

summary(mydata2)

mydata2[37, 10]

mydata2[c(2, 4, 6, 8, 10, 12, 14, 16, 18, 20,
          22, 24, 26, 28, 30, 32, 34, 36, 38), 10]

mydata2[seq(from = 2, to = 39, by = 2), 10]

mydata2[2:39, 10]

mydata2[, 10]  # 第10列全部。

mydata2[37, ]  # 第37行全部。

mydata2[, 'Sep']

mydata2$Sep

names(mydata2) # 或 colnames(mydata2)
names(mydata2)[1] <- 'year'
names(mydata2)

rownames(mydata2)
rownames(mydata2) <- mydata2$year
rownames(mydata2)

mydata2['1995', 'Sep']

sum(mydata2['1995', 2:13]) / 12

sum(mydata2['1996', 2:13]) / 12 - 
  sum(mydata2['1995', 2:13]) / 12

mydata2['1996', ] - mydata2['1995', ]

colMeans(mydata2[, 2:13]) # 排除掉第一列后，对整列求平均

mydata2$mean <- rowMeans(mydata2[, 2:13])

mydata2$median <- apply(X = mydata2[, 2:13], 
                        FUN = median, MARGIN = 1)

diff(mydata2$Sep)
```
