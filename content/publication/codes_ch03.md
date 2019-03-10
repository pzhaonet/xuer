+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-14"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第三章 作图）"
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

## 第三章 作图

```
mydata2 <- as.data.frame(t(matrix(
  co2, 12, 
  dimnames = list(month.abb, unique(floor(time(co2)))))))  

mydata2$year <- as.numeric(rownames(mydata2))

plot(mydata2$Sep)

example(plot)

plot(x = mydata2$year, y = mydata2$Sep)

plot(mydata2)

pairs(mydata2)

demo(graphics)

plot(x = mydata2$year, y = mydata2$Sep, 
     xlab = "Year", ylab = "CO2 in Sep", 
     ylim = c(300, 400), type = "l")
	 
mydata2 <- read.table(file = myfile2,
                      header = TRUE, sep = ",")

plot(x = mydata2$year, y = mydata2$Sep, type = "p")

plot(x = mydata2$year, y = mydata2$Sep, type = "p", pch = 20)

plot(x = mydata2$year, y = mydata2$Sep, 
     type = "p", pch = 'z')
	 
plot(x = mydata2$year, y = mydata2$Sep, type = "l", lty = 2)

plot(x = mydata2$year, y = mydata2$Sep, type = "l", lty = 2, 
     col = 'blue')

colors()

colors()[26]

plot(x = mydata2$year, y = mydata2$Sep, type = "p", pch = 20,
     col = colors()[27:(27 + 39 - 1)], cex = 3)
	 
demo(colors)
demo()
demo(persp)

rainbow(n = 39)
plot(x = mydata2$year, y = mydata2$Sep, type = "p", pch = 20,
     col = rainbow(n = 39), cex = 3)
	 
myco2 <- unlist(mydata2[, 1:12])
myco2 <- round(myco2)
myyear <- rep(mydata2$year, 12)
mymonth <- rep(1:12, each = nrow(mydata2))
n <- diff(range(myco2)) # 彩虹分割的颜色数量
mycolor <- rainbow(n)[myco2 - min(myco2) + 1]
plot(x = mymonth, y = myyear, 
     col = mycolor, cex = 10, pch = 15)
	 
image(t(as.matrix(mydata2[1:12])), col = rainbow(n))

plot(x = mydata2$year, y = mydata2$Sep)
abline(h = 350)
abline(h = 360, v = 1980, col = 'red')
abline(h = seq(from = 320, to = 340, by = 5), 
       v = seq(from = 1970, to = 1990, by = 5), col = 'grey')
abline(a = -2240, b = 1.3)
legend(x = 1970, y = 350, legend = 'Sep', pch = 1)
legend("topleft", legend = 'Sep', pch = 1)

plot(x = 1:12, y = mydata2['1959', 1:12], 
     xlab = 'Month', ylab = expression(CO[2]),
     ylim = c(310, 370), 
     type = "l", lty = 2, col = 'blue')
lines(x = 1:12, y = mydata2['1997', 1:12], col = 'red')
points(x = 1:12, y = mydata2['1997', 1:12], col = 'red', type = 'l')

plot(x = 1:12, y = mydata2['1959', 1:12], 
     xlab = 'Month', ylab = '1959',
     type = "l", lty = 2, col = 'blue')
par(new = TRUE)
plot(x = 1:12, y = mydata2['1997', 1:12], ylab = '1997', 
     type = "l", lty = 1, col = 'red')

# 1. 告诉R在右侧为副坐标轴留出空间。
par(mar = c(5,4,4,4))
# 2. 画第一张图。
plot(x = 1:12, y = mydata2['1959', 1:12], 
     xlab = 'Month', ylab = '1959',
     type = "l", lty = 2, col = 'blue')
# 3. 告诉R，下一张图跟第一张图叠加。
par(new = TRUE)
# 4. 画第二张图，但暂时不画坐标轴，也不标标签。
plot(x = 1:12, y = mydata2['1997', 1:12], 
     type = "l", lty = 1, col = 'red', axes = FALSE, 
     ylab = '', xlab = '')
# 5. 在右侧画出副坐标轴。
axis(side = 4, col = 'red')
# 6. 为副坐标轴添加名称。
mtext(side = 4, text = '1997', line = 3, col = 'red')

par(mfrow = c(1, 2))
plot(x = 1:12, y = mydata2['1959', 1:12],
     xlab = 'Month', ylab = '1959',
     type = "l", lty = 2, col = 'blue')
plot(x = 1:12, y = mydata2['1997', 1:12],
     xlab = 'Month', ylab = '1997', 
     type = "l", lty = 1, col = 'red')

# 打开一张宽度为8，高度为4的白纸:
pdf('c:/r4r/fig2_13.pdf', width = 8, height = 4)
# 在白纸上画图:
plot(x = mydata2$year, y = mydata2$Jan)
# 画完了，把纸张收起来:
dev.off()

install.packages(c('ggplot2', 'lattice', 'plotrix'))

library(ggplot2)
example(qplot)

library(lattice)
demo(lattice)

library(plotrix)
demo(plotrix)

mydatasub <- t(mydata2[as.character(
  seq(1960, by = 5, length.out = 8)), 1:12])
x <- rep(1:12, 8)
y <- as.vector(mydatasub)
group <- rep(colnames(mydatasub), each = 12)
library(lattice)
xyplot(y ~ x|group, type = c('p', 'l'), 
       xlab = 'Month', ylab = expression(CO[2]))

library(ggplot2)
qplot(x, y, col = group, geom = c("point", "line"), 
      xlab = 'Month', ylab = expression(CO[2]))

vignette('ggplot2-specs')
vignette(all = TRUE)
	 
```
