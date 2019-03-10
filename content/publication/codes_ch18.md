+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-03-31"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十八章 用 R 进行基础统计（二）：均值比较和方差分析）"
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

## 第十八章 用 R 进行基础统计（二）：均值比较和方差分析

```
myco2<-co2[1:12]
myco2
t.test(myco2,mu=316.45)
myco2.t1 <- co2[1:12] # 1959年的观测数据
myco2.t2 <- co2[13:24] # 1960年的观测数据
t.test(myco2.t1,myco2.t2)
myco2.t1 <- co2[1:12] # 1959年的观测数据
myco2.t3 <- co2[97:108] # 1965年的观测数据
t.test(myco2.t1,myco2.t3)

require(graphics) # 学生的睡眠数据
with(sleep, t.test(extra[group == 1], extra[group == 2]))
sleep 
t.test(extra ~ group, data = sleep) 
require(graphics)##学生的睡眠数据
with(sleep, t.test(extra[group == 1], extra[group == 2]))
t.test(extra ~ group, data = sleep,paired=TRUE)

attach(airquality)
Month <- factor(Month, labels = month.abb[5:9])
pairwise.t.test(Ozone, Month)
pairwise.t.test(Ozone, Month, p.adj = "bonf")
pairwise.t.test(Ozone, Month, pool.sd = FALSE)
detach()

oneway.test(weight~feed,data=chickwts, var.equal=T)
oneway.test(extra ~ group, data = sleep)
oneway.test(extra ~ group, data = sleep, var.equal = TRUE)
summary(aov(weight~feed,data=chickwts))
library(geepack)
data(dietox)
weight<-aov(Weight~Cu+Evit,data=dietox)
summary(weight)

data(dietox)
weight<-aov(Weight~Cu+Evit+Cu*Evit,data=dietox)
summary(weight)
data(seizure)
seiz.l <- reshape(seizure, 
    varying = list(c("base","y1", "y2", "y3", "y4")),
    v.names="y", times = 0:4, direction = "long")
seiz.l <- seiz.l[order(seiz.l$id, seiz.l$time),]
seiz.l$t <- ifelse(seiz.l$time == 0, 8, 2)
seiz.l$x <- ifelse(seiz.l$time == 0, 0, 1)
result <- aov(y ~ x + trt + x * trt, data=seiz.l)
summary(result)
data(dietox)
weight<-aov(Weight~Cu+Time+Cu*Time,data=dietox)
summary(weight)
wilcox.test(airquality$Ozone, mu = 36, 
    subset = Month %in% c(5, 8), exact = NULL, 
    correct = TRUE,conf.int = FALSE, conf.level = 0.95)
require(graphics)
x <- c(1.83,  0.5,  1.62,  2.48, 1.68, 1.88, 1.55, 3.06, 1.3)
y <- c(0.878, 0.647,0.598, 2.05, 1.06, 1.29, 1.06, 3.14,1.29)
wilcox.test(x, y, paired = TRUE, alternative = "greater")
wilcox.test(y - x, alternative = "less")
wilcox.test(y - x, alternative = "less",
            exact = FALSE, correct = FALSE)
x<-randu$x
y<-randu$y
wilcox.test(x,y,paired=FALSE) # Wilcox秩和检验
wilcox.test(x,y,paired =TRUE) # Mann-Whitney U检验
boxplot(weight~group, data=PlantGrowth)

kruskal.test(weight~group, data=PlantGrowth)
RoundingTimes <-  matrix(c(5.40, 5.50, 5.55,
                           5.85, 5.70, 5.75,
                           5.20, 5.60, 5.50,
                           5.55, 5.50, 5.40,
                           5.90, 5.85, 5.70,
                           5.45, 5.55, 5.60,
                           5.40, 5.40, 5.35,
                           5.45, 5.50, 5.35,
                           5.25, 5.15, 5.00,
                           5.85, 5.80, 5.70,
                           5.25, 5.20, 5.10,
                           5.65, 5.55, 5.45,
                           5.60, 5.35, 5.45,
                           5.05, 5.00, 4.95,
                           5.50, 5.50, 5.40,
                           5.45, 5.55, 5.50,
                           5.55, 5.55, 5.35,
                           5.45, 5.50, 5.55,
                           5.50, 5.45, 5.25,
                           5.65, 5.60, 5.40,
                           5.70, 5.65, 5.55,
                           6.30, 6.30, 6.25),
    nrow = 22,byrow = TRUE,
    dimnames = list(1:22,
        c("Round Out", "Narrow Angle", "Wide Angle")))
friedman.test(RoundingTimes)

data(iris)#鸢尾花数据集
head(iris)#查看下数据集
iris.data<-iris[,-5]#去掉最后一列，非数字变量
cor(iris.data)
head(airquality)
cor.test(airquality$Wind,airquality$Temp)
cor.test(airquality$Wind,airquality$Temp,method = "kendall")
if(!require(psych)) install.packages("psych")
library(psych)
corr.test(iris.data)
corr.test(iris.data)$r
corr.test(iris.data)$p
print(corr.test(iris.data)$r,digits=3)
if(!require(graphics)) install.packages(graphics)
require(graphics)
pairs(iris)
if(!require(corrplot)) install.packages("corrplot")
library(psych)
library(corrplot)
par(cex = 0.5)
corrplot(corr.test(iris.data)$r)

data(mtcars)
M <- cor(mtcars)
# different color series
col1 <- colorRampPalette(c("#7F0000","red","#FF7F00",
    "yellow","white", "cyan", "#007FFF", "blue","#00007F"))
col2 <- colorRampPalette(c("#67001F", "#B2182B", "#D6604D", 
    "#F4A582", "#FDDBC7", "#FFFFFF", "#D1E5F0", "#92C5DE", 
    "#4393C3", "#2166AC", "#053061"))
col3 <- colorRampPalette(c("red", "white", "blue"))
col4 <- colorRampPalette(c("#7F0000","red","#FF7F00",
    "yellow","#7FFF7F", "cyan", "#007FFF", "blue","#00007F"))
wb <- c("white","black")

library(corrplot)
par(mfrow = c(2,1))
corrplot(M, method = "number")
corrplot(M)

corrplot(M, order = "AOE", col = col1(20), cl.length = 21, 
         addCoef.col = "grey")

par(mfrow = c(3,1))
corrplot(M, method = "ellipse", col = col1(200),order ="AOE")
corrplot(M, method = "shade", col = col3(20),order = "AOE")
corrplot(M, method = "pie", order = "AOE")

par(mfrow = c(2,1))
corrplot(M, col = wb, order="AOE", outline=TRUE, cl.pos="n")
corrplot(M, col = wb, bg="gold2",  order="AOE", cl.pos="n")

corrplot(M,order = "AOE", type = "upper", tl.pos = "d")
corrplot(M,add = TRUE, type = "lower", method = "ell", 
    order = "AOE", diag=FALSE, tl.pos= "n", cl.pos = "n")
par(mfrow = c(2,1))

ran <- round(matrix(runif(225, -100,100), 15))
corrplot(ran, is.corr=FALSE)
corrplot(ran, is.corr=FALSE, cl.lim=c(-100, 100))
par(mfrow = c(3,1))

corrplot(M, order="AOE", tl.srt=60)
corrplot(M, order="AOE", diag=FALSE, tl.pos="d")
corrplot(M, order="AOE", type="lower", cl.pos="b")
cor.mtest <- function(mat, conf.level = 0.95){
  mat <- as.matrix(mat)
  n <- ncol(mat)
  p.mat <- lowCI.mat <- uppCI.mat <- matrix(NA, n, n)
  diag(p.mat) <- 0
  diag(lowCI.mat) <- diag(uppCI.mat) <- 1
  for(i in 1:(n-1)){
    for(j in (i+1):n){
      tmp <- cor.test(mat[,i], mat[,j], 
                      conf.level = conf.level)
      p.mat[i,j] <- p.mat[j,i] <- tmp$p.value
      lowCI.mat[i,j] <- lowCI.mat[j,i] <- tmp$conf.int[1]
      uppCI.mat[i,j] <- uppCI.mat[j,i] <- tmp$conf.int[2]
    }
  }
  return(list(p.mat, lowCI.mat, uppCI.mat))
}

res1 <- cor.mtest(mtcars,0.95)
res2 <- cor.mtest(mtcars,0.99)

par(mfrow = c(3,1))
corrplot(M, p.mat = res1[[1]], sig.level = 0.2)
corrplot(M, p.mat = res1[[1]], insig = "p-value",
         sig.level= -1) # add all p-values
corrplot(M, p.mat = res1[[1]], order = "hclust", 
         insig = "pch", addrect = 3)

if(!require(ellipse)) install.packages('ellipse')
library(ellipse)
library(psych)
mycol = colors()[as.vector(apply(corr.test(
  iris.data)$r, 2, rank))]
plotcorr(corr.test(iris.data)$r, 
         col = mycol, mar = rep(0, 4))
x <- c(44.4, 45.9, 41.9, 53.3, 44.7, 44.1, 50.7, 45.2, 60.1)
y <- c( 2.6,  3.1,  2.5,  5.0,  3.6,  4.0,  5.2,  2.8,  3.8)
par(mfrow = c(2, 1), mar = c(2, 4, 0.1, 0.1))
plot(x)
lines(x)
plot(y)
lines(y)
cor.test(x, y, method = "spearm", alternative = "g")
cov(x,y)
cor.test(x, y, method = "spearm", alternative = "g")
x <- as.data.frame(x) # 这个命令要求x是数据框或者矩阵
cov.wt(x, wt = rep(1/nrow(x), nrow(x)), cor = FALSE,
       center = TRUE, method = c("unbiased", "ML"))
xy <- cbind(x = 1:10, y = c(1:3, 8:5, 8:10))
w1 <- c(0,0,0,1,1,1,1,1,0,0)
cov.wt(xy, wt = w1) # i.e. method = "unbiased"
cov.wt(xy, wt = w1, method = "ML", cor = TRUE)
knitr::opts_chunk$set(tidy = FALSE)
```