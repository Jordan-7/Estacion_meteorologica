# Estacion_meteorologica

## Se mostrara el codigo para el proyecto 1

### Se cargan las librerias.

library(ggplot2)

library(dplyr)

library(hrbrthemes)

library(grindExtra)

library(grind)

library(tidyr)

###

Datos_clima <- read.csv ("liberia_datos_climaticos.csv", sep = ",", dec = ",", na.strings = "")

Datos_clima <- na.omit (Datos_clima)

Datos_clima <-Datos_clima %>% rename(lluvia = "Lluvia..mm.")

Datos_clima <-Datos_clima %>% rename(humedad = "HumedadRelativa....")

Datos_clima <-Datos_clima %>% rename(viento = "VelocidadViento..m.s.")

Datos_clima <-Datos_clima %>% rename(radiación = "Irradiacion..W.m2.")

Datos_clima <-Datos_clima %>% rename(temp = "Temperatura..Celsius.")

Datos_clima <-Datos_clima %>% rename(evapo = "EvapoTranspiracion..mm.")
