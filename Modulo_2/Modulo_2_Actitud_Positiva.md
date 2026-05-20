---
title: "Modulo 2"
author: "Actitud Positiva :)"
date: "2026-04-08"
output:
  pdf_document: default
  html_document: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

# Introducción

Este documento contiene información sobre R Markdown. Algunos conceptos útiles, ejercicios aplicados, comparativas con otros lenguajes como Python, y demás cosas.

## Markdown y R Markdown

Markdown es una sintaxis de texto simple para crear documentos estructurados utilizando texto plano. Util para la creación de documentos en formatos como HTML, PDF y Word, sin interfaces gráficas. Es uina herramienta sencilla, rápida y de amplia utilidad.

R Markdown es una extension del md que permite mezclar texto con código R y obtener resultados.

### Resumen de diferencias básicas

| Markdown | R Markdown |
|----------|-----------|
| Solo texto formateado | Texto + código R |
| No ejecuta nada | Ejecuta código |
| Estático | Dinámico |

### ¿Para qué sirve R Markdown?

En ingeniería es extremadamente útil para:

- Informes técnicos
- Análisis de datos
- Trabajos prácticos
- Automatización de resultados

R Markdown permite a otro correr tu archivo y obtener exactamente los mismos resultados  

## Uso de data sets o base de datos internos de R

Usando el comando `data()` en la consola obtenemos distintos datos ya cargados en la base de datos de R, estos datos estan cargados en tablas de las cuales podemos elegir columnas especificas si escribimos el signo `$` despues del comando de informacion especifico que queremos.

## Primeros comandos de R

R es un lenguaje muy parecido a Matlab que trabaja con matrices.

```{r}

A <- 10
B <- 789
C = B - A
D = C * A
C
D
```

### Comando Plot

Es un comando que sirve para graficar cualquier fuente de datos que le asignemos: Tenemos la posibilidad de asignar nombres a las variables o hacer cambios del grafico, en caso de no saber el comando podemos escribir `?plot` en la consola, a la derecha nos va a abrir una pestaña y ahí tocar Generic X-Y Plotting y ahi nos va a explicar cada comando.

Comp ejemplo de aplicación tenemos:

```{r}
plot(pressure,main="presion del gas ideal",xlab="Temperatura (°K)",ylab="hPa",type="l")
```

### Funciones estadisticas

```{r}
z1<-rnorm(350,22,5)
w1<-length(z1)
x1<-501:850
plot(x1,z1)
```

```{r}
hist(z1,main="Histograma",breaks=60)

```

```{r}
density(z1)

plot(density(z1),main="Densidad",type="l")
```
# Desarrollo

## Ejercicio 1:

### Crear un vector que tenga todos los numeros enteros desde 1 a 762
```{r}
secuencia_DNI<-(1:762)
secuencia_DNI
```
## Ejercicio 2: 

### Calcular la suma de todos los valores del vector secuencia_DNI
```{r}
total<-0
valor_final<-length(secuencia_DNI)
for (i in 1:valor_final){
  total<-total+i
}
total
```
## Ejercicio 3

### Repetir el ejercicio anterior pero en Python

```{python}
  
secuencia_DNI = list(range(1, 763))

suma_total = sum(secuencia_DNI)

print(suma_total)
```
## Ejercicio 3.1:

### ¿Cuanto tarda en correr el código del ejercicio 2?
```{r}
inicio<-Sys.time()
total<-0
valor_final<-10*length(secuencia_DNI)
for (i in 1:valor_final){
  total<-total+i
}
final<-Sys.time()
final-inicio
```
## Ejercicio 3.2:

### Repetir el ejercicio anterior usando la cabeza de Gauss.

```{r}
inicio <- Sys.time()
n <- 10 * length(secuencia_DNI)
total <- n * (n + 1) / 2
total
final <- Sys.time()
final - inicio
```
## Ejercicio 4:

### Generar una secuancia de 2 en 2 hasta 100000.

```{r}
system.time({
A<-numeric(50000)
for (i in 1:50000){
  A[i]<-i * 2
}
})
  head(A)
  tail(A)
```
### Secuencia con funcion integrada de R:

```{r}
system.time({
B<-seq(2,100000, by=2)
})
head(B)
tail(B)
```
## Ejercicio 5:

### Implementación de una serie de Fibonacci.

### Mediante función integrada:

### ¿Cuantas iteraciones se necesitan para generar un número de la serie mayor que 1.000.000?

```{r}
fib<- c(0,1)

while(tail(fib,1)<1e6) {
 fib <- c(fib, fib[length(fib)]+fib[length(fib)-1])
}
fib

print(paste("se requieren:",length(fib),"iteraciones"))

```
## Ejercicio 6:

### Implementación de una serie de Fibonacci.

### Mediante definición matemática (método iterativo):

### ¿Cuantas iteraciones se necesitan para generar un número de la serie mayor que 1.000.000?

```{r}

system.time({
f0 <- 0
f1 <- 1

contador <- 0

while (f1 <= 1000000) {
  
  f2 <- f1 + f0
  div <- f2/f1
  
  f0 <- f1
  f1 <- f2
  contador <- contador + 1
}
print(paste('Iteraciones necesarias:', contador))
print(paste('Valor alcanzado:', f1))
print(paste('Cociente:', div))

})

```
## Ejercicio 7:

### Ordenacion de un vector por método burbuja. Burbuja vs Sort

```{r}
library(microbenchmark)

x <- sample(1:20000, 20000)

burbuja <- function(x) {
  n <- length(x)
  
  for (j in 1:(n - 1)){
    for (i in 1:(n - j)){
      if (x[i] > x[i + 1]){
        temp <- x[i]
        x[i] <- x[i + 1]
        x[i + 1] <- temp
      }
    }
  }
  return(x)
}

resultado <- microbenchmark(
  burbuja = burbuja(x),
  sort_R = sort(x),
  times = 3
)

summary(resultado)
```
### Conclusión

Al comparar ambos métodos con microbenchmark, se observa que el método sort() posee una performance muy superior al método burbuja. Esto se debe a que el algoritmo burbuja compara pares de elementos repetitivamente, mientras que sort() utiliza algoritmos internos más eficientes. Para una muestra de tamaño 20.000, la diferencia de tiempo de ejecución es muy significativa, mostrando que el método burbuja resulta poco adecuado para vectores grandes.

## Ejercicio 8 - 1er Forma con Microbenchmark:

### Desarrolla dos algoritmos que hagan este trabajo, por ejemplo para sumar desde 1 hasta \( 1 \times 10^{10} \) y verifica cuál de los dos es más eficiente.

```{r}

suma_iterativa <- function(n) {
  total <- 0
  for (i in 1:n) {
    total <- total + i
  }
  return(total)
}

suma_gauss <- function(n) {
  return(n * (n + 1) / 2)
}

library(microbenchmark)

n <- 1e6

resultado <- microbenchmark(
  iterativo = suma_iterativa(n),
  gauss = suma_gauss(n),
  times = 5
)

resultado
summary(resultado)

suma_iterativa(n)
suma_gauss(n)

```
## Ejercicio 8 - 2da Forma

### Desarrolla dos algoritmos que hagan este trabajo, por ejemplo para sumar desde 1 hasta \( 1 \times 10^{10} \) y verifica cuál de los dos es más eficiente.

```{r}
n <- 1e6

system.time({
  suma <- 0
  for (i in 1:n) {
    suma <- suma + i
  }
})
suma

system.time({
suma2<-n * (n+1)/2
})
suma2
```
### Conclusión

El método iterativo presenta mayor demora, por lo tanto menor eficiencia, debido a que realiza una suma por cada elemento. En cambio, el método de Gauss tiene menor demora, por tanto mayor eficiencia, ya que utiliza una fórmula directa que disminuye las iteraciones, recursos y por tanto los tiempos.

Esto hace que el método de Gauss sea significativamente más eficiente, especialmente para valores grandes de \( n \). Para \( n = 1 \times 10^{10} \), el método iterativo resulta impracticable, mientras que el método de Gauss obtiene el resultado de forma instantánea.

Sin embargo, por cuestiones de recursos disponibles para ejecutar y depurar los códigos se tomó como criterio \( n = 1 \times 10^{6} \), debido a que un exponente 10 en el metodo iterativo colapsaba el entorno e imposibilitaba la ejecución
