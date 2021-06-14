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

### Parte 2

