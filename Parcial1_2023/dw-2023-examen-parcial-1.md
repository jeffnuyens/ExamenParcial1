dw-2023-parcial-1
================
Tepi
9/11/2023

# Examen parcial

Indicaciones generales:

- Usted tiene el período de la clase para resolver el examen parcial.

- La entrega del parcial, al igual que las tareas, es por medio de su
  cuenta de github, pegando el link en el portal de MiU.

- Pueden hacer uso del material del curso e internet (stackoverflow,
  etc.). Sin embargo, si encontramos algún indicio de copia, se anulará
  el exámen para los estudiantes involucrados. Por lo tanto, aconsejamos
  no compartir las agregaciones que generen.

## Sección 0: Preguntas de temas vistos en clase (20pts)

- Responda las siguientes preguntas de temas que fueron tocados en
  clase.

1.  ¿Qué es una ufunc y por qué debemos de utilizarlas cuando
    programamos trabajando datos? Respuesta: Una ufunc es una función
    universal que opera individualmente con cada elemento del array.
    Debemos utilizarlas porque facilitan operaciones complejas en arrays
    de datos, permitiendo un código más eficiente y mejor en
    legibilidad.

2.  Es una técnica en programación numérica que amplía los objetos que
    son de menor dimensión para que sean compatibles con los de mayor
    dimensión. Describa cuál es la técnica y de un breve ejemplo en R.
    Respuesta: La técnica es broadcasting. Permite que los operadores y
    funciones se apliquen de una manera vectorizada sobre arrays de
    diferentes tamaños y formas.

``` r
x <- 1:5
y <- 1:5

# Crear una tabla de multiplicar usando la función outer y el operador de multiplicación
broadcasting <- outer(x, y, FUN = "*")

print(broadcasting)
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    1    2    3    4    5
    ## [2,]    2    4    6    8   10
    ## [3,]    3    6    9   12   15
    ## [4,]    4    8   12   16   20
    ## [5,]    5   10   15   20   25

3.  ¿Qué es el axioma de elegibilidad y por qué es útil al momento de
    hacer análisis de datos? Respuesta: Es un axioma que postula que
    para cada familia de conjuntos no vacíos, existe otro conjunto que
    contiene un elemento de cada una de esas familias. Esta axioma es
    útil en análisis de datos porque facilita el manejo de muchas
    muestras y problemas de optimización en contextos más generales y
    abstractos. También, permite definir funciones y estructuras (como
    bases en espacios vectoriales) que serían imposibles de definir sin
    este axioma, ayudando así en el desarrollo de métodos avanzados de
    análisis.

4.  Cuál es la relación entre la granularidad y la agregación de datos?
    Mencione un breve ejemplo. Luego, explique cuál es la granularidad o
    agregación requerida para poder generar un reporte como el
    siguiente: Respuesta: La granularidad es el nivel de detalle en un
    conjunto de datos. La agregación es el proceso de combinar varios
    datos en uno solo para reducir esa granularidad. Por ejemplo, al
    sumar las ventas diarias para obtener un total mensual, estamos
    aumentando el nivel de agregación porque estamos combinando el total
    de ventas diarias, y reduciendo la granularidad de los datos porque
    estamos reduciendo qué tan detallado es nuestro conjunto de datos y
    reduciéndolo solo a un total mensual.

| Pais | Usuarios |
|------|----------|
| US   | 1,934    |
| UK   | 2,133    |
| DE   | 1,234    |
| FR   | 4,332    |
| ROW  | 943      |

Respuesta: Para poder generar un reporte con esta granularidad se
necesitan datos a nivel de usuario que incluyan información sobre el
país de cada usuario. También, se necesita agregar estos datos a nivel
de país para obtener el número total de usuarios por país, por lo que la
agregación requerida aquí sería una sumatoria del número de usuarios por
cada país.

## Sección I: Preguntas teóricas. (50pts)

- Existen 10 preguntas directas en este Rmarkdown, de las cuales usted
  deberá responder 5. Las 5 a responder estarán determinadas por un
  muestreo aleatorio basado en su número de carné.

- Ingrese su número de carné en `set.seed()` y corra el chunk de R para
  determinar cuáles preguntas debe responder.

``` r
#set.seed("20210420") 
v<- 1:10
preguntas <-sort(sample(v, size = 5, replace = FALSE ))

paste0("Mis preguntas a resolver son: ",paste0(preguntas,collapse = ", "))
```

    ## [1] "Mis preguntas a resolver son: 1, 2, 3, 6, 8"

### Listado de preguntas teóricas

1.  Para las siguientes sentencias de `base R`, liste su contraparte de
    `dplyr`:

    - `str()`
    - `df[,c("a","b")]`
    - `names(df)[4] <- "new_name"` donde la posición 4 corresponde a la
      variable `old_name`
    - `df[df$variable == "valor",]`

2.  Al momento de filtrar en SQL, ¿cuál keyword cumple las mismas
    funciones que el keyword `OR` para filtrar uno o más elementos una
    misma columna? Respuesta: IN

3.  ¿Por qué en R utilizamos funciones de la familia apply
    (lapply,vapply) en lugar de utilizar ciclos?

4.  ¿Cuál es la diferencia entre utilizar `==` y `=` en R?

5.  ¿Cuál es la forma correcta de cargar un archivo de texto donde el
    delimitador es `:`? Respuesta: data \<- read.table(“archivo”,
    sep=“:”, header=TRUE)

6.  ¿Qué es un vector y en qué se diferencia en una lista en R?
    Respuesta: Un vector es un conjunto de elementos del mismo tipo. En
    cambio, una lista puede contener elementos de diferentes tipos,
    incluyendo otros vectores o listas.

7.  ¿Qué pasa si quiero agregar una nueva categoría a un factor que no
    se encuentra en los niveles existentes?

8.  Si en un dataframe, a una variable de tipo `factor` le agrego un
    nuevo elemento que *no se encuentra en los niveles existentes*,
    ¿cuál sería el resultado esperado y por qué?

    - El nuevo elemento
    - `NA` Respuesta: NA. Una variable de tipo factor tiene un conjunto
      fijo de niveles para representar categorías y cualquier valor que
      no coincida con estos niveles predefinidos se trata como un dato
      faltante.

9.  En SQL, ¿para qué utilizamos el keyword `HAVING`? Respuesta: Si
    queremos filtrar por agregacion, utilizamos HAVING.

10. Si quiero obtener como resultado las filas de la tabla A que no se
    encuentran en la tabla B, ¿cómo debería de completar la siguiente
    sentencia de SQL?

    - SELECT \* FROM A \_\_\_\_\_\_\_ B ON A.KEY = B.KEY WHERE
      \_\_\_\_\_\_\_\_\_\_ = \_\_\_\_\_\_\_\_\_\_

Extra: ¿Cuántos posibles exámenes de 5 preguntas se pueden realizar
utilizando como banco las diez acá presentadas? (responder con código de
R.)

``` r
# Número de posibles exámenes
posibles_examenes <- choose(10, 5)

print(posibles_examenes)
```

    ## [1] 252

## Sección II Preguntas prácticas. (30pts)

- Conteste las siguientes preguntas utilizando sus conocimientos de R.
  Adjunte el código que utilizó para llegar a sus conclusiones en un
  chunk del markdown.

A. De los clientes que están en más de un país,¿cuál cree que es el más
rentable y por qué?

B. Estrategia de negocio ha decidido que ya no operará en aquellos
territorios cuyas pérdidas sean “considerables”. Bajo su criterio,
¿cuáles son estos territorios y por qué ya no debemos operar ahí?

### II. Preguntas prácticas

## A

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
data_parcial <- readRDS("parcial_anonimo.rds")

# Clientes que están en más de un país
clientes_multinacionales <- data_parcial %>%
  group_by(Cliente, Pais) %>%
  summarise() %>%
  group_by(Cliente) %>%
  filter(n() > 1) %>%
  select(Cliente)
```

    ## `summarise()` has grouped output by 'Cliente'. You can override using the
    ## `.groups` argument.

``` r
# Ventas totales por cliente
ventas_por_cliente <- data_parcial %>%
  filter(Cliente %in% clientes_multinacionales$Cliente) %>%
  group_by(Cliente) %>%
  summarise(Venta_Total = sum(Venta, na.rm = TRUE))

# Cliente más rentable
cliente_mas_rentable <- ventas_por_cliente %>%
  arrange(desc(Venta_Total)) %>%
  top_n(1)
```

    ## Selecting by Venta_Total

``` r
print(cliente_mas_rentable)
```

    ## # A tibble: 1 × 2
    ##   Cliente  Venta_Total
    ##   <chr>          <dbl>
    ## 1 a17a7558      19818.

Respuesta: El cliente a17a7558 es el más rentable porque representa la
mayor cantidad de ventas, 19817.7

## B

``` r
#Ventas negativcas
ventas_negativas <- data_parcial %>%
  filter(Venta < 0) %>%
  group_by(Territorio) %>%
  summarise(perdidas_totales = sum(Venta, na.rm = TRUE), 
            ventas_negativas = n()) %>%
  filter(ventas_negativas > 10)

print(ventas_negativas)
```

    ## # A tibble: 41 × 3
    ##    Territorio perdidas_totales ventas_negativas
    ##    <chr>                 <dbl>            <int>
    ##  1 0bbe6418              -218.               11
    ##  2 0c169a3b             -1171.               59
    ##  3 0dd30fcd              -479                20
    ##  4 0ef0ce97              -348.               16
    ##  5 1c81fb6c              -481.               25
    ##  6 1d407777             -3300.              129
    ##  7 23e9d55d              -765.               43
    ##  8 2e812869             -3056.              149
    ##  9 3cae948b              -626.               24
    ## 10 45c0376d              -475.               19
    ## # ℹ 31 more rows

Respuesta: Suponemos que la empresa no tolerará aquellos territorios con
ventas negativas mayores a 10 ventas.
