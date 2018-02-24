# RStudio - Survival guide
---
## Opsætning
### Installér R
#### R-statistics <https://www.r-project.org/>
#### RStudio <https://www.rstudio.com/>
### Working directory (WD)
#### Aktuelle WD

`` > getwd() ``

#### Skift WD
`` > setwd(“C://file/path”) ``

Eller  

`` > setwd("~/Test") ``

---
### Installer relevante pakker

```
> install.packages("<the package's name>")
```

### Indlæs pakke

```
> library(<the package's name>)
```

### Importer eller åbn data

`` > read.csv(file=”myfile”) ``

### Gem tabelformateret data fra fil til tabel i R

`` > dat <-read.table(”filename”, header=T, sep=”\t”, row.names=1) ``

	• “dat” Kaldes en dataframe, hvis den er formateret som en tabel. 
	• Derfor indeholder en dataframe kolonner og rækker med data.
	• If every column contains a title, then argument should be header=TRUE (or header=T), otherwise header=F.
	• If the file is tab-delimited, then sep=”\t”. Other options are, e.g., sep=”,” and sep=” ”.
	• If every case (row) has it’s own non-repeating title, and the first column of the file contains these row name
	• then row.names=1, otherwise the argument should be deleted.


## Diskriptiv statistik
---
### Funktioner

#### 1. Indbygget

`` > sapply(mydata) ``

	Output: mean, sd, var, min, max, median, range, and quantile. Ekskluderer manglende værdier

#### 2. Indbygget

`` > summary(mydata) ``

	Output: mean,median,25th and 75th quartiles,min,max

#### 3. Hmisc-pakken

```
> install.packages("hmisc")
> library(Hmisc)
> describe(mydata) 
```
	Output: n, nmiss, unique, mean, 5,10,25,50,75,90,95th percentiles, the 5 lowest and 5 highest scores.

#### 4. Pastecs-pakken

```
> install.packages("pastecs")
> library(pastecs)
> stat.desc(mydata) 
```
	Output: nbr.val, nbr.null, nbr.na, min max, range, sum, median, mean, SE.mean, CI.mean, var, std.dev, coef.var

#### 5. Psych-pakken

```
> install.packages("psych")
> library(psych)
> describe(mydata)
```
	Output: item name ,item number, nvalid, mean, sd, median, mad, min, max, skew, kurtosis, se

## Statistiske analyser
---
### Case-control studies

#### 1. <http://rpubs.com/kaz_yos/case-control1/>

## Eksporter eller gem data i fil
---
`` > write.table(dat, ”dat.txt”, sep=”\t”, quote=F, row.names=T, col.names=T) ``

	• dat name of the table in R
	• ”dat.txt” name of the file on disk
	• sep=”\t” use tabs to separate columns
	• quote=F don’t quote anything, not even text
	• row.names=T write out row names (or F if there are no row names)
	• col.names=T write out column names

## Mest relevante biostatistics pakker
---
	• dplyr - Subsetting, summarizing, rearranging, and joining together data sets.
	• vcd - Visualization tools and tests for categorical data.
	• foreign - Want to read a SAS data set into R? Or an SPSS data set?
	• tidyr - Changes the layout of your data sets, converts into tidy format by gather and spread functions.
	• multcomp - Tools for multiple comparison testing.
	• survival - Tools for survival analysis.
	• stringr - Easy to learn tools for regular expressions and character strings.
	• lubridate - Tools that make working with dates and times easier.
	

## Indbyggede datasæt i R
---
####	<http://www.sthda.com/english/wiki/r-built-in-data-sets/>

## Basale funktioner
---
### Se importeret dataværdier i dataframe (tabel)

	`` > dat ``
	
### Se alle variable (kolonner) i dataframen (tabellen)
	
	`` > ls() ``
	
### Lav ny dataframe (tabel) med specifikke variable (kolonner)
	```
	> myvars <- c("v1", "v2", "v3")
	> newdata <- mydata[myvars]
	```
### Choose only certain columns with select(dataframename, columnName1, columnName2)
	
	`` > select(mtcars, mpg, hp) ``
	
## Nyttige funktioner og pakker
---
### Indlæs data fra database
	
	`` RMySQL, RPostgresSQL, RSQLite ``
	
### Indlæs og skriv data til Excel
	
	`` XLConnect, xlsx ``
	
### Indlæs data fra SAS, SPSS mv. i R
	
	`` foreign ``
	
### Indlæs data fra tekstfiler (indbygget i R)
	
	`` read.csv, read.table, and read.fwf. ``
	
## Visualiser data
---
	ggplot2 - R's famous package for making beautiful graphics.

	ggvis - Interactive, web based graphics built with the grammar of graphics.

	rgl - Interactive 3D visualizations with R.

	htmlwidgets - A fast way to build interactive (javascript based) visualizations with R. 
	
		Packages that implement htmlwidgets include:

			leaflet (maps)
			dygraphs (time series)
			DT (tables)
			diagrammeR (diagrams)
			network3D (network graphs)
			threeJS (3D scatterplots and globes)
 			googleVis - Let's you use Google Chart tools to visualize data in R. 

## To model data
---
	car - car's Anova function is popular for making type II and type III Anova tables.

	mgcv - Generalized Additive Models

	lme4/nlme - Linear and Non-linear mixed effects models

	randomForest - Random forest methods from machine learning

	multcomp - Tools for multiple comparison testing

	vcd - Visualization tools and tests for categorical data

	glmnet - Lasso and elastic-net regression methods with cross validation

	survival - Tools for survival analysis

	caret - Tools for training regression and classification models

## Report results
---
	shiny - Easily make interactive, web apps with R.

	R Markdown - Reporting. Export your report as an HTML, pdf, or MS Word document, or a HTML or pdf slideshow.

	xtable - The xtable function takes an R object (like a data frame) and returns the latex or HTML code to embed.

## Spatial data
---
	sp, maptools - Tools for loading and using spatial data including shapefiles.

	maps - Easy to use map polygons for plots.

	ggmap - Download street maps straight from Google maps and use them as a background in your ggplots.

## Time Series and Financial data
---
	zoo - Provides the most popular format for saving time series objects in R.

	xts - Very flexible tools for manipulating time series data sets.

	quantmod - Tools for downloading financial data, plotting common charts, and doing technical analysis.

## High performance R code
---	
	Rcpp - Write R functions that call C++ code for lightning fast speed.

	data.table - An alternative way to organize data sets for very, very fast operations. Useful for big data.

	parallel - Use parallel processing in R to speed up your code or to crunch large data sets.

## Work with the web
---
	XML - Read and create XML documents with R

	jsonlite - Read and create JSON data tables with R

	httr - A set of useful tools for working with http connections

## Diverse
---
	testthat - testthat provides an easy way to write unit tests for your code projects.

	roxygen2 - Document your R packages, turns inline code comments into pages.

## Yderligere ressourcer
---
#### 1.	<https://support.rstudio.com/hc/en-us/articles/200552336>
	
#### 2.	<https://www.youtube.com/watch?v=T5uMTKHoiHE&index=1&list=PLIUXJDHaV5ppQ53AVcUMpC3c9w51g6OQ>


