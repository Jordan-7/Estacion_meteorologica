# Estacion_meteorologica

## Se mostrara el codigo para el proyecto 1


## Parte 1

### Se cargan las librerias.

library(ggplot2)

library(dplyr)

library(hrbrthemes)

library(grindExtra)

library(grind)

library(tidyr)

### Se declaron los valores para el documento y cada columna de la tala

Datos_clima <- read.csv ("liberia_datos_climaticos.csv", sep = ",", dec = ",", na.strings = "")

Datos_clima <- na.omit (Datos_clima)

Datos_clima <-Datos_clima %>% rename(lluvia = "Lluvia..mm.")

Datos_clima <-Datos_clima %>% rename(humedad = "HumedadRelativa....")

Datos_clima <-Datos_clima %>% rename(viento = "VelocidadViento..m.s.")

Datos_clima <-Datos_clima %>% rename(radiación = "Irradiacion..W.m2.")

Datos_clima <-Datos_clima %>% rename(temp = "Temperatura..Celsius.")

Datos_clima <-Datos_clima %>% rename(evapo = "EvapoTranspiracion..mm.")

### Formato para la fecha.

Datos_clima <-Datos_clima %>% mutate(fecha = as.Date(datc, format = "%d/%m/%Y"))

### Realizar histogramas.

n1 <- ggplot(Datos_clima, aes(x = lluvia , group = 1))+geom_histogram (col = "blue")

n2 <- ggplot(Datos_clima, aes(x = humedad , group = 2))+geom_histogram (col = "green")

n3 <- ggplot(Datos_clima, aes(x = viento , group = 3))+geom_histogram (col = "pink")

n4 <- ggplot(Datos_clima, aes(x = radiación , group = 4))+geom_histogram (col = "yellow")

n5 <- ggplot(Datos_clima, aes(x = temp , group = 5))+geom_histogram (col = "red")

n6 <- ggplot(Datos_clima, aes(x = evapo , group = 6))+geom_histogram (col = "gray")


## Parte 2

dat.dat <-Datos_clima %>% select (lluvia, humedad, viento, radiación, temp, evapo)%>% 

mutate(fecha = as.Date(fecha, format = "%d/%m/%Y"))%>%

summarise(lluvia = sum(lluvia), evapo = sum(evaporacion), temp= mean(t_celcius), viento = mean(vel_viento), radiacion = mean(irradiacion), humedad = mean(humedad))

### Para crear con geometria de linea

m1<- ggplot(Datos_clima, aes(x = fecha, y=lluvia ,group = 1))+geom_line (col = "blue")

m2<- ggplot(Datos_clima, aes(x = fecha, y=evapo ,group = 2))+geom_line (col = "gray")

m3<- ggplot(Datos_clima, aes(x = fecha, y=temp ,group = 1))+geom_line (col = "red")

m4<- ggplot(Datos_clima, aes(x = fecha, y=viento ,group = 1))+geom_line (col = "pink")

m5<- ggplot(Datos_clima, aes(x = fecha, y=radiacion ,group = 1))+geom_line (col = "yellow")

m6<- ggplot(Datos_clima, aes(x = fecha, y=humedad ,group = 1))+geom_line (col = "green")

grid.arrange("m1", "m2", "m3", "m4", "m5", "m6")


## Parte 3

### Para hacerlo con puntos geometricos

A1 <- ggplot(Datos_clima, aes(x = fecha, y=lluvia , group = 1))+geom_point (col = "blue")

A2 <- ggplot(Datos_clima, aes(x = fecha, y=evapo , group = 2))+geom_point (col = "gray")

A3 <- ggplot(Datos_clima, aes(x = fecha, y=temp , group = 3))+geom_point (col = "red")

A4 <- ggplot(Datos_clima, aes(x = fecha, y=viento , group = 4))+geom_point (col = "pink")

A5 <- ggplot(Datos_clima, aes(x = fecha, y=radiacion , group = 5))+geom_point (col = "yellow")

A6 <- ggplot(Datos_clima, aes(x = fecha, y=humedad , group = 6))+geom_point (col = "green")

grid.arrange("A1", "A2", "A3", "A4", "A5", "A6"
