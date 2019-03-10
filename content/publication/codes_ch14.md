+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-04"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十四章 论文书稿写作）"
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

## 第十四章 论文书稿写作

```
install.packages("bookdownplus")
require(bookdownplus)
for(i in template()[1:19])
  bookdownplus(template = i,
               more_output = more_output()[1:3])
for(mf in mail_font()) {
  for(ms in mail_style()) {
    for(mt in mail_theme()) {
      outputname <- paste('mail', ms, mf, mt, sep = '_')
      bookdownplus(template = 'mail',
                   mail_style = ms,
                   mail_font = mf,
                   mail_theme = mt,
                   output_name = outputname)
    }
  }
}

bookdownplus(template = 'article')

bookdownplus(template = template()[1])
template()

bookdownplus(template = 'article',
             author = 'John Smith',
             title = 'My article')

more_output()

bookdownplus(template = 'article',
             more_output = more_output())

bookdown::publish_book()

bookdownplus(template = 'thesis_ubt')

bookdownplus(template = 'thesis_mypku')

install.packages('mindr')
library('mindr')
md2mm()

bookdownplus(template = `nte_zh`)

bookdownplus(template = 'journal')

bookdownplus(template = 'guitar')

```
