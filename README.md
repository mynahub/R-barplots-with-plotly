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

#Plotting Cterminal-SNP frequency with different color.

library(ggplot2)
library(dplyr)
library(tidyr)
df<-read.csv("NTerminalIndels.csv")
head(df)
df=ggplot(df, aes(Indel, Percentage, fill=Country))+
  geom_bar(stat ="identity", width = 0.7, position = position_dodge() )+
  #coord_flip()+
  ggtitle("N-Terminal INDELs")+
  theme_minimal()+
  theme(axis.title = element_text(size = 10, face = "bold"))+
  theme(plot.title = element_text(hjust =0.5, face = "bold", size = 10))
  df+scale_fill_manual(values=c('#e6194b', '#3cb44b', '#ffe119', '#4363d8', '#800000', '#911eb4', '#46f0f0', '#f032e6', '#000075', '#808000', '#008080', '#000000'))

df
