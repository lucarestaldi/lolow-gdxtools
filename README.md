# gdxtools

The gdxtools package converts data (parameter or variables) from a GDX file (produced by the GAMS software) into a data.frame. It also provides a function to get information on a GDX file. This package is based on the R interface provided by GAMS software [gdxrrw](http://support.gams.com/doku.php?id=gdxrrw:interfacing_gams_and_r)

## Installation

```R
install.packages("gdxtools_0.3.zip",repos=NULL)
```

or

```R
library("devtools")
install_github('lolow/gdxtools')
```

## Usage

```R
library(gdxtools)

# define a gdx
mygdx <- gdx('results.gdx')

# get information on all items in the gdx
all_items(mygdx)

# create a data.frame from a parameter
travel_cost <- mygdx["travel_cost"]

# create a data.frame from the lower bound of a variable
lo_travel_time <- mygdx["travel_time", field="lo"]

# create a data.frame from the marginal value of an equation
m_time_constraint <- mygdx["time_constraint", field="m"]

# Extract a list of items from many GDX
myfiles = c("test1.gdx","test2.gdx")
allparam = batch_extract("myparam",files=myfiles)

# write gdx
param1 = data.frame(x=c('1','2'),value=1:10)
param2 = data.frame(a=c('london','paris','tahiti'),value=c(50,0.2,1e-2))
write.gdx("test.gdx",list(param1=param1,param2=param2))


```
