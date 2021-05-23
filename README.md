# Datos_Hidrologicos

## Se mostrara la fuente ó codigo de R realizado en la clase del día 17 de mayo.

### En primera instancia se ddfinio una variable para el documento hidrologico de formato .csv y se comprobo si tenia espacios vacios.

dat <- read.csv("FDC.csv", na.strings="")

head(dat)
dim(dat)

dat[!complete.cases(dat),]

### Seguidamente se mostrará una grafica; rojo rio estrella, amarillo rio banano. La grafica representa los datos hidrologicos. 

plot(dat[,2], type = "l", col="red")

lines(dat[,3], col="yellow")

## Grafico que se muestra en las anteriores lineas de codigo
![Grafico que se muestra en las anteriores lineas de codigo](https://user-images.githubusercontent.com/82826199/119245365-13380a80-bb36-11eb-8dde-c7b91c8c8dc2.png)

### Promedio de los caudales diarios, al igresar esta linea de codigo en la consola se muestra una estadistica descriptiva.

summary(dat[,2:3])

###
