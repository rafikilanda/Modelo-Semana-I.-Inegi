# Modelo-Semana-I.-Inegi
Dentro de este repositorio se encuentra el código usado generar los insights de el reto de la semana i usado con R

A <-Distribucion

head(A)
#Media
#Varianza 
#Desviacion estandar 
#Histograma 
#Curtosis 

mean(A$`Volumen de agua suministrada`)
estVar()

summary(A$`Volumen de agua suministrada`)
summary(A$Industrial)
summary(A$`Volumen (Miles de m3) mantos superficiales`)
summary(A$`Volumen (Miles de m3) mantos subsuelo`)

hist(A$Entidad)
library(ggplot2)
ggplot(A, aes(A$`Volumen de agua suministrada`, A$Entidad),
       main = "Distribucion del agua por entidad", xlab("Volumen de agua"), ylab("Entidad")) + geom_point(colour = "red")

ggplot(A, aes(A$Industrial, A$Entidad),
       main = "Distribucion del agua por entidad", xlab("Volumen de agua"), ylab("Entidad")) + geom_point(colour = "red")

Mod1 <- lm(A$`Volumen de agua suministrada`~ A$Domestica, A$Industrial, Poblacion_01$Total)

mod2<-lm(A$`Volumen de agua suministrada`~ A$Domestica + A$Industrial + A$`Poblacion total`)
summary(mod2)

mod3 <-lm(A$Domestica ~A$`Volumen de agua suministrada` + A$Industrial  + A$`Poblacion total`)
summary(mod3)
