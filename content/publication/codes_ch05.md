+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-12"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第五章 循环）"
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

## 第五章 循环

```
mydata2 <- as.data.frame(t(matrix(co2, 12,
    dimnames = list(month.abb, unique(floor(time(co2)))))))
mydata2$year <- as.numeric(rownames(mydata2))
x <- mydata2$year
y <- mydata2$Sep
par(mfrow = c(3,3), cex = 1.2, mar = c(3, 2, 0.5, 1))
plot(x = x, y = y, type = 'p')
legend('topleft', legend = 'p', cex = 0.8,
       bty = "n", text.col = 'blue')
plot(x = x, y = y, type = 'l')
legend('topleft', legend = 'l', cex = 0.8,
       bty = "n", text.col = 'blue')
plot(x = x, y = y, type = 'b')
legend('topleft', legend = 'b', cex = 0.8,
       bty = "n", text.col = 'blue')
plot(x = x, y = y, type = 'c')
legend('topleft', legend = 'c', cex = 0.8,
       bty = "n", text.col = 'blue')
plot(x = x, y = y, type = 'o')
legend('topleft', legend = 'o', cex = 0.8,
       bty = "n", text.col = 'blue')
plot(x = x, y = y, type = 'h')
legend('topleft', legend = 'h', cex = 0.8,
       bty = "n", text.col = 'blue')
plot(x = x, y = y, type = 's')
legend('topleft', legend = 's', cex = 0.8,
       bty = "n", text.col = 'blue')
plot(x = x, y = y, type = 'S')
legend('topleft', legend = 'S', cex = 0.8,
       bty = "n", text.col = 'blue')
plot(x = x, y = y, type = 'n')
legend('topleft', legend = 'n', cex = 0.8,
       bty = "n", text.col = 'blue')
       
par(mfrow = c(3, 3), cex = 1.2, mar = c(3, 2, 0.5, 1))
for(i in c('p', 'l', 'b', 'c', 'o', 'h', 's', 'S', 'n')) {
  plot(x = mydata2$year, y = mydata2$Sep, type = i)
  legend('topleft', legend = i, cex = 0.8,
         bty = 'n', text.col = 'blue')
}


for(i in 1:20) print(i)

r <- 0.011
N1 <- 66.8
N2 <- N1 + r * N1
N3 <- N2 + r * N2
# ...... 如此写99行，就可以写到 N100。
N100 <- N99 + r * N99

r <- 0.011
N <- numeric(100)
N[1] <- 66.8
N[2] <- N[1] + r * N[1]
N[3] <- N[2] + r * N[2]
# ...... 如此写99行，一直写到 N[100]。
N[100] <- N[99] + r * N[99]

r <- 0.011
N <- numeric(100)
N[1] <- 66.8
for(t in 1:99) N[t + 1] <- N[t] + r * N[t] 

Y <- seq(2008, length.out = 100)
plot(Y, N)

abline(h = 100)
locator(1)

for(i in 1:360) {
    plot(1, ann = F, type = "n", axes = F)
    text(1, 1, "Ninja, go!", srt = i, col =
        rainbow(360)[i], cex = 7 * i/360)

}

example(image)

install.packages('simecol')
require(simecol)
# 40 * 40的棋盘:
m <- matrix(0, 40, 40)
# 玩家放置细胞的初始条件。0 表示该位置没有细胞，1 表示有细胞：
m[5:35, 19:21] <- 1
# 白色表示没有细胞，绿色有细胞：
image(m, col = c("white", "darkgreen"), axes = FALSE)
for(i in 1:200) {
  nn <- eightneighbours(m)
  m.old <- m
  # 当周围有三个细胞时该位置产生细胞：
  m[m.old == 0 & nn == 3] <- 1
  # 当周围细胞少于 2 个（太孤单）或大于 3 个（太拥挤）时，
  # 该位置细胞死亡。
  m[m.old == 1 & (nn < 2 | nn > 3)] <- 0
  image(m, col = c("white", "darkgreen"), axes = FALSE)
  Sys.sleep(0.1)
}

png(paste("c:/R/data/conway_",
          formatC(i, width = 2, flag = "0"), ".png",
          sep = ""),
    width = 300, height = 300)
image(m, col=c("white", "darkgreen"), axes = FALSE)
dev.off()

install.packages('rgl')
require(rgl)
example(movie3d)

x <- c(61, 45, 55, 46, 56, 79, 86, 57, 56, 56, 57, 71)
x + 100
for(i in 1:12) print(x[i] + 100)

wp <- as.data.frame(WorldPhones) # 转化为数据框类型
wp$year <- as.numeric(rownames(wp)) # 将行名称转化为数值类型
mydata3 <- data.frame( # 生成一个新数据框
  nphone = unlist(wp[, 1:7]), year = rep(wp$year, 7),
  conti = rep(names(wp)[1:7], each = nrow(wp)))
  
summary(mydata3)

str(mydata3)

mydata3$year <- as.factor(mydata3$year)
str(mydata3)

nlevels(mydata3$year)
levels(mydata3$year)

nlevels(mydata3$conti)
levels(mydata3$conti)


for(i in levels(mydata3$year)) {
  print(sum(mydata3$nphone[mydata3$year == i]))
}

tapply(mydata3$nphone, mydata3$year, sum)

mydata2 <- read.csv(file = "c:/r4r/co2.csv")
smr1 <- summary(mydata2)
smr1
smr1[6, 2] - smr1[1, 2]

smr2 <- lapply(mydata2, summary)
smr2[[2]][6] - smr2[[2]][1]

smr3 <- sapply(mydata2, summary)
smr3[6, 2] - smr3[1, 2]

plot(x = mydata3$year, y = mydata3$nphone)
boxplot(mydata3$nphone ~ mydata3$year)

N <- numeric(100)
N[1] <- 66.8
r <- 0.011
for(t in 1:3)
{
  N[t+1] <- N[t] + r * N[t]
  winDialog(type = c("ok"),
            message = paste('population in', t + 2007,
                            'will be', N[t + 1])) #信息提示框
}

n <- winDialogString(
  message = "which year's population would you like to see",
  default = '2050')
winDialog(type = c("ok"), message = paste(
  'population in', n, 'will be', N[as.numeric(n) - 2007]))

winDialog(type = c("ok"), message = paste(
  'population in', winDialogString(
    message = "which year's population would you like to see",
    default = '2050'), 'will be', N[as.numeric(n) - 2007]))
```
