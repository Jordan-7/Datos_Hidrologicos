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

### Grafico que se muestra en las anteriores lineas de codigo
![Grafico que se muestra en las anteriores lineas de codigo](https://user-images.githubusercontent.com/82826199/119245365-13380a80-bb36-11eb-8dde-c7b91c8c8dc2.png)

### Promedio de los caudales diarios, al igresar la siguiente linea de codigo, en la consola se muestra una estadistica descriptiva.

summary(dat[,2:3])


### Para visualizar un histograma de los datos.

hist(estrella, col="green")

![H Estrella](https://user-images.githubusercontent.com/82826199/119245551-68285080-bb37-11eb-9f55-084315b50147.png)

hist(banano, col="blue")

![H Banano](https://user-images.githubusercontent.com/82826199/119245559-74141280-bb37-11eb-876e-28284c3e6021.png)


### Se nombra las columnas de los datos para así hacer uso de una en especifico cuando sea necesario

names(dat) <- c("fecha", "estrella", "banano")

attach(dat)

### Se utiliza para mostrar una grafica

plot(estrella, col="blue")

![Grafica estrella](https://user-images.githubusercontent.com/82826199/119245707-7aef5500-bb38-11eb-8258-097df07bbb74.png)

plot(banano, col="blue")

![Grafica Banano](https://user-images.githubusercontent.com/82826199/119245762-d6214780-bb38-11eb-9c42-639bee6bce05.png)


### Se crea una variable de la serie del tiempo.

Datatime <- strptime(dat[,1], format= "%d/%m/%Y")

### Se crean más variables para el periodo anual

MAQ_Estrella <- tapply(estrella, format(Datatime, format="%Y"), FUN=sum)

MAQ_Banano <- tapply(banano, format(Datatime, format="%Y"), FUN=sum)

### El siguiente comando se usa para crear un documento en el directorio donde se tiene el documento de R salvado/guardado.

write.csv(rbind(MAQ_Estrella,MAQ_Banano), file= "MAQ.csv")

### Con esta linea de comando se puede crear una grafica que representa los valores anuales del caudal de los datos.

plot(MAQ_Banano, ylim=c(100,3000))

lines(MAQ_Estrella, col=6)

![MAQ Banano](https://user-images.githubusercontent.com/82826199/119245879-dc63f380-bb39-11eb-9e7b-a0227d372619.png)

plot(MAQ_Estrella, ylim=c(100,3000))

lines(MAQ_Banano, col=4)

![MAQ Estrella](https://user-images.githubusercontent.com/82826199/119245929-5f854980-bb3a-11eb-8730-a75fbf23e8d9.png)

Como se pudo apreciar anterior mente la linea y los puntos representan la diferencia con respecto a los otros valores.

### Con esta linea de comando se puede crear una grafica que representa los valores mensuales del caudal de los datos.

MMQ_Estrella <- tapply(estrella, format(Datatime, format="%m"), FUN=sum)

MMQ_Banano <- tapply(banano, format(Datatime, format="%m"), FUN=sum)





