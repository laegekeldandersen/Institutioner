# RStudio - Survival guide

## Opsætning

### Installer R
#### R-statistics (https://www.r-project.org/)
#### RStudio (https://www.rstudio.com/)

### Working directory
#### Se aktuelle: getwd()
#### Vælg nyt: setwd(“C://file/path”)

### Installer relevante pakker
#### Packages -> Select repository
#### Packages  -> Install packages
#### install.packages("<the package's name>")

#### Load pakke: library(<the package's name>)

### Importer eller åben data
####read.csv(file=”myfile”)



## Diskriptiv statistik
### Funktioner
#### 1. sapply() *1
#### 2. summary(mydata)
#### 3. describe(mydata)
#### 4. stat.desc(mydata)
#### 5. describe(mydata)
#### 6. 


## Statistisk analyse


## Eksporter eller gem data

Installering


Opsætning
Arbejdsbibliotek ("working directory")

Definér: setwd("~/Test") eller 

Klargør rådata
Korrekt og konsistent formatering og type af data
Data til import i R::
Indlæs data fra Excel
Indlæs data fra SAS og SPSS
Indlæs data fra CSV fil (mellemrum, tabulatur, kolon, komma)
Kommandoer i konsolen
Åben data 
Load relevant pakke*. Mest relevante biostatistics packages:

dplyr - Essential shortcuts for subsetting, summarizing, rearranging, and joining together data sets.
vcd - Visualization tools and tests for categorical data.
foreign - Want to read a SAS data set into R? Or an SPSS data set?
tidyr - Tools for changing the layout of your data sets. Use the gather and spread functions to convert your data into the tidy format.
multcomp - Tools for multiple comparison testing.
survival - Tools for survival analysis




library("<the package's name>")



Importer data fra fil:

dat <-read.table(”filename”, header=T, sep=”\t”, row.names=1)

“dat” som det er anført ovenfor i a. Kaldes en dataframe, hvis “filename” er formateret som en tabel. Derfor indeholder en dataframe kolonner og rækker med data.

If every column contains a title, then argument should be header=TRUE (or header=T), otherwise header=F.

If the file is tab-delimited (there is a tab between every column), then sep=”\t”. Other options are, e.g., sep=”,” and sep=” ”
If every case (row) has it’s own unambiquous (non-repeating) title, and the first column of the file contains these row names, then row.names=1, otherwise the argument should be deleted.

 3. Benyt indbyggede datasæt i R:

http://www.sthda.com/english/wiki/r-built-in-data-sets

Arbejd med data
Basal datamanipulation

Se importeret data værdier i dataframen (tabellen): > dat

Se alle variable (kolonner) i dataframen (tabellen): > ls() 

Lav ny dataframe (tabel) med specifikke variable (kolonner): > 

# select variables v1, v2, v3
myvars <- c("v1", "v2", "v3")
newdata <- mydata[myvars]

To choose only certain columns, you use the select() function with syntax such as select(dataframename, columnName1, columnName2). No quotation marks are needed with the column names:

select(mtcars, mpg, hp)

Statistiske tests

Deskriptiv Statistik
Statistiske funktioner til case-control studies 

	http://rpubs.com/kaz_yos/case-control1
Visualiser data 
Gem data 
write.table(dat, ”dat.txt”, sep=”\t”, quote=F,
row.names=T, col.names=T)
• dat name of the table in R
• ”dat.txt” name of the file on disk
• sep=”\t” use tabs to separate columns
• quote=F don’t quote anything, not even text
• row.names=T write out row names (or F if there are no row names)
• col.names=T write out column names


*Nyttige R-packages

To load data
RMySQL, RPostgresSQL, RSQLite - If you'd like to read in data from a database, these packages are a good place to start. Choose the package that fits your type of database.

XLConnect, xlsx - These packages help you read and write Micorsoft Excel files from R. You can also just export your spreadsheets from Excel as .csv's.

foreign - Want to read a SAS data set into R? Or an SPSS data set? Foreign provides functions that help you load data files from other programs into R.

R can handle plain text files – no package required. Just use the functions read.csv, read.table, and read.fwf. If you have even more exotic data, consult the CRAN guide to data import and export.

To manipulate data
dplyr - Essential shortcuts for subsetting, summarizing, rearranging, and joining together data sets. dplyr is our go to package for fast data manipulation.

tidyr - Tools for changing the layout of your data sets. Use the gather and spread functions to convert your data into the tidy format, the layout R likes best.

stringr - Easy to learn tools for regular expressions and character strings.

lubridate - Tools that make working with dates and times easier.

To visualize data
ggplot2 - R's famous package for making beautiful graphics. ggplot2 lets you use the grammar of graphics to build layered, customizable plots.

ggvis - Interactive, web based graphics built with the grammar of graphics.

rgl - Interactive 3D visualizations with R

htmlwidgets - A fast way to build interactive (javascript based) visualizations with R. Packages that implement htmlwidgets include:

leaflet (maps)
dygraphs (time series)
DT (tables)
diagrammeR (diagrams)
network3D (network graphs)
threeJS (3D scatterplots and globes).
 

googleVis - Let's you use Google Chart tools to visualize data in R. Google Chart tools used to be called Gapminder, the graphing software Hans Rosling made famous in hie TED talk.

To model data
car - car's Anova function is popular for making type II and type III Anova tables.

mgcv - Generalized Additive Models

lme4/nlme - Linear and Non-linear mixed effects models

randomForest - Random forest methods from machine learning

multcomp - Tools for multiple comparison testing

vcd - Visualization tools and tests for categorical data

glmnet - Lasso and elastic-net regression methods with cross validation

survival - Tools for survival analysis

caret - Tools for training regression and classification models

To report results
shiny - Easily make interactive, web apps with R. A perfect way to explore data and share findings with non-programmers.

R Markdown - The perfect workflow for reproducible reporting. Write R code in your markdown reports. When you run render, R Markdown will replace the code with its results and then export your report as an HTML, pdf, or MS Word document, or a HTML or pdf slideshow. The result? Automated reporting. R Markdown is integrated straight into RStudio.

xtable - The xtable function takes an R object (like a data frame) and returns the latex or HTML code you need to paste a pretty version of the object into your documents. Copy and paste, or pair up with R Markdown.

For Spatial data
sp, maptools - Tools for loading and using spatial data including shapefiles.

maps - Easy to use map polygons for plots.

ggmap - Download street maps straight from Google maps and use them as a background in your ggplots.

For Time Series and Financial data
zoo - Provides the most popular format for saving time series objects in R.

xts - Very flexible tools for manipulating time series data sets.

quantmod - Tools for downloading financial data, plotting common charts, and doing technical analysis.

To write high performance R code
Rcpp - Write R functions that call C++ code for lightning fast speed.

data.table - An alternative way to organize data sets for very, very fast operations. Useful for big data.

parallel - Use parallel processing in R to speed up your code or to crunch large data sets.

To work with the web
XML - Read and create XML documents with R

jsonlite - Read and create JSON data tables with R

httr - A set of useful tools for working with http connections

To write your own R packages
devtools - An essential suite of tools for turning your code into an R package.

testthat - testthat provides an easy way to write unit tests for your code projects.

roxygen2 - A quick way to document your R packages. roxygen2 turns inline code comments into documentation pages and builds a package namespace.

You can also read about the entire package development process online in Hadley Wickham's R Packages book

Ressources
https://support.rstudio.com/hc/en-us/articles/200552336
https://www.youtube.com/watch?v=T5uMTKHoiHE&index=1&list=PLIUXJDHaV5ppQ53AVcUMpC3c9w51g6OQ_


