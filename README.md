# Short course on R environment

**M.Sc. Marco Antonio Peixoto**
- PhD. candidate in genetics and breeding - UFV
- Visiting researcher scholar - University of Florida  
- Quantitative genetics/genomics and data analyses

---
## 1. Introduction

This is an repository created to aidded the short course in R programming offered to **Núcleo de estudos em Silvicultura - UFLA**

---
## 2. Summary

[1 Download R and RStudio](#pt1)

[2 Introduction to R and RStudio](#pt2)

[3 Basic functions in R language](#pt3)

[4 Download and install packages](#pt4)

[5 Models (AoV)](#pt5)

[6 Plotting using ggplot2 package](#pt6)


---
## 3.Content

<div id="pt1" />

#### 1. Download R and RStudio

 Use the following link to download R program and install it in your computer. It can be done for Windows, Linux and MAC systems. After the download and intallation of R, you can also download and install RStudio. RStudio is an IDE (integrated development environment). It basically makes your life easier

- Download R (https://cran.r-project.org/) 
- Download RStudio (https://www.rstudio.com/products/rstudio/download/)


**Tip: go to this link (https://www.youtube.com/watch?v=jpptwObI1ps) that they will explain you everything that you need to download and install both tools**

<div id="pt2" />

#### 2. Introduction to R and RStudio

- Integration, IDE, console, R environment, and communities

<div id="pt3" />

#### 3. Basic functions in R language 

- mean, var, mode, length, dim, str

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

- setdw() command and saving projects

```r

getwd() #Your currently directory

setwd("C:/folder/folder/") #Your path

```

- Import and export/save datasets

```r
#reading your data
df = read.data("mydata.txt)

#Modifing
df1 = df/sqrt(df)

#saving the output

save.table(df1, file = "myoutput.txt)

```

<div id="pt4" />

#### 4. Download and install packages

- What is a package and how to install and use them

- CRAN and Github

<div id="pt5" />

#### 5. Models (AoV)

- Analyses of variance using the package ExpDes (Ferreira et al, 2021)

<div id="pt6" />

#### 6. Plotting using **ggplot2** package

- Installing the package ggplot2
- Organizing the dataset
- Types of graphs: boxplot, density, histogram, ...

```r
p = ggplot(airquality, aes(Temp, Ozone)) + 
  geom_point() + 
  geom_smooth(method = "loess"
)

```

- Plotting the graph

```r
p

```

![Fig1](https://user-images.githubusercontent.com/59318360/182245039-7b60671b-d4a6-48fd-8929-2cbb6ee7d560.jpeg)




- Saving the graphs


---
## 3. Sources that you may use

### 1. Github

### 2. Coursera

### 3. Youtube

### 4. Usefull functions

```r
#Paste
paste()
paste0()

```

### 5. Usefull packages

```r
tydiverse
ggplot2
dplyr
plyr
stringr

```

