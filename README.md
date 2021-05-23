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

### Se utiliza para mostrar una grafica; los valores de las columnas Estrellas y Banano

plot(estrella, col="blue")

![Grafica estrella](https://user-images.githubusercontent.com/82826199/119245707-7aef5500-bb38-11eb-8258-097df07bbb74.png)

plot(banano, col="blue")

![Grafica Banano](https://user-images.githubusercontent.com/82826199/119245762-d6214780-bb38-11eb-9c42-639bee6bce05.png)


### Se crea una variable de la serie del tiempo.

Datatime <- strptime(dat[,1], format= "%d/%m/%Y")

### Se crean más variables para el periodo anual

MAQ_Estrella <- tapply(estrella, format(Datatime, format="%Y"), FUN=sum)

MAQ_Banano <- tapply(banano, format(Datatime, format="%Y"), FUN=sum)

### El siguiente comando se usa para crear un documento de formato .csv en el directorio donde se tiene el documento de R salvado/guardado.

write.csv(rbind(MAQ_Estrella,MAQ_Banano), file= "MAQ.csv")

### Con esta linea de comando se puede crear una grafica que representa los valores anuales del caudal de los datos.

plot(MAQ_Banano, ylim=c(100,3000))

lines(MAQ_Estrella, col=6)

![MAQ Banano](https://user-images.githubusercontent.com/82826199/119245879-dc63f380-bb39-11eb-9e7b-a0227d372619.png)

plot(MAQ_Estrella, ylim=c(100,3000))

lines(MAQ_Banano, col=4)

![MAQ Estrella](https://user-images.githubusercontent.com/82826199/119245929-5f854980-bb3a-11eb-8730-a75fbf23e8d9.png)

Como se pudo apreciar anterior mente la linea representa los valores de los caudales del año una sustancia y los puntos representan la diferencia con respecto a los otros valores. Linea 1 Estrella y Linea 2 Banano.

### Con esta linea de comando se puede crear una grafica que representa los valores mensuales del caudal de los datos.

MMQ_Estrella <- tapply(estrella, format(Datatime, format="%m"), FUN=sum)

MMQ_Banano <- tapply(banano, format(Datatime, format="%m"), FUN=sum)

### La siguiente linea se utiliza el analisis de la correlación de los datos aplicados y se representaran 3 graficos para la finalización de este trabajo, que representan la correlacion de los datos.

cordata <- cor(dat[,2:3], method= "spearman")

dat.lm <- lm(dat[,2] ~ dat[,3], data=dat)

summary(dat.lm)

plot(dat.lm)

![RvsL](https://user-images.githubusercontent.com/82826199/119246105-fe5e7580-bb3b-11eb-8a8f-2e54e271e0c9.png)

![RvsF](https://user-images.githubusercontent.com/82826199/119246111-133b0900-bb3c-11eb-8dec-75eca3ba38b0.png)

![NormalQ-Q](https://user-images.githubusercontent.com/82826199/119246119-2221bb80-bb3c-11eb-9e6d-cfa1d0a6c892.png)

![Scale location](https://user-images.githubusercontent.com/82826199/119246132-3d8cc680-bb3c-11eb-870a-68e8629e22d4.png)

![RevsLev](https://user-images.githubusercontent.com/82826199/119246140-51382d00-bb3c-11eb-88e2-796de54d7e25.png)


Con Este ultimo grafico se daria por terminado la secion del día 17 de mayo, sobre la **Exploración de Datos Hidrológicos**



