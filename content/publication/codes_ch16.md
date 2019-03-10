+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-02"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十六章 在工作中应用）"
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

## 第十六章 在工作中应用

```
rdoc <- readLines('c:/r4r/rdoc.Rmd', encoding = 'UTF-8')
for(k in 1:7) {
  newrmd <- paste('c:/r4r/', k, '.Rmd', sep = '')
  rdoc[13] <- paste('i <-', k)
  writeLines(rdoc, newrmd, useBytes = TRUE)
  rmarkdown::render(newrmd, encoding = 'UTF-8')
}
```
