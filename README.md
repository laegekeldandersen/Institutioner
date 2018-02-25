# RStudio - Survival guide
------

## Indhold
------

### 1. Opsætning

### 2. Indlæs data

### 3. Basale funktioner

### 4. Statistik

### 5. Datavisualisering

### 6. Gem eller eksport data

### 7. Begreber

### 8. Ressourcer

### 9. Todo

------
## 1. Opsætning
------

### 1.1 Installér R

* R-statistics: <https://www.r-project.org/>

* RStudio: <https://www.rstudio.com/>

### 1.2 Arbejdsbibliotek

* Aktuelle

```
> getwd() 
```
	

* Skift

```
> setwd(“C://file/path”) 
```

* Eller  

```
> setwd("~/Test") 
```


### 1.3 Installer pakker
------

``` 
> install.packages("<the package's name>")
```


### 1.4 Indlæs pakke
------

```
> library(<the package's name>) 
```


## 2. Indlæs data
------

```
> read.csv(file=”myfile”)
```
```
> read.csv2(file=”myfile”, header=TRUE)
```
```
> read.delim(file=”myfile”, header=TRUE)
```
```
> readLines("myfile”)
```
```
> read.fwf(”myfile”, widths=c(1,2,3)
```

**Indlæs data fra SAS, SPSS mv. i R**
  
**SPSS**
```
> library("foreign")
> read.spss(“myfile”) 
```
**Stata**
```
> library("foreign")
> read.dta(“myfile”) 
```
**SAS**
```
> library("foreign")
> read.export(“myfile”) 
```

**Indbyggede datasæt i R**

* http://www.sthda.com/english/wiki/r-built-in-data-sets/


## 3. Basale Funktioner
------

**Se importeret dataværdier i dataframe (tabel)**

``` 
> dat
```
    
**Se alle variable (kolonner) i dataframen (tabellen)**
    
``` 
> ls() 
```
    
**Lav ny dataframe (tabel) med specifikke variable (kolonner)**

```
> myvars <- c("v1", "v2", "v3")
> newdata <- mydata[myvars]
```

**Vælg individuelle variable (kolonner)**
    
```
> select(mtcars, mpg, hp)
```

**Ekskludér individuelle variable (kolonner)**

´´´
myvars <- names(mydata) %in% c("v1", "v2", "v3") 
newdata <- mydata[!myvars]
´´´

## 4. Statistik
------

### 4.1 Diskriptiv statistik

``` 
> sapply(mydata)
```

**Output: mean, sd, var, min, max, median, range, and quantile. Ekskluderer manglende værdier**


``` 
> summary(mydata)
```

**Output: mean, median, 25th and 75th quartiles, min, max**


### 4.2 Hmisc-pakken

```
> install.packages("hmisc")
> library(Hmisc)
> describe(mydata) 
```

**Output: n, nmiss, unique, mean, 5,10,25,50,75,90,95th percentiles, the 5 lowest and 5 highest scores.**


### 4.3 Pastecs-pakken

```
> install.packages("pastecs")
> library(pastecs)
> stat.desc(mydata) 
```

**Output: nbr.val, nbr.null, nbr.na, min max, range, sum, median, mean, SE.mean, CI.mean, var, std.dev, coef.var**


### 4.4 Psych-pakken


```
> install.packages("psych")
> library(psych)
> describe(mydata)
```

**Output: item name, item number, nvalid, mean, sd, median, mad, min, max, skew, kurtosis, se**



### 1. Case-control studies
------

**Udbygges snarest med konkrete eksempler!**

* 
* http://rpubs.com/kaz_yos/case-control1/


**Mest relevante pakker til biostatistik**
------

- dplyr - Subsetting, summarizing, rearranging, and joining together data sets.
- vcd - Visualization tools and tests for categorical data.
- foreign - Want to read a SAS data set into R? Or an SPSS data set?
- tidyr - Changes the layout of your data sets, converts into tidy format by gather and spread functions.
- multcomp - Tools for multiple comparison testing.
- survival - Tools for survival analysis.
- stringr - Easy to learn tools for regular expressions and character strings.
- lubridate - Tools that make working with dates and times easier.


## Nyttige funktioner og pakker
------

#### Indlæs data fra database
        
``` 
RMySQL, RPostgresSQL, RSQLite 
```
        
**Indlæs og skriv data til Excel**
        
```
XLConnect, xlsx 
```
                
## 5. Datavisualisering
------
 
        
#### 1. Indlæs din dataframe (data i tabelformat)
                        
```
grafdata <- read.table("minedata.txt", header = TRUE)
```
		
Eller
		
``` 
grafdata <- read.csv("minedata.csv") 
```
                
#### 2. Basal datavisualisering
                
##### Histogram
                
**Brug den indbyggede funktion hist()**
                
```
> hist(grafdata) 
```
                
##### Box Plot
                
**Brug den indbyggede funktion boxplot()**
                        
```
> boxplot(grafdata) 
```     
     
#### 3. Udviddet datavisualisering
        
**Brug datavisualiseringspakker, eksempelvis den populære ggvis()**
        
```
install.packages("ggvis") 
```
		             
``` 
library(ggvis) 
```            
        
**Flere populære pakker til datavisualisering**
        
- ggplot2 - R's famous package for making beautiful graphics.

- ggvis - Interactive, web based graphics built with the grammar of graphics.

- rgl - Interactive 3D visualizations with R.

- htmlwidgets - A fast way to build interactive (javascript based) visualizations with R. 

   - Packages that implement htmlwidgets include:

	- leaflet (maps)
	- dygraphs (time series)
	- DT (tables)
	- diagrammeR (diagrams)
	- network3D (network graphs)
	- threeJS (3D scatterplots and globes)
	- googleVis - Let's you use Google Chart tools to visualize data in R. 

## 6. Gem data til fil
------

```
> dat <-read.table(”filename”, header=T, sep=”\t”, row.names=1)
```

**En dataframe (“dat”) er formateret som en tabel.**

**Derfor indeholder en dataframe kolonner og rækker med data.**

* If every column contains a title, then argument should be header=TRUE (or header=T), otherwise header=F.
* If the file is tab-delimited, then sep=”\t”. Other options are, e.g., sep=”,” and sep=” ”.
* If every case (row) has it’s own non-repeating title, and the first column of the file contains these row name
* then row.names=1, otherwise the argument should be deleted.

```
> write.table(dat, ”dat.txt”, sep=”\t”, quote=F, row.names=T, col.names=T)
```
* dat name of the table in R

* ”dat.txt” name of the file on disk

* sep=”\t” use tabs to separate columns

* quote=F don’t quote anything, not even text

* row.names=T write out row names (or F if there are no row names)

* col.names=T write out column names



 6. Model data
------
        
- car - car's Anova function is popular for making type II and type III Anova tables.
 
- mgcv - Generalized Additive Models
 
- lme4/nlme - Linear and Non-linear mixed effects models
 
- randomForest - Random forest methods from machine learning
 
- multcomp - Tools for multiple comparison testing
 
- vcd - Visualization tools and tests for categorical data
 
- glmnet - Lasso and elastic-net regression methods with cross validation
 
- survival - Tools for survival analysis

- caret - Tools for training regression and classification models


 Report results
------
        
- shiny - Easily make interactive, web apps with R.

- R Markdown - Reporting. Export your report as an HTML, pdf, or MS Word document, or a HTML or pdf slideshow.

- xtable - The xtable function takes an R object (like a data frame) and returns the latex or HTML code to embed.

 
## 8. Spatial data
------

- sp, maptools - Tools for loading and using spatial data including shapefiles.

- maps - Easy to use map polygons for plots.

- ggmap - Download street maps straight from Google maps and use them as a background in your ggplots.


Time Series and Financial data
------

- zoo - Provides the most popular format for saving time series objects in R.

- xts - Very flexible tools for manipulating time series data sets.

- quantmod - Tools for downloading financial data, plotting common charts, and doing technical analysis.


10. Work with the web
------

- XML - Read and create XML documents with R

- jsonlite - Read and create JSON data tables with R

- httr - A set of useful tools for working with http connections


## 7. Begreber
------

* testthat - testthat provides an easy way to write unit tests for your code projects.

* roxygen2 - Document your R packages, turns inline code comments into pages.


## 8. Ressourcer
------
* https://www.statmethods.net/

* https://www.r-bloggers.com/

* https://rseek.org/

* https://support.rstudio.com/hc/en-us/articles/200552336
        
* https://www.youtube.com/watch?v=T5uMTKHoiHE&index=1&list=PLIUXJDHaV5ppQ53AVcUMpC3c9w51g6OQ

## 9. Todo
------
