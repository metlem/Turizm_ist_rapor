# 

---  
title: "  Türkiye'nin Son Üç Yıla Ait Turizm İstatistikleri "
author:meltemdizdar
output: html_document
runtime: shiny
---

 

```{r include=FALSE}
library(readxl)
library(dplyr)
library(knitr)

 turizm_ist <- read_excel("~/turizm_ist/turizm_ist.xlsx")
 numeric_turizm_ist <- read_excel("~/turizm_ist/turizm_ist.xlsx")

```
```{r echo=FALSE}
knitr::include_graphics("resim1.jpg")
```
> Bu rapor  [Türk Seyahat Acentaları Birliği'nin](http://www.tursab.org.tr/tr/turizm-verileri) 2014-2016 yılları arasıda kaydedilen verileri üzerinden hazırlanmıştır.

> 

> Son üç yılın turizm verilerinin bir kısmı aşağıdaki gibidir :

```{r echo=FALSE}
knitr::kable(turizm_ist[1:5,1:5])
knitr::kable(turizm_ist[1:5,6:10])
```


> ######Kullanılan R kodu _#knitr::kable(turizm_ist[1:5,1:5])_ ve _#knitr::kable(turizm_ist[1:5,6:10])_'dir.

> 

> Elimizdeki turizm verilerinin özet bilgisi şu şekildedir :

```{r echo=FALSE}
knitr::kable(summary(turizm_ist[,1:5]))
knitr::kable(summary(turizm_ist[,6:10]))
#summary(turizm_ist)
```

> ######_Kullanılan R kodu _#knitr::kable(summary(turizm_ist[,1:5]))_ ve _#knitr::kable(summary(turizm_ist[,6:10]))_'dir.


> Görüldüğü gibi ülkemizi 2014 yılında ortalama 383.647 turist ziyaret ederken, 2015 yılında ise 377.248 kişi ziyaret etmiştir. 2016 yılında ise ortalama turist sayımız 263.867'ye düşmüştür.

> Ülkemizi 2014 yılında minumum 10.000 kişiden 1.824, 2015 yılında 1.040, 2016 yılında ise 2.158 turist ziyaret etmiştir. 

> Ülkemize 2014-2015 yılları arasında gelen turistlerin minimum değişim oranı -43.3'tür. 2015-2016 yılında ise bu oran -76,2'dir. Bu oranların negatif olması beklenen turist sayısının yıllara göre düştüğünü göstermektedir.











```{r, echo = FALSE}
sliderInput("bins", "Aralığı seçiniz:", min = 1, max = 50, value = 30)
  
renderPlot({
   x <- turizm_ist[[9]]
  bins <- seq(min(x), max(x), length.out = input$bins + 1)

  hist(x, breaks = bins, col = '#000000', border = 'white',main = "2014-2015 Yılları Arası Değişim Oranı" )
  
 
  
})
```
```{r, echo = FALSE}
sliderInput("bins1", "Aralığı seçiniz:", min = 1, max = 50, value = 30)
  
renderPlot({
   y <- turizm_ist[[10]]
  bins1 <- seq(min(y), max(y), length.out = input$bins1 + 1)

  hist(y, breaks = bins1, col = '#000000', border = 'white',main = "2015-2016 Yılları Arası Değişim Oranı" )

 
  
})
```




