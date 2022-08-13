# Short course on R environment

**M.Sc. Marco Antonio Peixoto**
- PhD. candidate in genetics and breeding - UFV
- Visiting researcher scholar - University of Florida  
- Quantitative genetics/genomics and data analyses

---

## Information

Date: 08/27/2022 

Time: 9-12 am (GMT 3) 

Zoom link:  https://ufl.zoom.us/j/97857089852?pwd=MzkzTG54ckoxWGJuYk5IcWtkSDh3UT09


---
## Introduction

This is a repository created to aid the short course in R programming offered to **Núcleo de estudos em Silvicultura - UFLA**

---
## Summary

[1 Download R and RStudio](#pt1)

[2 Introduction to R and RStudio](#pt2)

[3 Basic functions and structures in R language](#pt3)

[4 Download and install packages](#pt4)

[5 Models (AoV)](#pt5)

[6 Tukey test](#pt6)

[7 Regression models](#pt7)

[8 Plotting using ggplot2 package](#pt8)


---
## Content

<div id="pt1" />

#### 1. Download R and RStudio

Use the following link to download R program and install it in your computer. It can be done for Windows, Linux and MAC systems. After the download and intallation of R, you can also download and install RStudio. RStudio is an IDE (integrated development environment). It basically makes your life easier.

- Download R (https://cran.r-project.org/) 
- Download RStudio (https://www.rstudio.com/products/rstudio/download/)


**Tip: go to this link (https://www.youtube.com/watch?v=28bKdOtIgSY) that they will explain you everything that you need to download and install both tools**

<div id="pt2" />

#### 2. Introduction to R and RStudio

- Integration, IDE, console, R environment, and communities

<div id="pt3" />

#### 3. Basic functions and structures in R language 

- mean, variance, median, length, dim, str

```r
data = rnorm(100,100,20)

mean(data)

var(data)

median(data)

length(data)

#dim(data)

str(data)

```

- data structure: matrix, dataframe, list, arrays

Vector

```r

V1 = c(1:15)

V1[1]

```

Matrix


```r
M1 = matrix(V1, nrow = 5,ncol = 3)

M1[1,3]

```

Arrays

```r
V2 = c(16:30)
M2 = matrix(V2,ncol=3,nrow=5)

A1 = array(c(M1,M2), dim=c(3,5,2))

```


Data frame

```r
df1 = data.frame(id=c(rep(c(1,2,3,4,5),2)),
                  Var1=c(rnorm(10,10,1)),
                  Var2=c(runif(10,2,5)),
                  Var3=c(rep(c("a","b"),5)))

str(df1)

```

List 

```r
L1=list()

L1[[1]] = c(1,2,5,6,4,5,4,9)

L1[[2]] = c(54,28,68,45,75,98,74,68,45,45,"u","t","d",3,"x",6)

L1[[3]] = c(rnorm(18, 2,0.7))

str(L1)

```

- Import and export/save datasets

Where is your main directory

```r
getwd() #Your currently directory

setwd("C:/folder/folder/") #Your path

```

Reading your data

```r
#reading your data
df = read.table("data/EX_DATA.txt",h=T)#reading your data

head(df)
dim(df)

#Modifying
df$YLD = df$YLD/sqrt(df$YLD) #Modifing

#saving the output

write.table(df, file = "data/myoutput.txt") #saving the output

```

<div id="pt4" />

#### 4. Functions and packages

- What is a function?

Lets creat a mean function

```r
dat_mean = c(1:5)

#Mean R (1)
mean(dat_mean)

#Mean (2) = soma(dat_mean)/n(dat_mean)
(1+2+3+4+5)/5

#Mean (3)
sum(dat_mean)/length(dat_mean)

#Function
media = function(x){
  y = sum(x)
  y2 = length(x)
  
  y3 = y/y2

  return(y3)  
}

#Generate a new dataset
x = rnorm(20, 10, 2)

#our function
media(x=dat_mean)

#R function
mean(dat_mean)

```

- What is a package and how to install and use them

- CRAN and Github

<div id="pt5" />

#### 5. Models (AoV)

- Analyses of variance using the package ExpDes (Ferreira et al, 2021)

<div id="pt6" />

#### 6. Tukey test

- Implementation of tukey test

<div id="pt6" />

#### 7. Regression models

- Regression models

y = B0 + B1 + e

<div id="pt7" />

#### 8. Plotting using **ggplot2** package

- Installing the package ggplot2

```r
install.packages("ggplot2")

require(ggplot2)

``` 
- Organizing the dataset
- Using ggplot2
```r
ggplot(data, aes(x_, y_)) + #first line you should specify the data and x/y axes. 
  geom_point()              #Insert the type of graph that you want 

```

- Types of graphs: boxplot, density, histogram, point

Boxplot

```r
ggplot(airquality, aes(Temp, Ozone)) + 
  geom_point() + 
  geom_smooth(method = "loess"
)

```
Density

```r
ggplot(airquality, aes(Temp, Ozone)) + 
  geom_density() 

```

Histogram

```r
p = ggplot(airquality, aes(Temp, Ozone)) + 
  geom_histogram() 

p

```

Point

```r
p = ggplot(airquality, aes(Temp, Ozone)) + 
  geom_point() + 
  geom_smooth(method = "loess"
)

p

```


![Fig1](https://user-images.githubusercontent.com/59318360/182245039-7b60671b-d4a6-48fd-8929-2cbb6ee7d560.jpeg)



- Saving the graphs

```r

#saving (We can save several formats, like .tiff, .png, .jpeg or even .pdf)

tiff("filename.tiff", width = 16, height = 8, units = 'in', res = 300)
plot
dev.off()

```

<div id="pt8" />

---
## 3. Sources that you may use

### i. Github

### ii. Coursera

### iii. Youtube

### iv. Usefull functions

```r
#Paste
paste()
paste0()

#binds
rbind()
cbind()

```

### v. Usefull packages

```r
tydiverse
ggplot2
dplyr
plyr
stringr

```

### vi. Usefull websites

```r

#Graphics
https://r-graph-gallery.com/index.html

#Paclages cheatsheet
https://www.rstudio.com/resources/cheatsheets/


```
