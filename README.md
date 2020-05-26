To cite bibliometrix in publications, please use: 
Aria, M. & Cuccurullo, C. (2017) bibliometrix: An R-tool for comprehensive science mapping analysis, Journal of Informetrics, 11(4), pp 959-975, Elsevier.


```{r}
library("bibliometrix")


```

```{r}
scopus_constructivism <- "scopus_constructivism.bib"
scopus_behaviorism <- "scopus_behaviorism.bib"
M_scopus_constructivism <- convert2df(file = scopus_constructivism, dbsource = "scopus", format = "bibtex")
M_scopus_behaviorism <- convert2df(file = scopus_behaviorism, dbsource = "scopus", format = "bibtex")


```

The first step is to perform a descriptive analysis of the bibliographic data frame.

The function biblioAnalysis calculates main bibliometric measures using this syntax:

```{r}
results_scopus_constructivism <- biblioAnalysis(M_scopus_constructivism, sep = ";")
results_scopus_behaviorism <- biblioAnalysis(M_scopus_behaviorism, sep = ";")
options(width=500)
results_scopus_constructivism["Key"] = "constructivism"
results_scopus_behaviorism["Key"] = "behaviorism"
results_scopus <- rbind(results_scopus_constructivism, results_scopus_behaviorism)



summary_scopus_constructivism<- summary(object = results_scopus_constructivism, k = 10, pause = FALSE)
S
#plot(x = results_scopus_constructivism, k = 15, pause = FALSE)
#plot(x = results_scopus_behaviorism, k = 15, pause = FALSE)

names(results_scopus_constructivism)
plot(table(results_scopus_constructivism$Years),type="l")
lines(table(results_scopus_behaviorism$Years),col="green")

#legend(x="topright",c("Theoretical (B=2)","Observed"),col=c("red","blue"),lty = c(1,1,1),cex=0.6,bty="n")
```

