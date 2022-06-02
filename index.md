# Understand
## Understanding Impact of ESG Risk Exposures on Short-term Stock Returns



```
library(data.table)
library(dplyr)
library(readxl)

DATE <- function(yyyymmdd) {
  s <- as.character(yyyymmdd)
  dte <- as.Date(sprintf("%s-%s-%s",substr(s,1,4),substr(s,5,6),substr(s,7,8)))
  return(dte)
}

DATE2 <- function(x) {
  s <- as.character(x)
  dte <- as.Date(sprintf("20%s-%s-%s",substr(s,7,8),substr(s,4,5),substr(s,1,2)))
  return(dte)
}
```
