+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-09"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第九章 函数）"
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

## 第九章 函数

```
y <- sd(x = 1:5)  # sd 是函数名, x 是自变量。
y
sd
assign("x", 1:5)

newscore <- function(x) {
  y <- sqrt(x) * 10
  return(y)
}
newscore(x = 40)

x <- 36
y <- 81
newscore(x = y)  # 函数内部的 x 把 81 的值接过来，而不是36。
x # 函数外部的x仍然是36。

news <- function(x, n) {
  sqrt(x) * 10 + n
}
news(x = 36, n = 10)
news(36, 10)
news(n = 10, x = 36)

newscore()
newscore <- function(x = 36) # 将x默认值设为36。
{
  sqrt(x) * 10
}
newscore()

exponentialGrowth <- function(N0, r = 0.01, tmax = 10) 
  # 三个自变量：初始值，增长率（默认为0.01），时间（默认为10）。
{
  N <- N0
  for(t in 1 : (tmax - 1)) {
    N[t + 1] <- N[t] + r * N[t]
  }
  return(N) 
}
plot(exponentialGrowth(80, 0.02, 100))

source('c:/r4r/myf.r')

install.packages("maptools") # 第一次使用某个扩展包时要先安装。
require(maptools)  # 调用包，让R把其中的函数读进R的脑子里。
position <- c(116.39, 39.91)  # 天安门广场的经纬度。
mydate <- "2017-10-01"  # 要计算的日期。
# 日出时刻：
sunriset(matrix(position, nrow = 1), 
         as.POSIXct(mydate, tz = "Asia/Shanghai"), 
         direction = c("sunrise"), POSIXct.out = TRUE)$time
# 日落时刻:
sunriset(matrix(position, nrow = 1), 
         as.POSIXct(mydate, tz = "Asia/Shanghai"), 
         direction = c("sunset"), POSIXct.out = TRUE)$time
# 函数名为flag，默认是计算2017年情人节开始一周内升降国旗时刻。
flag <- function(date.start = "2017-02-14", date.length = 7) 
{
  mydate <- seq(as.POSIXct(date.start, tz="Asia/Shanghai"), 
                by = 3600 * 24, length.out = date.length)
  data.frame(
    sunrise = sunriset(
      matrix(c(116.39, 39.91), nrow = 1), 
      as.POSIXct(mydate, tz="Asia/Shanghai"),
      direction=c("sunrise"), POSIXct.out = TRUE)$time,
    sunset = sunriset(
      matrix(c(116.39, 39.91), nrow = 1), 
      as.POSIXct(mydate, tz="Asia/Shanghai"), 
      direction=c("sunset"), POSIXct.out = TRUE)$time)
}

flag("2017-10-01") # 好了，以后调用这个函数就能很方便计算。


install.packages("beginr")
beginr::plotpch()
beginr::plotlty()
beginr::plottype()
beginr::plotcolors()

set.seed(123)
x <- 1:10
y <- 1:10 + rnorm(10)
beginr::plotlm(x, y, refline = TRUE)

x <- rnorm(10000)
beginr::plothist(x)

df <- data.frame(a = 1:10,
                 b = 1:10 + rnorm(10),
                 c = 1:10 + rnorm(10))
beginr::plotpairs(df)
beginr::plotpairs2(df)

par(mfrow = c(1,2), mar = c(0.1, 0.1, 0.1, 0.1))
x <- seq(0, 2 * pi, length.out = 100) 
y <- data.frame(sin(x), cos(x))
# 假定yerror是y的误差范围
yerror <- data.frame(abs(rnorm(100, sd = 0.3)), 
                     abs(rnorm(100, sd = 0.1)))
beginr::dfplot(x, y, yerror = yerror)
beginr::dfplot2(y, x, xerror = yerror, xlab = '', ylab = '')

x <- seq(0, 2 * pi, length.out = 100)
y <- sin(x)
plot(x, y, type = "l")
beginr::errorbar(x, y, yupper = 0.1, ylower = 0.1)
df <- data.frame(a = 1:10, 
                 b = 1:10 + rnorm(10), 
                 c = 1:10 + rnorm(10))
beginr::lmdf(df)

beginr::bib(pkg = c("mindr", "bookdownplus", "pinyin"))

install.packages("fortunes")
require(fortunes)
fortune('Actually, I see it as part of my job')
citation("bookdown")

length(unique(rownames(available.packages())))

a <- available.packages() # 获取所有扩展包的信息
b <- rownames(a) # 挑出扩展包的名称
c <- unique(b) # 去掉重复的名称
d <- length(c) # 数数有几个

beginr::plotpkg('rmarkdown', from = '2014-01-01')

install.packages(c("devtools", "roxygen2", "knitr", "beginr"))
beginr::rpkg()
newscore <- function(x) {
  y <- sqrt(x) * 10
  return(y)
}

#' Calculate new score
#'
#' @param x old score
#'
#' @return new score
#' @export
#'
#' @examples newscore(49)
newscore <- function(x) {
  y <- sqrt(x) * 10
  return(y)
}

library(mypkg)
newscore(36)

example(newscore)

devtools::install_github("pzhaonet/beginr")
```
