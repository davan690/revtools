This repository is an extention of Martin Westgate from the Australian National University. 

The aims of this project are to extend the revtools package developed from Martin's work to produce reproducible meta-research and an extended `sentiment analysis` for demographic modelling in NZ forest systems. 

## Additional to `revtools`

*Not much yet sorry.* I am currently working on:

- turning this into a gitbook in vignette file?
- link with online editor/shiny?

My concept for PFNZ extention (Oct 2019):

- Collect bibliography from search engines like google scholar
- Import references from a single paper and analysis
- Create process diagrams for the workflow.
- Link this with a database structure such as Zotero as an add-in

## `revtools`

<img align="left" height="120" src="https://github.com/mjwestgate/revtools_website/blob/master/assets/img/revtools_hex.png"><b>revtools v0.4.1:For a complete introduction to revtools you can check out the [user manual](https://revtools.net/); but to get started now you can download revtools either from this site (development version) or CRAN (stable version) as follows:</b>

Tools to support literature review and evidence synthesis in R, including import, de-duplication and interactive display of bibliographic data.

```{r}
install.packages("revtools") # install from CRAN
devtools::install_github("mjwestgate/revtools") # install from GitHub
library(revtools) # load
```

For a complete introduction to revtools you can check out the [website](https://revtools.net/); but to get started now you can download revtools either from this site (development version) or CRAN (stable version) as follows:

Once you've installed & loaded revtools, you can use any of the inbuilt apps by loading them and drag-and-dropping the data you want to analyse. All the apps export to csv format so you don't need to use R to investigate their results if you'd prefer not to. The apps available in revtools are:

- <code>screen_duplicates()</code> to investigate potential duplicates within a dataset
- <code>screen_titles()</code> to screen articles by title
- <code>screen_abstracts()</code> to screen articles by abstract
- <code>screen_topics()</code> to run topic models on bibliographic data

If you're a keen to investigate your data in the R workspace, revtools is designed to make data import as straightforward as possible. It does this by using a single function to import bibliographic data from bib, ris, ciw or csv formats:

```{r}
file_location <- system.file("extdata",
  "avian_ecology_bibliography.ris",
  package = "revtools")

# to import bibliographic information into a data.frame
data <- read_bibliography(file_location)
```

Then you can pass these data to your apps as you would with any other function:

```{r}
screen_topics(data) # runs using your data

# you can save progress to the workspace by specifying an object:
result <- screen_topics(data)

# or save to a file within the app, and reload that saved file:
y <- readRDS("saved_object.rds")
screen_topics(y)
```
