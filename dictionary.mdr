The following table provides some quick translations of Stata commands into R.  Since R supports multiple data sets, we need to specify a specific data set to manipulate when using data accessing/modifying commands. We use mydata as the default data set to target. 

Stata                         | R                                          | Description
------------------------------|--------------------------------------------|------------------------------
insheet using "foo.csv", comma| mydata <- read.csv("foo.csv")              | Read csv file
cd "mydirectory"              | setwd("mydirectory")                       | Change working directories
reg y x1 x2                   | summary(lm(y~x1+x2, data=mydata))          | Ordinary least squares with constant
reg y x1 x2, nocon            | summary(lm(y~x1+x2-1, data=mydata))        | Ordinary least squares without constant
if (x==y) {...}               | if (x==y) {...}                            | Initial line condition use to evaluate whether a command(s) should be exectuted
reg y x if (x>0)              | lm(y~x, data=mydata[mydata$x>0,])          | Select a conditional subset of data
forvalues i=1/100 {...}       | for (i in 1:100) {...}                     | Loop through integer values of i from 1 to 100
foreach i in "a" "b" "c" {...}| for (i in c("a","b","c")) {...}            | Loop through a list of items
di "Hello World"              | print("Hello World")                       | Prints "hello world" on screen
do "mydofile.do"              | source("myRscript.R")                      | Call and run code file
use "mydata.dta", clear       | load("mydata.Rdata")                       | Load saved workspace/data
save "mydata.dta", replace    | save.image("mydata.Rdata")                 | Save current workspace/data
di 2345^2                     | 2345^2                                     | Calculate 2345 squared
logit y x                     | summary(glm(y~x,data=mydata,family="binomial"))| Perform logit maximum likelihood estimation
probit y x                    | summary(glm(y~x,data=mydata,family=binomial(link = "probit")))| Perform probit maximum likelihood estimation
sort x y                      | mydata[order(mydata$x, mydata$y),]         | Sort the data frame by variable x
cor x y                       | cor(x,y)                                   | Produce a table of correlates between x and y
help command                  | 1. ?command <br> 2. help(command)          | Load the help file on a command
edit                          | edit(mydata)                               | Open data editor window (not recommended)
summarize                     | summary(mydata)                            | Provide summary values for data
table x y                     | table(mydata$x,mydata$y)                   | Two way table
hist x                        | hist(mydata$x)                             | Histogram of variable x
scatter x y                   | plot x y                                   | Scatter plot of x on y
list                          | mydata                                     | Print to screen all of the values of the data frame
list in 1/5                   | 1. head(mydata) <br> 2. mydata[1:5,]       | Print to screen first 5 rows of data
generate x2=x^2               | mydata$x2 <- mydata$x^2                    | Create a new variable x2 which is the square of x
replace x=y1+y2               | 1. mydata$x <- mydata$y1 + mydata$y2 <br> 2.  mydata$x <- with(mydata, y1 + y2) | Change the x value of data to be equal to y1+y2
for i=1/10 {<br> di `i' <br> } | for (i in 1:10) print(i)                  | Print count from 1 to 10
replace x=0 if x<0             | mydata$x[mydata$x<0] <- 0                 | Replace all values of x less than 0 with zero
drop if x>100                  | mydata <- mydata[!mydata$x>100,]          | Drop observations with x greater than 100
keep if x<100                  | mydata <- mydata[mydata$x<100,]           | Keep observations with x less than 100
drop x                         | mydata$x <- NULL                          | Drop variable x from the data
keep x                         | mydata <- mydata$x                        | Keep only x in the data
append using "mydata2.dta"     | mydata <- rbind(mydata, mydata2)          | Append mydata2 to mydata
merge 1:1 index using "mydata2.dta" | merge(mydata,mydata2,index)          | Merge two data sets together by index variable(s)
set obs 1000 <br> gen x=rnormal() | mydata$x <- rnorm(1000)                | Generate 1000 random normal draws
set obs 1000 <br> gen x=runiform() | mydata$x <- runif(1000)                | Generate 1000 random uniform draws
set obs 1000 <br> gen x=rbinomial(10,.1) | mydata$x <- rbinom(1000, 10, .1) | Generate 1000 random binomial (10,.1) draws
count                          | nrow(mydata)                               | Count the number of observations in the data
foreach v of varlist * { <br> rename \`v' \`v'old <br> } | names(mydata) <- paste0(names(mydata),"old") | Rename all of the variables in the data ...old
clear <br> set obs 100 <br> gen x=rnormal(100) <br> gen y=x*2 + rnormal(100)*5 | mydata<-data.frame(x=x<-rnorm(100), y=x*2 + rnorm(100)*5)| Simulate a new data set with y dependent upon x
egen id = group(x y)           | 1. within(mydata, {ID <- ave(ID, list(x, y), FUN=seq_along)}) <br> 2. mydata$ID <- with(mydata, ave(ID, list(x, y), FUN=seq_along)) <br> 3. mydata$ID <- ave(ID, list(mydata$x, mydata$y), FUN=seq_along)| Create an identifier ID from variables x and y
