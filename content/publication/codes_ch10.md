+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-08"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十章 字符）"
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

## 第十章 字符

```
x <- 'The quick brown fox jumps over the lazy dog'
xlower <- tolower(x)
class(xlower)
length(x)
nchar(x)

myfile2 <- "c:/r4r/co2.csv"

xsingle <- strsplit(xlower, '')[[1]]
nchar(xsingle)
length(xsingle)

grep(xsingle[1], xsingle)
for(i in 1:length(xsingle)) print(grep(xsingle[i], xsingle))
for(i in 1:length(xsingle))
  print(paste(xsingle[i], grep(xsingle[i], xsingle)))
sapply(xsingle, function(x) grep(x, xsingle))
table(xsingle)
duplicated(xsingle)
xsingle[!duplicated(xsingle)]
unique(xsingle)
length(unique(xsingle))



download.file(url =
                "http://dapengde.com/r4rookies/qianziwen.txt",
              destfile = "c:/r4r/qianziwen.txt")
qzw <- readLines('c:/r4r/qianziwen.txt', encoding = 'UTF-8')
class(qzw)
length(qzw) #向量长度
nchar(qzw) #向量里每个元素包含的字符数
qzwmerged <- paste(qzw, collapse = '')
qzwmerged <- gsub(' ', '', qzwmerged)
nchar(qzwmerged)
qzwsingle <- strsplit(qzwmerged, '')[[1]]
chardup <- qzwsingle[duplicated(qzwsingle)]
for(i in chardup) print(paste(i, grep(i, qzw, value = TRUE)))


download.file(url =
                "http://dapengde.com/r4rookies/kdclip.txt",
              destfile = "c:/r4r/kdclip.txt")
aa <- readLines("c:/r4r/kdclip.txt", encoding = "UTF-8")
length.aa <- length(aa)
title <- aa[c(seq(1, length.aa, by = 5))]
title.o <- order(title)
title <- title[title.o]
highlight <- aa[c(seq(4, length.aa, by = 5))][title.o]
kn <- data.frame(Title = title, Highlight = highlight)
write.table(kn, "c:/r4r/kn.txt",
            sep = "\t", row.names = FALSE)
location <- aa[c(seq(2, length.aa, by = 5))][title.o]
location[1]
time.aa <- substr(location,
                  (regexpr(" Added on ", location) + 10) ,
                  nchar(location))[title.o]
loc <- substr(
  location, 13,
  regexpr(" Added on ", location) - 5)[order(title.o)]
kn <- data.frame(Title = title, Highlight = highlight,
                 Loc = loc, Time = time.aa)
write.table(kn, "c:/r4r/kn2.txt",
            sep = "\t", row.names = FALSE)

```
