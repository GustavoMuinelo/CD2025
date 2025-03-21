Cargamos paquetes

{r, message=FALSE, warning=FALSE, echo=FALSE}
library(tidyverse)

Importar el dataset

{r, message=FALSE, warning=FALSE}
barrios <- read_csv("C:/Users/Usuario/Desktop/Ciencia Datos R/dataset barrios.csv")

miramos los datos

{r}
head(barrios)

transformar a factor

{r}
barrios$cluster <- as_factor(barrios$cluster)

otra forma

{r}
barrios = mutate(barrios, cluster=as_factor(cluster))

otra forma es utilizando los pipes

{r}
barrios = barrios |> mutate(cluster=as_factor(cluster))

grafico

{r}
ggplot(data=barrios, aes(x=INGRESO, y=EDUCACION)) + geom_point()

cluster

{r}
g1=ggplot(data=barrios, aes(x=INGRESO,
                         y=EDUCACION,
                         color=cluster,
                         size=DESEMPLEO
                         ))+
                         geom_point(alpha=0.5) + theme_bw()

{r}
library(plotly)

{r}
ggplotly(g1)

facet_wrap

{r}
ggplot(data=barrios, aes(x=INGRESO,
                         y=EDUCACION,
                         color=cluster,
                         size=DESEMPLEO
                         ))+ geom_point(alpha=0.5) + theme_bw()+
                         facet_wrap(~cluster)

geom_smooth

{r, message=FALSE, warning=FALSE}
ggplot(data=barrios,
       aes(x=INGRESO,
           y=EDUCACION,
           color=cluster,
           size=DESEMPLEO))+ geom_point(alpha=0.5) +
           geom_smooth(se=FALSE) + theme_bw()

geom_smooth ()agregamos la tendencia lineal

{r, message=FALSE, warning=FALSE}
ggplot(data=barrios, aes(x=INGRESO,
                         y=EDUCACION,
                         size=DESEMPLEO))+ geom_point(alpha=0.5) +        geom_smooth(se=FALSE) + geom_smooth(method="lm", color="red", se=FALSE) + theme_bw()

distribucion del ingreso

{r, message=FALSE, warning=FALSE}
ggplot(data=barrios, aes(x=INGRESO)) + geom_histogram(bins=10)

distribucion del ingreso

{r, message=FALSE, warning=FALSE}
ggplot(data=barrios, aes(x=INGRESO), fill=cluster) +
  geom_density(bins=10)

Quarto enables you to weave together content and executable code into a finished document. To learn more about Quarto see https://quarto.org.

