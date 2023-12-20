# Short course on R environment

**M.Sc. Marco Antonio Peixoto**
- PhD. candidate in genetics and breeding - UFV
- Visiting scholar researcher - University of Florida  
- Quantitative genetics/genomics and data analyses

---

## Information

Date: 08/27/2022 

Time: 9-12 am (GMT 3) 


---
## Introduction

This is a repository created to aid the short course in R programming offered to **Núcleo de estudos em Silvicultura - UFLA**

---
<div id="top"/>

## Summary

[1 Download R and RStudio](#pt1)

[2 Introduction to R and RStudio](#pt2)

[3 Basic functions and structures in R language](#pt3)

[4 Functions and packages](#pt4)

[5 Models (AoV)](#pt5)

[6 Tukey test](#pt6)

[7 Regression models](#pt7)

[8 Plotting using ggplot2 package](#pt8)


---
## Content

<div id="pt1" />

#### 1 Download R and RStudio

Use the following link to download the R program and install it on your computer. It can be done for Windows, Linux, and MAC systems. After the download and installation of R, you can also download and install RStudio. RStudio is an IDE (integrated development environment). It makes your life easier.

- Download R (https://cran.r-project.org/) 
- Download RStudio (https://www.rstudio.com/products/rstudio/download/)


**Tip: go to this link (https://www.youtube.com/watch?v=28bKdOtIgSY) they will explain to you everything that you need to download and install both tools**

<div id="pt2" />

#### 2 Introduction to R and RStudio

- Integration, IDE, console, R environment, and communities

<div id="pt3" />

#### 3 Basic functions and structures in R language 

- mean, variance, median, length, dim, str

<!--
```r
data = rnorm(100,100,20)

mean(data)

var(data)

median(data)

length(data)

#dim(data)

str(data)

```

-->

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

<!--
Where is your main directory

```r
getwd() #Your currently directory

setwd("C:/folder/folder/") #Your path

```

Reading your data

```r
#reading your data
df0 = read.table("data/EX_DATA.txt",h=T)#reading your data

df = df0

head(df)
dim(df)
tail(df)

#Modifying
df$YLD = df$YLD/sqrt(df$YLD) #Modifing

#saving the output

write.table(df, file = "data/myoutput.txt") #saving the output

```
-->

<div id="pt4" />


#### 4 Functions and packages

- What is a function?

<!--
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
-->

- What is a package and how to install and use them

<!--
```r
install.packages("devtools") #Using install

require(devtools) #Call the package

```

- CRAN and Github

```r

devtools::install_github("adriancorrendo/metrica")

```
-->

<div id="pt5" />

#### 5 Models (AoV)

- Analyses of variance using the package Agricolae (Mendiburu, 2021)

<!--
Install the package and load it

```r
install.packages("agricolae")

require(agricolae)

```

Running the model and outputs

```r
# Model for ANOVA: y = u + block + gen + error 
mod = aov(YLD ~ NAME + BLOCK,
          data = df)

#summary
anova(mod)
summary.aov(mod)


#Mean
cv.model(mod)


#Plot for residuals
plot(mod)


```
-->

<div id="pt6" />

#### 6 Tukey test

- Implementation of tukey test

<!--
```r
###>>>>---- 2. Model
mod = aov(YLD ~ NAME + BLOCK,df)

##Residual

res = df.residual(mod)

## LSD
LSD.test(mod,"NAME",console = TRUE)

## Tukey
#HSD tukey = honestly significant differences

HSD.test(mod,"NAME",group = FALSE, console = TRUE)

```
-->

<div id="pt7" />

#### 7 Regression model

- Regression model

y = B0 + B1 + e

<!--

Using function lm


```r
#Regression

# y = Xb + e

#lm(target trait ~ predicted trait)

reg = lm(df$YLD ~ df$NAME)

#Plot
plot(reg)

```
-->

<div id="pt8" />

#### 8 Plotting using **ggplot2** package

- Installing the package ggplot2

<!--

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


Point

```r
ggplot(df, aes(YLD, HT)) + 
  geom_point() 


```

Density

```r
ggplot(df, aes(YLD)) + 
  geom_density(fill="#69b3a2", 
               color="#e9ecef", 
               alpha=0.8) 

```



Histogram

```r
p = ggplot(df, aes(HT)) + 
  geom_histogram(color = "blue",
                 fill = "blue") 
 

p

```


Boxplot

```r
df$RANGE = df$RANGE %>% as.factor 

ggplot(df, aes(RANGE, YLD)) + 
  geom_boxplot(fill = "blue") +
  theme(
    
  )

```

-->



- Saving the graphs

<!--
```r

#saving (We can save several formats, like .tiff, .png, .jpeg or even .pdf)

tiff("filename.tiff", width = 16, height = 8, units = 'in', res = 300)
plot
dev.off()

```
-->


---
## Sources that you may use

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

#Graphics

```r

https://r-graph-gallery.com/index.html

```

#Paclages cheatsheet

```r

https://www.rstudio.com/resources/cheatsheets/

```


[Main Menu](#top)
