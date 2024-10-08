dplyr
================

# Data transformation with dplyr: Part 1

The dplyr package includes functions that you can use to transform a
data frame:

- functions that operate on rows:

  - filter() changes which rows are present without changing their order

  - arrange() changes the order of rows without changing which rows are
    present

  - distinct() finds rows with unique values

- functions that operate on columns:

  - mutate() creates new columns based on existing columns

  - select() changes which columns are present

  - rename() changes the names of columns

  - relocate() changes the positions of columns

- Once you understand these functions, we can combine them using the
  pipe operator.

- We’ll also use functions that work with groups:

  - group_by()

  - summarize()

  - slice()

  - ungroup()

# Useful keyboard shortcuts:

*Cmd/Ctrl+Shift+Enter* runs code chunk (make sure your cursor is in the
code chunk to make it active)

*Cmd/Ctrl+Enter* runs current line of code

*Cmd/Ctrl+Shift+M* pipe operator (%\>%)

*Option+-* (Mac) assignment operator (\<-)

*Alt+-* (Windows) assignment operator (\<-)

# Data set and packages:

We’ll be using a dataset of flights departing from New York City in
2013. This data is available in a package called nycflights13.

This lecture is based on [Chapter
3](https://r4ds.hadley.nz/data-transform) of R for Data Science.

We’ll start by installing the necessary packages in the console and then
load the libraries in the code chunk.

You do not need to install the packages every time you open R, which is
the reason you install them in the Console. You also do not want to
include them in R script files that others will use. If you have not
installed the package already, attempting to load the library will give
you error text in this format:

Error in library(packagename) : there is no package called ‘packagename’

Here is the format for install.packages:

install.packages(“packagename”)

You do need to load libraries every session:

library(packagename)

Note the difference in usage of quotation marks!

These are the packages we’ll be using in this session:

- tidyverse

- dplyr

- nycflights13

# Exploring the flights dataframe

Wait, what’s a dataframe? Time for some common terminology:

In the tidyverse, a data frame is rectangular data with variables in
columns and observations in the rows.

A variable (column) will be an attribute of all flights, and an
observation (row) is all the attributes of a single flight.

Here are a few ways you can look at a data frame:

- Type the name to see a preview of the contents

- Use glimpse(dataframe) to see all the variables and a few observations

- Use View(dataframe) to open a data viewer in RStudio

- To learn more about an R data package, use ?dataframe

# General dplyr function commonalities:

The first argument is always a data frame.

Subsequent arguments describe which columns to operate on using the
variable names.

The output is always a new data frame.

Often we’ll need to combine multiple functions, using the pipe %\>%. One
way to read the pipe is to think of it as “and then.” We can start using
the pipe with a single function, too.

dplyr functions never modify the inputs. If you want to save the new
data frame for later, you assign it to a new object using the assignment
operator (\<-). Assignment operator shortcuts:

*Option+-* (Mac) assignment operator (\<-)

*Alt+-* (Windows) assignment operator (\<-)

# Filter()

filter() changes which rows are present without changing their order

**Question: How many flights had a departure delay longer than 3
hours?**

``` r
# use filter without pipe

# use filter with pipe

# create a new data frame called flights_delay_180
```

The new flights_delay_180 now appears in your Environment pane. You can
use this new data frame later.

In this first example, we used \> greater than. Other conditions
include:

- \>= greater than or equal to

- \< less than

- \<= less than or equal to

- == equal to

- != not equal to

You can also combine conditions:

- & “and”

- \| “or”

**Question: Which flights departed on September 17, 2013?**

**Check-in question: What columns do we need to use to set our
conditions?**

# Arrange()

arrange() changes the order of rows without changing which rows are
present

**Task: Arrange the flights by departure time.**

**Check-in question: Which column(s) do we need to use to arrange the
data frame?**

``` r
# different interpretation
```

desc() can be used inside arrange () to reorder the data frame in
descending order.

**Task: Arrange the data frame to find the longest departure delay.**

# Distinct()

distinct() finds rows with unique values

**Question: Are there any duplicate rows?**

**Question: How many unique origin and destination pairs are there in
this data frame?**

# More practice with filter(), arrange(), and distinct()

[3.2.5 Exercises in
R4DS](https://r4ds.hadley.nz/data-transform#exercises)

You can include answers to one or many of these exercises in your
submission for Assignment 2. This is one way to demonstrate large gains
of skills and concepts, especially if you already have R experience from
DATA 3001.
