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

