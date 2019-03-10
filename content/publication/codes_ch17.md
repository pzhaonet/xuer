+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-01"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十七章 用 R 进行基础统计（一）：概率分布检验）"
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

## 第十七章 用 R 进行基础统计（一）：概率分布检验

```
binom.test(x = 27, n = 60, p = 0.5, alternative = "less")
binom.test(x = 203, n = 558, p = 0.4, alternative = "less")
binom.test(x = 203, n = 558, p = 0.4, alternative ="greater")

poisson.test(13,15) 
poisson.test(13,24,alternative="less")

qpois(0.95,lambda =24)
qpois(0.05,lambda =24)

x <- 0:6
y <- c(7, 10, 12, 8, 3, 2, 0)
mean <- mean(rep(x, y))
q <- ppois(x, mean)
n <- length(y)
p <- q
p[1] <- q[1]
p[n] <- 1 - q[n - 1]
for(i in 2:(n - 1))
  p[i] <- 1 - q[i - 1]
chisq.test(y, p = rep(1/length(y), length(y)))

myfreq<-c(30,21,24,35,42,48) # 得到的频数
myprobs<-c(1,1,1,1,1,1)/6 # 指定的概率分布
chisq.test(myfreq,p=myprobs)

par(mfcol=c(1,2),ps=6.5)
hist(AirPassengers,breaks=20)
qqnorm(AirPassengers,pch=1)
shapiro.test(AirPassengers)

par(mfcol=c(1,2),ps=6.5)
hist(lh,breaks=20)
qqnorm(lh,pch=1)
shapiro.test(lh) #人群血样中促黄体浓度属于正态分布吗？

A <- rnorm(100,5,3) 
ks.test(A,5,3) 
ks.test(A,15,1) 
set.seed(1)
mydata <- rexp(950)
ks.test(mydata, "pexp")
set.seed(1)
mydata <- rgamma(1500,1)
ks.test(mydata, "pgamma", 1)
ks.test(mydata, "pgamma", 2)
set.seed(1)
mydata<-rweibull(8500,1)
ks.test(mydata, "pweibull", 1)
ks.test(mydata, "pweibull",2)
ks.test(co2[1:12],co2[97:108],alternative ="two.sided")
qnorm(0.025)
qnorm(0.975)
```
