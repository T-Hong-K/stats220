## Index
 ![](bingen.jpg)
 
 Below is the code that I used to create this meme.

```r 
library(magick)

before <- image_read("images/before.jpg") %>%
  image_scale(355)

after <- image_read("images/after.jpg") %>%
  image_scale(355)

goa <- image_blank(width = 200,
                   height = 200,
                   color = "#000000")%>%
  image_annotate(text = "jesse \ntheyre \ncoming a",
                 color = "#FFFFFF", 
                 size = 40,
                 font = "Impact",
                 gravity = "center")
wtfteam <- image_blank(width = 200,
                       height = 200,
                       color = "#000000")%>%
  image_annotate(text = "WTF why\ndidnt you\nhelp me",
                 color = "#FFFFFF",
                 size = 40,
                 font = "Impact",
                 gravity = "center")
first_row <- c(before, goa)%>%
  image_append()

second_row <- c(after, wtfteam)%>%
  image_append()

bingen <-c(first_row, second_row)%>%
  image_append(stack = TRUE)

image_write(bingen, "images/bingen.jpg")
