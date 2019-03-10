+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-06"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十二章 时间）"
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

## 第十二章 时间

```
bd <- '1994-09-22 20:30:00'
bdtime <- strptime(x = bd, format = '%Y-%m-%d %H:%M:%S', 
                   tz = "Asia/Shanghai")
bdtime

class(bd)
class(bdtime)
t1 <- Sys.time() # 返回当前时刻
t2 <- date() # 返回当前时刻
t3 <- Sys.Date() # 返回当前日期
t1
t2
t3
class(t1)
class(t2)
class(t3)
bdtime$wday

unlist(unclass(bdtime))
format(bdtime, format = '%d.%m.%Y')

bdtime + 1
bdtime + 60
bdtime + 3600

t3 <- bdtime + 86400
t3

bdtime2 <- strptime(
  '1995-09-01 7:30', format = '%Y-%m-%d %H:%M', 
  tz = 'Asia/Shanghai')
bdtime2 - bdtime

difftime(time1 = bdtime2, time2 = bdtime, units = 'secs')

mean(c(bdtime, bdtime2))

(a <- strptime("2018-03-25 03:00:00", 
              format = "%Y-%m-%d %H:%M:%S", tz = "CET"))
a - 1
(a <- as.POSIXlt("2018-03-25 03:00:00", tz = "CET"))
a - 1
(a <- as.POSIXlt("2018-03-25 02:00:00", tz = "CET"))
(a <- strptime("2018-03-25 02:00:00", 
              format = "%Y-%m-%d %H:%M:%S", tz = "CET"))
a - 1
```
