+++
title = "{{ replace .TranslationBaseName "-" " " | title }}"
date = {{ .Date }}
draft = false

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = []
categories = []

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
# Use `caption` to display an image caption.
#   Markdown linking is allowed, e.g. `caption = "[Image credit](http://example.org)"`.
# Set `preview` to `false` to disable the thumbnail in listings.
[header]
image = ""
caption = ""
preview = true
+++

Note: for a _blog post_ make sure that the tags and categories are like this in the YAML front matter

```
tags:
  - blog
categories:
  - blog
```


```{r setup, echo = FALSE, message = FALSE, warning = FALSE}
## For R images to display well in the RSS feed (disable for local preview)
knitr::opts_knit$set(base.url = 'http://rladies-baltimore.github.io/post/')

## Load frequently used packages for blog posts
library('knitcitations') # for citations
library('BiocStyle') # for CRANpkg() Biocpkg() Githubpkg()
library('sessioninfo') # for session_info()

## Load knitcitations with a clean bibliography
cleanbib()
cite_options(hyperlink = 'to.doc', citation_format = 'text', style = 'html')

bib <- c(
    'BiocStyle' = citation('BiocStyle'),
    'blogdown' = citation('blogdown')[2],
    'knitcitations' = citation('knitcitations'),
    'sessioninfo' = citation('sessioninfo')
)
```


### Post content

Typical location to start editing since the bibliography chunk is hidden. Make sure that you selected `R Markdown (.Rmd)` as the _format_ option of the post when using the `New Post` `r CRANpkg('blogdown')` addin.

### R image


```{r 'plot', echo = TRUE, fig.width = 6, fig.height = 6, eval = FALSE}
## This imaged will be saved in the /post/*_files/ directory
## Use echo = FALSE if you want to hide the code for making the plot
plot(1:10, 10:1)
```

If you prefer not to use the `fig.width` and `fig.height` options in every plot chunk, edit the YAML (the part at the top of the post) with:

```
output:
  blogdown::html_page:
    toc: no
    fig_width: 5
    fig_height: 5
```

The spaces are important.

### Custom image

The easiest option is to use the `r CRANpkg('blogdown')` _Insert Image_ RStudio addin to add an external image described in this [blog post](http://lcolladotor.github.io/2018/03/07/blogdown-insert-image-addin). You need to use version 0.5.7 or newer to have access to this plugin. 

If you want to add images manually, check this [blog post](http://lcolladotor.github.io/2018/02/17/r-markdown-blog-template/#.WqChJZPwa50) for more details on the image syntax.


### Acknowledgements


This blog post was made possible thanks to:

* `r Biocpkg('BiocStyle')` `r citep(bib[['BiocStyle']])`
* `r CRANpkg('blogdown')` `r citep(bib[['blogdown']])`
* `r CRANpkg('knitcitations')` `r citep(bib[['knitcitations']])`
* `r CRANpkg('sessioninfo')` `r citep(bib[['sessioninfo']])`

### References

```{r bibliography, results = 'asis', echo = FALSE, cache = FALSE}
## Print bibliography
bibliography(style = 'html')
```

### Reproducibility

```{r reproducibility, echo = FALSE}
## Reproducibility info
options(width = 120)
session_info()
```
