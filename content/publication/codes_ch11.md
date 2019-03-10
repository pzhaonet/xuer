+++
abstract = ""
abstract_short = ""
authors = []
date = "2017-04-07"
image_preview = ""
math = true
publication_types = ["6"]
publication = ""
publication_short = ""
selected = true
title = "示例代码（第十一章 地图）"
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

## 第十一章 地图

```
download.file(url = "http://dapengde.com/r4rookies/us.csv",
              destfile = "c:/r4r/us.csv")
us <- read.csv("c:/r4r/us.csv")
summary(us)
nlevels(us$state)
plot(us$lon, us$lat)

plot(us$lon, us$lat)
points(us$lon[us$state == "Texas"],
       us$lat[us$state == "Texas"], col="blue")

cols <- rainbow(nlevels(us$state))
plot(us$lon, us$lat, col = cols[us$state], pch = 20)

lon.median <- tapply(us$lon, us$state, median)
lat.median <- tapply(us$lat, us$state, median)
text(labels = levels(us$state), x = lon.median, y = lat.median, 
     cex = 0.5, col = 'White')
points(-74.02, 40.73, pch = 17, cex = 2)


download.file(url = "http://dapengde.com/r4rookies/cm.zip",
              destfile = "c:/r4r/cm.zip")
unzip(zipfile = "c:/r4r/cm.zip", exdir = "c:/r4r")
install.packages('rgdal')
require(rgdal) 
cm <- readOGR(dsn = "c:/r4r/cm", layer = "bou2_4p") 
plot(cm)

summary(cm)
is.factor(cm$NAME)
levels(cm$NAME)  # 省市名称。

download.file(url =
                "http://dapengde.com/r4rookies/aqi.csv",
              destfile = "c:/r4r/aqi.csv")
aqi <- read.csv("c:/r4r/aqi.csv")
aqi
aqstandard <- c(0, 50, 100, 150, 200, 300, 500, Inf)
aqilevel <- cut(aqi$aqi[match(levels(cm$NAME),aqi$province)], 
                aqstandard)
mycol <- grey(seq(1, 0, 
                  length.out = nlevels(aqilevel)))[aqilevel]
col <- cm$NAME
levels(col) <- mycol
plot(cm, col = as.character(factor(col)), axes = TRUE)

install.packages('plotrix')
library(plotrix)
legendn <- character((length(aqstandard) - 2) * 2 + 1)
legendn[seq(2, length(legendn), by = 2)] <- 
  aqstandard[2:(length(aqstandard)-1) ]
color.legend(
  xl = 135, yb = 10, xr = 137, yt = 30,legend = legendn,
  rect.col = grey(seq(1, 0, length.out = nlevels(aqilevel))),
  align = "lb", gradient = "y")  # 添加图例。
color.legend(
  xl = 135, yb = 10, xr = 137, yt = 30,
  legend = c('Excellent','Good','Lightly', 'Moderately', 
             'Heavily', 'Severely', 'OMG'),
  rect.col = grey(seq(1, 0, length.out = nlevels(aqilevel))),
  align = "rb", gradient = "y")  # 添加图例。

install.packages('leafletCN')
require(leafletCN)
aqi$aqi[aqi$aqi == -1] <- NA
pvs <- regionNames("china")
loc <- match(pvs, aqi$province)
aqi2 <- data.frame(name = pvs, value = aqi$aqi[loc])
geojsonMap(dat = aqi2, mapName = "china",
           popup =  paste(aqi2$name, aqi2$value),
           legendTitle = "AQI")
```
