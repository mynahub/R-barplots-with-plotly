# R-barplots-with-plotly
R barplots with plotly
###N-Terminal SNP
library(plotly)

x <- c("Bioko", "Cameroon", "Gambia", "Ghana", "Iran", "Kenya", "Malawi", "Phillipiens", "Solomon Island", "Tanzania", "Vanuatu", "Venezuela")
y1 <- c(0, 0, 100, 0, 100, 0, 0, 0, 0, 0, 0, 0)
y2 <- c(49, 100, 100, 26, 100, 31, 0, 100, 100, 100, 100, 100)
data <- data.frame(x, y1, y2)

#The default order will be alphabetized unless specified as below:
data$x <- factor(data$x, levels = data[["x"]])

fig <- plot_ly(data, x = ~x, y = ~y1, type = 'bar', name = '1MMRKLAILSVSSFLF15', marker = list(color = 'rgb(49,130,189)'))
fig <- fig %>% add_trace(y = ~y2, name = '76DGNNNNGDNGREGKDEDKR77', marker = list(color = '#EC8FA3'))
fig <- fig %>% layout(xaxis = list(title = "Country", size = t, tickangle = -45),
                      yaxis = list(title = "Prevalence(%)"),
                      margin = list(b = 100),
                      barmode = 'group')

fig

