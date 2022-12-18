# Chapter 1

- Comparison of R and SAS
  - big diff is that SAS is not object oriented. It revolves around tables
- Basic structure of a SAS program
  - proc and data statements
  - other statements
  - run or quit
- Sintax
  - not case sensitive
  - statements end in semicolons
- Comments
  - sintax depends on context
- Interface
  - code, log and results tabs
- libraries
  - all permanent, except work
  - libname statement to register and access a library
  - `library.dataset` sintax

# Chapter 2

- creating a dataset by hand
  - datalines statement
  - length and input statements
  - multiple rows in one line and different delimitations
- importing data set from a file
  - data way: infile statement
  - proc way: import statement
    - renaming variables with `rename`
- reporting data
  - proc contents: summary of the data
  - `proc print`: showing rows of data
  - `where` to print conditionally
  - `proc sql` for full SQL functionality
  - comparison and logical operators
  - `label` to display names of columns
  - `format` to select how to display variables
    - dates
      - stored in SAS with JAN11960 as ref
      - displayed using predefined formats
    - `proc format` to create user-defined formats
    - using informats (: operator) to set format when inputing
    - you can use `format` and `label` in a `data` statement
    - you have to use `label` option in `print` to make SAS actually use the labels

# Chapter 3

- creating new variables
  - `set` statement to alter a given dataset
  - conditional numerical variables using if-else
  - caracter variables are similar, but you should specify `length` first
  - for more general computations that require several statements, use `do`. it always ends with `end`
  - using functions
    - same sintax as R, as long as you're applying row-wise
    - list of functions to apply to character variables
    - defining functions to apply row-wise using `proc fcmp`
      - stored in packages inside libraries
    - using the `options cmplib =` to load the functions inside a dataset
- subsetting data
	- `keep` statement to select a set of variables from an existing dataset 
	- `drop` to select all but some of the variables 
	- `firstobs` and `obs` to select rows 
	- `where` to select rows that meet criteria 
- concatenating datasets
	- rbind with `set`
	- multiple `set` statements to rbind 
	- `merge` to cbind with different dimensions
	- `merge` has all the usual considerations of joins 

# Chapter 4

- `do` loop
	- It basically creates an iter, along which you can generate new variables
	- the iter gets recorded as a column by default
	- use `keep` and `drop` to select which variables get recorded 
	- they can be nested
	- `set` to create a new varible along the rows of an existing dataset
	- `sum` statement to just count 
- random number generation 
	- `rand` to generate random variates 
	- associated probability functions
- plotting
	- `plotname x=variable y=variable` sintax for most plots 
	- `by` statements to facet 
	- `sgscatter` to create multipanel plot
		- `matrix` to recreate pairs 
		- `plot` to generate multiple scatter plots 
	- `ods layout`
	- `sgpanel`, `panelby` 

# Chapter 5

- descriptive statistics 
	- `mean` will also print stuff that you would see in R's summary
	- `univariate` is like a catch all 
- ODS
	- SAS code just produces the numbers, the ODS creates the formatted tables
	- `ods select` before the `proc` to select some of the output 
	- `ods output` to save output to a new dataset 
	- `output out` statement to save specific statistics 
- macro variables 
	- `%let` and `&` sintax to create global variables
	- Using quotation marks to resolve character variables 
	- Using `proc sql` and `:` sintax to create global variables automatically
	- `%put` to print stuff to the log
- macro programs 
	- `%macro` and `%` sintax to create and call macros 
	- positional and keyword parameters 
	- Macro statements 
		- `%if`, `%then` and `%else% to run SAS code conditionally
		- `%do% and `%end` to run several lines of code
		
# Chapter 6 

- Linear models 
	- `proc reg` and `model` is the basic sintax 
	- `store` to save the model
	- `proc plm` to predict based on a model
	- `glm` for general linear models, specifically for anova
	- `proc glmselect` to perform model selection
	- `proc logistic` for logistic regression
	- `proc genmod` for generalized linear models 
	- `proc mixed` to code mixed effects models
	- `proc glimmix` for generalized linear models with mixed effects 
	- `proc mcmc` to implement MCMC

# Chapter 7 

- basics 
	- braces to enter matrices by hand 
	- matrices have to be of single type
	- `print` statement to see stuff 
	- accessing entries and obtaining dimentions is basically the same as in R
	- basic and comparison operators 
	- recycling works a little different: it's mindful of whether the small object is a row or column
	- subscript reduction operators are similar to apply for a established set of operators
- modules and subroutines 
	- distinction between functions and subroutines 
	- `J` and `randgen` subroutines to create a random matrix
	- `randfun` to create random vectors
	- most common matrix functions are just like in R
	- `repeat`, `concat`, `any`, `all`, `sample`, `unique`
	- creating a module
		- global arguments for functions
		- creating multiple matrices with subroutines 
	- storage 
		- 
