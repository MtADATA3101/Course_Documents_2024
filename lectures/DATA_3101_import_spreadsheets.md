Data Import: Spreadsheets
================

This class is based on [Chapter 7 Data
Import](https://r4ds.hadley.nz/data-import) and [Chapter 20
Spreadsheets](https://r4ds.hadley.nz/spreadsheets) from R4DS.

So far we’ve only worked with data provided from R packages (including
data from nycflights13, ….). This is a good way to get started with data
science tools like dplyr and to introduce data tidying ideas like
lengthening and widening data.

Usually, you’re going to be working with your own data, or reusing data
created by someone else. This means we need to practice getting data
into R.

### Readr, readxl, writexl, googlesheets4

readr, like dplyr, is part of the core tidyverse.

readr parses flat files (2D databases or tables) into tibbles. For more
on how this parsing process works, check out the [readr
vignette.](https://readr.tidyverse.org/articles/readr.html)

In this class we’ll talk about importing plain text files like .csv and
.tsv as well as spreadsheets from Excel or Google sheets.

We’ll need tidyverse for readr, and to load some new libraries: readxl,
writexl, and googlesheets4

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(readxl)
library(writexl)
library(googlesheets4)
```

#### Flat file from web link: Fish example

In a previous class, we looked at research data from a deposit in
Borealis:

Parker, Katya; El, Nir; Buldo, Elena; MacCormack, Tyson, 2023,
“Replication Data for: Parker et al. Mechanisms of PVP-functionalized
silver nanoparticle toxicity in fish: Intravascular exposure disrupts
cardiac pacemaker function and inhibits Na+/K+-ATPase activity in heart,
but not gill”, <https://doi.org/10.5683/SP3/FCDBBT>, Borealis, V1;
Figure 3A.tab \[fileName\], UNF:6:6Qrmtes/AAEkr3TwN3PVeA== \[fileUNF\]

Borealis provides a download URL that we can use for data import:

<https://borealisdata.ca/api/access/datafile/637561>

**Question: From the Borealis record, what is the delimiter for this
file? Will we use read_csv() or read_tsv() to import this data?**

Some of the typical things we can fix at the same time as we import the
file include: column names, data types, skipping extra rows at the
beginning of the file, and dropping empty rows.

In this case, skip_empty_rows = TRUE did not do what I would expect.
Let’s take a look at the csv and tsv files using a text editor.

Empty strings (““) are read in as NA values.

**Assignment extra challenge:**

**Find a way to skip that row as we import the data and share it with
the class as a discussion item in GitHub.**

Now we can tidy the new fish tibble.

What are some of the things we wanted to fix when we looked at this as
an example in the tidy data class?

#### Excel file added to R project: StatsCan example

Download data/2024_statscan_tech_adoption.xls from MtADATA3101.

Create a new folder in your repository called data.

Move the downloaded file into your data folder.

To work with Excel files, we need readxl, which we loaded at the
beginning of class.

readxl funtions are all about loading Excel spreadsheets:

- read_xls() reads Excel files with xls format

- read_xlsx() reads Excel fies with xlsx format

- read_excel() can read either xls or xlsx formats

Let’s load the data to test that we can find our new file:

This is a mess!!!

One thing to notice is that by default, R has loaded the first sheet. We
can specify the sheet in the read_excel() function.

Another is that we have lots of rows that are helpful for creating a
citation or noting the data quality, but not for analysis or
visualization. We can specify the range.

We can add meaningful column names, using col_names.

Now let’s do the same for New Brunswick:

You can join these together by using the bind_rows function:

What do we need to do to make this tidy?

- data types

- pivot_long

Write back to the data folder using writexl. We’ll need to install the
package and load the library.

#### Google sheets

We’ll use the penguin example from [Chapter 20 in
R4DS](https://r4ds.hadley.nz/spreadsheets#google-sheets)

Google Sheets are much like Excel files, with a few exceptions:

- [authentication](https://r4ds.hadley.nz/spreadsheets#authentication):
  unless you are accessing public resources, you will be prompted to
  authenticate with a gmail account. This can be avoided for public
  resources using gs4_deauth(), which suspends authorization.

- URLs for Google sheets are unpleasant! The suggestion is to save the
  ID as an object.

In this example, we’ll find out the names of the sheets in the penguins
Google Sheet, and then read in one of the sheets.

As with read_excel(), you can specify ranges to read in. You can also
write to a Google Sheet (but will likely need to authenticate.)
