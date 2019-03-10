+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-03"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十五章 搭建小型网站）"
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

## 第十五章 搭建小型网站

```
if(!require(devtools)) install.packages('devtools')
devtools::install_github('rstudio/blogdown')
blogdown::install_hugo()
setwd('c:/blogdown_default')
blogdown::new_site()
blogdown::serve_site()
blogdown::build_site()
setwd('c:/blogdown_default')
blogdown::new_site(theme='gcushen/hugo-academic')
```
