+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-11"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第六章 分支）"
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

## 第六章 分支

```

3 > 2  # 3比2大？是真（true）的。
1 > 2  # 1比2大？是假（false）的。
!(1 > 2)  # 1不比2大？呃......
3 > 2 & 1 > 2  # 3比2大，并且1比2大？假的。
3 > 2 | 1 > 2  # 3比2大，或者1比2大吗？真的。
3 > 2 & !(1 > 2)  # 3比2大，并且1不比2大？好像是真的吧...

x <- 1:3
x == 2

x == 2 | x == 3

y <- c(4, 1, 2)
x > y

x > y & y > 1

TRUE * FALSE
TRUE + TRUE

sum(x > y)

x %in% y
x[x %in% y]
which(x %in% y)
Y[N > 100][1]

x <- 60
if(x < 75) print("x is less than 75")  

if(x < 75) {
	print("x is less than 75")
	y <- x + 10
	print(y)
	}
	
x <- 60
if(x < 75) {
    print("x is less than 75")
} else {
    print("x is larger than 75")
}  # 如果()，那么{}，否则{}。

x <- 60
if(x < 75) {
    print("small")
} else if(x > 90){
    print("large")
} else {
	print("good")
}

ifelse(x < 75, "small", ifelse(x > 90, "large", "good"))


N <- numeric(100)
N[1] <- 66.8
for(t in 1:99) N[t + 1] <- N[t] + r * N[t]
Y <- seq(2008, length.out = 100)
plot(x = Y + 2007, y = N, xlab = "Year", ylab = "Population", 
     cex = ifelse(N >= 100, 2, 1), pch = 16, type = "b", 
     col = ifelse(N >= 100, "red", "darkgreen"))
```
