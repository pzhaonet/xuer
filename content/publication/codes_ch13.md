+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-05"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十三章 批量处理文件）"
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

## 第十三章 批量处理文件

```
download.file(url= "http://dapengde.com/r4rookies/figren.zip",
              destfile = "c:/r4r/figren.zip")
unzip(zipfile = "c:/r4r/figren.zip", exdir = "c:/r4r")
fotodir <- 'c:/r4r/figren'
fotofilefull <- dir(fotodir, full.names = TRUE)
fotofile <- dir(fotodir)
fotoinfo <- file.info(fotofilefull)
fotoinfo
fototime <- format(fotoinfo$mtime, '%Y-%m-%d-%H%M%S')
newname <- paste(
  fotodir, '/', fototime, '_', fotofile, sep = '')
file.rename(fotofilefull, newname)

urlink <- 'http://www.biomet.co.at/pictures/'
aa <- readLines(urlink, encoding = 'UTF-8') # 读取网页
linkformat <-
  'src="http://www.biomet.co.at/wp/wp-content/gallery'
bb <- aa[grep(linkformat, aa)]

for(i in 1:length(bb))
  bb[i] <- substring(
    bb[i],
    regexpr("http", bb[i])[1],
    regexpr(".jpg\"", bb[i])[1]+3) # 获取链接
bb <- unique(bb)
length(bb)
writeLines(bb, 'c:/r4r/links.txt')

stname <- substring(bb, 47, 50)
stname <- stname[-which(stname == '')]
for(i in unique(stname))
  dir.create(paste('c:/r4r/', i, sep = ''))

for(i in 1:length(bb)) {
  download.file(
    url = bb[i],
    destfile = paste(
      'c:/r4r/', stname[i],'/', stname[i], i, '.jpg',
      sep = ""),
    method = 'curl', quiet = TRUE)
  print(paste(i, 'of', length(bb), 'downloaded.'))
}
winDialog(type = c("ok"), message = '下载完毕！')

download.file(url = "http://dapengde.com/r4rookies/obs.zip",
              destfile = "c:/r4r/obs.zip")
unzip(zipfile = "c:/r4r/obs.zip", exdir = "c:/r4r")
stn <- 54527
obsdir <- 'c:/r4r/obs'
obsfilefull <- dir(obsdir, full.names = TRUE)
obstime <- as.numeric(dir(obsdir))
output <- NULL
for(k in 1:length(obsfilefull))
{
  input <- read.table(obsfilefull[k], header = FALSE,
                      skip = 2, sep="")
  output_new <- input[which(input[, 1] == stn),]
   if(nrow(output_new) != 0)
     rownames(output_new) <- obstime[k]
  output <- rbind(output, output_new)
}
output$time <- rownames(output)


shell('notepad')
shell('start iexplore http://xuer.pzhao.net')
shell('cmd /c "D:/Program Files/Tencent/QQProtect.exe"')
```
