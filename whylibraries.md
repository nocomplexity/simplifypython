# External Libraries

Solving problems with Python should be easy. The first thing to remember when hitting any problem is to remember this humble advise:

:::{tip}
It has been solved many times and properly better than you can do!
:::


The Python ecosystem consists of many solutions for all kinds of problems. The [Python Package Index (PyPI) repository](https://pypi.org/) contains nearly 600.000 packages. And this is only a fraction (!!) of the modules,notebooks and FOSS code that is available to be reused. 

Using an external library can give you an immense time profit. However if you want to keep things simple you SHOULD follow the key [NO|Complexity principles](https://nocomplexity.com/documents/0complexity/abstract.html).

This means dealing with the dilemma of:
1. Using an external library.
2. Increasing complexity, because adding extra dependencies will increase your security and maintenance effort.

:::{admonition} Simplify programming with Python means: Stop reinventing the wheel!
:class: attention
:class: dropdown
So Make use of proven open solutions! So use and improve great solid FOSS Python frameworks and libraries to keep things simple.
:::


:::{tip}
If you can do things simpler without an external FOSS library: Maybe you should do it.
:::

Humans love visualizations. The Python ecosystem has many visualization libraries. A reference to the well [maintained overview of the Python visualization landscape](https://pyviz.org/overviews/index.html) is available in the ToC of this publication. Improve this overview instead of creating your own!

:::{note}
This collection in this publication is a very opinionated selection. Core selecting criteria are:
* The product must have a valid FOSS license. So an OSI approved license.
* The library should be actively maintained  and meet a minimal quality level. Which is of course very opinionated and context dependent.
:::



```{include}  generatedfiles/guiframeworks.md
```


```{include}  generatedfiles/htmlparsing.md
```


```{include}  generatedfiles/tuiframeworks.md
```


```{include}  generatedfiles/testing.md
```