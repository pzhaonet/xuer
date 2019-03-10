+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-13"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第四章 拟合）"
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

## 第四章 拟合

```
wp <- as.data.frame(WorldPhones)
wp$year <- as.numeric(rownames(wp))
m <- lm(wp$Asia ~ wp$Europe) 

m0 <- lm(wp$Asia ~ wp$Europe + 0) 

m  # 查看模型，显示斜率和截距。
msum <- summary(m)
msum  # 模型的详细总结报告。

msum$r.squared
msum$coefficients

example(lm)

par(mfrow = c(2, 2), mar = c(4, 4.2, 2, 1)) 
plot(m)

plot(x = wp$Europe, y = wp$Asia, pch = 19)
abline(m, col = "blue")
legend("bottomright", pch = c(19, NA), lty = c(NA, 1),
       legend = c("Data", "Linear fit"),
       col = c("black", "blue"), bty = 'n')
	   
text(x = 23000, y = 8500, labels = '(a)', col = 'red')

eqlm1 <- 'y = 0.2915x + 3783'
text(x = 23000, y = 7000, labels = eqlm1, adj = 0)

eqlm2 <- expression(y == 0.2915 * x + 3783)
text(x = 23000, y = 6000, labels = eqlm2, adj = 0)

eqlm3 <- expression(italic(y) == 0.2915 * italic(x) + 3783)
text(x = 23000, y = 5000, labels = eqlm3, adj = 0)

eqr2 <- expression(italic(R) ^ 2 == 0.9752)
text(x = 23000, y = 4000, labels = eqr2, adj = 0)

txt1 <- expression(sqrt(x))
legend('topright', legend = txt1)
legend('right', legend = txt1, lty = 1, col = 'blue', 
       bty = 'n')
	   
txt2 <- expression(integral(f(x) * dx, a, b))
legend('topleft', legend = txt2, col = 'blue', bty = 'n')

set.seed(123)
x <- seq(0, 50, 1)
y <- runif(1, 5, 15) * exp(-runif(1, 0.01, 0.05) * x) + 
  rnorm(51, 0, 0.5)
  
plot(x,y)

a_start <- 8
b_start <- - log(1/a_start) / 50
m <- nls(y ~ a * exp(-b * x), 
         start = list(a = a_start, b = b_start))
m

cor(y,predict(m))

summary(m)

example(lm)
demo(plotmath)
```
