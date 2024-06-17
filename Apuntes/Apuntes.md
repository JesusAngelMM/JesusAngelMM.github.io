<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.css" integrity="sha384-AfghSM7D5reI2w5afveGRfWZGpns6soXtrZ7H4VLjpCBzETKqlsCHeV1HGKJwHVG" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.js" integrity="sha384-gh2Eq3St/Q6MfhoaxUQV8e0qJLkp1B1QGOsND4T+blW2dhFzJ57yyjG3/GAUN8Hp" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/contrib/auto-render.min.js" integrity="sha384-mll67QQWKoQZ2vka3cS+XysF00R0sIdNo5ZLs5UXlgISaUHSKPneYJXJfMEEXBDr" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>


# Apuntes Métodos Numéricos

## 1.1 Importancia de los métodos numéricos
**Los métodos numéricos** constituyen técnicas mediante las cuales es posible formular problemas matemáticos, de tal forma que puedan resolverse utilizando operaciones ARITMETICAS.

- Suma
- Resta
- Multiplicación
- División

Invariablemente requieren un buen número de **tediosos cálculos** aritméticos.

No es raro que con el desarrollo de **computadoras digitales eficientes y rápidas**, el papel de los métodos numéricos en la solución de problemas en ingeniería haya aumentado de forma considerable en los últimos años.

Los métodos numéricos pueden ser aplicados para resolver procedimientos matemáticos en:

- Cálculo de derivadas
- Integrales
- Ajustes de curvas
- Polinomios
- Operaciones con matrices

Si los **métodos numéricos** son los algoritmos (conjuntos detallados y secuenciados de operaciones) que nos llevan hasta las soluciones estimadas de los problemas, el estudio de éstos y del **análisis de errores** que pueden llevar asociados constituye el **Análisis Numérico**.


### Conceptos básicos de cifras significativas...
Se necesita que los resultados sean exactos y precisos
- Exactitud: Es la cercanía de una medida al **valor real**
- Precisión: Es el grado de cercanía de los valores de **varias mediadas** en un punto.

![[Pasted image 20240206225046.png]]

Ambas son independientes la una de la otra. Así los resultados en los valores de una medición pueden ser precisos y no exactos y viceversa.

*Ejemplo dado*

$$70,69.5, 70.2, 69.75$$
1. Dado unos datos obtengo el promedio
2. Calculo de errores

La variación de una bascula es un ejemplo de error.
>Pág. 56

### Iteraciones
Un concepto importante son las *iteraciones*.
- Una serie de instrucciones que se repiten.
- Usan el número de repetición anterior.
- Para hasta cuando el resultado se repite continuamente.

## 1.2 Error y tipos de errores

Los errores numéricos surgen del uso de aproximaciones para representar operaciones y cantidades matemáticas exactas.
$$ Valor_{vedadero} = Valor_{Medido} + Error$$
$$ Valor_{vedadero} = Valor_{Aproximado} + Error$$

Por lo tanto...
$$Error = Valor_{vedadero} - Valor_{Aproximado}$$
Estas incluyen los *errores de truncamiento* que resultan del empleo de aproximaciones como un procedimiento matemático exacto.

Los *errores de redondeo* que se producen cuando se usan número que tiene un límite de cifras significativas para representar números exactos.

Aquí tienes las correcciones y adiciones a tus fórmulas respecto a métodos numéricos:

1. **Error Absoluto:** 
   $E_a = |Valor_{verdadero} - Valor_{aproximado}|$

2. **Error Relativo Fraccional Verdadero:**
   $E = \frac{\text{Error Verdadero}}{\text{Valor Verdadero}}$

3. **Error Porcentual:**
   $E_\% = \frac{\text{Error Verdadero}}{\text{Valor Verdadero}} \times 100$

4. **Error de Redondeo:** Se produce al redondear un número. Si el dígito a la derecha del último dígito redondeado es mayor que 5, se suma 1 al último dígito redondeado.

6. **Error de Truncamiento:** Se refiere al error que se comete al ignorar los dígitos que siguen en un número. Por ejemplo:
   $3.141591... \text{ (truncado)}$

Espero que estas correcciones sean útiles. Si tienes alguna pregunta adicional, no dudes en preguntar.

### Ejemplo:

Calcular el **error absoluto** y el *error relativo* porcentual que se genera cuando se realiza el cálculo el resultado que se obtiene es 1.4 y debería ser 1.8

- Valor medido o medido: $1.4$
- Valore real: $1.8$

$E_a = |Valor_{verdadero} - Valor_{aproximado}|$
$Ea=|1.8-1.4|$

Calcular el *error absoluto* y el *error relativo porcentual* que se genera cuando al realizar un cálculo el resultado que se obtiene es $1.4$ y debería ser $1.8$.

- Valor medido o medido: $1.4$
- Valore real: $1.8$

$\%Er = \frac{Valor_{verdadero} - Valor_{aproximado}}{Valor_{verdadero}}100$
$\%Er = \frac{1.8 - 1.4}{1.8}100$
$\%Er =22.22$

## Excel y Programas
Podemos usar Excel para calcular los errores de una serie de datos, basta con ingresar los datos en la zona correspondiente.

![[Pasted image 20240307132924.png]]

---
![[Excel Errores 1.xlsx]]

---
