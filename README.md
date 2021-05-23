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

### Promedio de los caudales diarios, al igresar la siguiente linea de codigo, en la consola se muestra una estadistica descriptiva.

summary(dat[,2:3])

### Para visualizar un histograma de los datos.

hist(estrella, col="green")
![H Estrella](https://user-images.githubusercontent.com/82826199/119245551-68285080-bb37-11eb-9f55-084315b50147.png)

hist(banano, col="blue")
![H Banano](https://user-images.githubusercontent.com/82826199/119245559-74141280-bb37-11eb-876e-28284c3e6021.png)


