# 🐍 Ejercicios de Python — Guía Completa con Explicaciones

> Material didáctico: estructuras de control, bucles, funciones, matplotlib y un caso integrador de análisis de ventas con visualización de datos.

---

## 📚 Índice

1. [Condicionales (if / else)](#1-condicionales-if--else)
2. [Operadores lógicos (and)](#2-operadores-lógicos-and)
3. [Estructura match-case](#3-estructura-match-case)
4. [Manejo de excepciones (try/except)](#4-manejo-de-excepciones-tryexcept)
5. [Bucles for y while básicos](#5-bucles-for-y-while-básicos)
6. [Números pares e impares](#6-números-pares-e-impares)
7. [Tablas de multiplicar](#7-tablas-de-multiplicar)
8. [Números primos](#8-números-primos)
9. [Serie de Fibonacci](#9-serie-de-fibonacci)
10. [Factorial y permutaciones](#10-factorial-y-permutaciones)
11. [Funciones (def)](#11-funciones-def)
12. [Visualización de datos con matplotlib (gráficos individuales)](#12-visualización-de-datos-con-matplotlib-gráficos-individuales)
13. [Dashboards comparativos con subplots (dos gráficos lado a lado)](#13-dashboards-comparativos-con-subplots-dos-gráficos-lado-a-lado)
14. [Caso integrador: Sistema de análisis de ventas](#14-caso-integrador-sistema-de-análisis-de-ventas)

---

## 1. Condicionales (if / else)

### 1.1 Verificación de mayoría de edad (valor fijo)

**📌 Enunciado:** Dada una variable con un valor fijo de edad, determinar si la persona es mayor o menor de edad usando una estructura condicional simple.

**💡 Explicación / Definición:** El `if` es una estructura de control que evalúa una condición booleana (verdadera o falsa). Si la condición se cumple, se ejecuta el bloque indentado bajo `if`; si no, se ejecuta el bloque bajo `else`. Aquí se compara `edad >= 18` usando el operador relacional `>=` (mayor o igual que).

```python
# DEFINO MI VARIABLE Y VALOR

edad = 17

if edad >= 18:
    print("Eres mayor de edad")
else:
    print("Eres menor de edad")
```

**⚙️ Comentario de funcionamiento:** Python evalúa `17 >= 18`, lo cual es `False`, por lo que el flujo salta al bloque `else` e imprime `"Eres menor de edad"`.

---

### 1.2 Verificación de mayoría de edad (con input del usuario)

**📌 Enunciado:** Igual al ejercicio anterior, pero solicitando la edad al usuario por teclado en tiempo de ejecución.

**💡 Explicación / Definición:** `input()` siempre devuelve una cadena de texto (`str`), por lo que debe convertirse con `float()` para poder hacer comparaciones numéricas. Esta versión corrige un exceso de paréntesis que existía en un intento anterior.

```python
# DEFINO MI VARIABLE Y VALOR (Corregido el exceso de paréntesis)
edad = float(input("Ingresa tu Edad: "))

# pregunto con un if (estructura de control si)
if edad >= 18:
    print("Eres Mayor de Edad:", edad)
else:
    print("Eres Menor de Edad:", edad)
```

**⚙️ Comentario de funcionamiento:** El programa se detiene esperando que el usuario escriba un número, lo convierte a `float` (número decimal) y evalúa la misma condición que el ejercicio 1.1, mostrando además el valor ingresado junto al mensaje.

---

## 2. Operadores lógicos (and)

### 2.1 Login con credenciales fijas

**📌 Enunciado:** Validar un acceso comparando usuario y contraseña contra valores predefinidos en el código.

**💡 Explicación / Definición:** El operador lógico `and` requiere que **ambas** condiciones sean verdaderas para que el resultado total sea `True`. Se usa el operador de comparación `==` (igualdad), que no debe confundirse con `=` (asignación).

```python
# Variables que introduce el usuario
usuario = "admin"
contrasenia = "12345"

# Ambos lados del 'and' deben cumplirse
if usuario == "admin" and contrasenia == "12345":
    print("Acceso concedido. ¡Bienvenido!")
else:
    print("Usuario o contraseña incorrectos.")
```

**⚙️ Comentario de funcionamiento:** Como ambas variables ya tienen los valores correctos, las dos comparaciones son `True`, el `and` da `True` y se concede el acceso.

---

### 2.2 Login con credenciales ingresadas por el usuario

**📌 Enunciado:** Solicitar usuario y contraseña por teclado y validarlos contra credenciales correctas almacenadas en variables.

**💡 Explicación / Definición:** Se separan las credenciales "correctas" (constantes de referencia) de las credenciales "ingresadas" (capturadas con `input()`). No se usa `float()` aquí porque usuario y contraseña son texto, no números.

```python
# Variables que introducen las credenciales correctas (como texto)
usuario_correcto = "admin"
contrasenia_correcta = "12345"

# Solicitamos los datos al usuario (Quitamos float porque son cadenas de texto)
usuario = input("Ingrese el usuario: ")
contrasenia = input("Ingrese la contrasenia: ")

# Ambos lados del 'and' deben cumplirse
if usuario == usuario_correcto and contrasenia == contrasenia_correcta:
    print("Acceso concedido. ¡Bienvenido!")
else:
    print("Usuario o contraseña incorrectos.")
```

**⚙️ Comentario de funcionamiento:** El programa compara dinámicamente lo que el usuario escribe contra los valores de referencia; si alguna de las dos comparaciones falla, el `and` devuelve `False` y se rechaza el acceso.

---

## 3. Estructura match-case

### 3.1 Estación del año según el mes (fijo y con input)

**📌 Enunciado:** Determinar la estación del año a partir del número de mes, primero con un valor fijo en el código y luego solicitado al usuario.

**💡 Explicación / Definición:** `match-case` (disponible desde Python 3.10) es una alternativa a múltiples `if/elif` para comparar un valor contra varios patrones. El operador `|` dentro de un `case` permite agrupar varias opciones equivalentes. El patrón `case _:` funciona como un "caso por defecto" (comodín), similar al `else`.

```python
# ==========================================
# PARTE A: SIN INPUT (Valor fijo en el código)
# ==========================================
mes_fijo = 12  # Cambia este número manualmente para probar

print("--- Resultado Sin Input ---")
match mes_fijo:
    case 12 | 1 | 2:
        print(f"El mes {mes_fijo} corresponde a Invierno.")
    case 3 | 4 | 5:
        print(f"El mes {mes_fijo} corresponde a Primavera.")
    case 6 | 7 | 8:
        print(f"El mes {mes_fijo} corresponde a Verano.")
    case 9 | 10 | 11:
        print(f"El mes {mes_fijo} corresponde a Otoño.")
    case _:
        print("Número de mes inválido (debe ser del 1 al 12).")


# ==========================================
# PARTE B: CON INPUT (El usuario decide)
# ==========================================
print("\n--- Prueba Con Input ---")
mes_usuario = int(input("Ingresa el número de un mes (1-12): "))

match mes_usuario:
    case 1:
        print("Enero")
    case 2:
        print("Febrero")
    case 3:
        print("Marzo")
    # ... puedes agregar el resto de meses aquí ...
    case 12:
        print("Diciembre")
    case _:
        print("Ese mes no existe.")
```

**⚙️ Comentario de funcionamiento:** En la Parte A, Python recorre los `case` de arriba hacia abajo hasta encontrar una coincidencia; como `mes_fijo = 12` cae en `case 12 | 1 | 2`, imprime "Invierno". En la Parte B, el `match` compara el mes ingresado contra casos individuales (1, 2, 3... 12); si el número no está listado explícitamente, cae en `case _`.

---

### 3.2 Calculadora básica con match-case

**📌 Enunciado:** Solicitar dos números y un operador (`+`, `-`, `*`, `/`) al usuario y realizar la operación correspondiente, validando la división entre cero.

**💡 Explicación / Definición:** Cada `case` representa un patrón de texto (el símbolo del operador). Antes de dividir, se valida con un `if` que el divisor no sea cero, evitando así un error de ejecución (`ZeroDivisionError`).

```python
# Pedimos los números y la operación al usuario
num1 = float(input("Ingresa el primer número: "))
num2 = float(input("Ingresa el segundo número: "))
operacion = input("Ingresa la operación (+, -, *, /): ")

match operacion:
    case "+":
        resultado = num1 + num2
        print(f"Resultado de la suma: {resultado}")
    
    case "-":
        resultado = num1 - num2
        print(f"Resultado de la resta: {resultado}")
    
    case "*":
        resultado = num1 * num2
        print(f"Resultado de la multiplicación: {resultado}")
    
    case "/":
        # Validamos que no se divida entre cero para que no falle el programa
        if num2 != 0:
            resultado = num1 / num2
            print(f"Resultado de la división: {resultado}")
        else:
            print("Error: No se puede dividir entre cero.")
            
    case _:
        print("Operador no válido. Usa +, -, * o /.")
```

**⚙️ Comentario de funcionamiento:** El `match` selecciona el bloque según el símbolo escrito por el usuario; dentro del caso `"/"` hay una validación anidada adicional (`if num2 != 0`) porque `match-case` no puede evitar por sí solo el error de dividir entre cero, así que se combina con un `if` normal.

---

## 4. Manejo de excepciones (try/except)

### 4.1 Calculadora robusta con try/except

**📌 Enunciado:** Repetir la calculadora anterior, pero evitando que el programa se caiga si el usuario ingresa texto en lugar de números.

**💡 Explicación / Definición:** El bloque `try` contiene el código "propenso a errores". Si ocurre una excepción del tipo especificado (aquí `ValueError`, que se produce al intentar convertir texto no numérico con `float()`), el flujo salta automáticamente al bloque `except` en lugar de detener el programa con un error fatal.

```python
# Ponemos el código propenso a errores dentro de un bloque 'try'
try:
    num1 = float(input("Ingresa el primer número: "))
    num2 = float(input("Ingresa el segundo número: "))
    
    operacion = input("Ingresa la operación (+, -, *, /): ")

    match operacion:
        case "+":
            print(f"Resultado: {num1 + num2}")
        case "-":
            print(f"Resultado: {num1 - num2}")
        case "*":
            print(f"Resultado: {num1 * num2}")
        case "/":
            if num2 != 0:
                print(f"Resultado: {num1 / num2}")
            else:
                print("❌ Error: No se puede dividir entre cero.")
        case _:
            print("❌ Operador no válido. Usa +, -, * o /.")

# Si ocurre un ValueError (escribir texto en vez de números), se ejecuta esto:
except ValueError:
    print("❌ Error: ¡Debes ingresar números válidos, no letras o símbolos!")
```

**⚙️ Comentario de funcionamiento:** Si el usuario escribe, por ejemplo, `"abc"` cuando se le pide un número, `float("abc")` lanza un `ValueError`; en vez de que el programa se detenga con un mensaje de error técnico, el `except ValueError` lo intercepta y muestra un mensaje amigable.

---

## 5. Bucles for y while básicos

### 5.1 Números naturales del 1 al 100 (uno por línea)

**📌 Enunciado:** Imprimir los números del 1 al 100, cada uno en una línea distinta.

**💡 Explicación / Definición:** `range(1, 101)` genera una secuencia de números desde 1 hasta 100 (el límite superior de `range` **no se incluye**, por eso se usa 101). El `for` recorre esa secuencia asignando cada valor a la variable `i`.

```python
print("Los Numeros Naturales hasta el 100:")

for i in range(1, 101):
    print(i)
```

**⚙️ Comentario de funcionamiento:** Cada llamada a `print(i)` termina con un salto de línea por defecto, por lo que cada número aparece en su propia línea.

---

### 5.2 Números naturales del 1 al 100 (en una sola línea)

**📌 Enunciado:** Igual al anterior, pero mostrando todos los números separados por espacio en una sola línea.

**💡 Explicación / Definición:** El parámetro `end=" "` de `print()` reemplaza el salto de línea por defecto (`"\n"`) por un espacio, logrando que las impresiones queden en la misma línea.

```python
print("Los Numeros Naturales hasta el 100:")

for i in range(1, 101):
    print(i, end=" ")
```

**⚙️ Comentario de funcionamiento:** Al imprimir cada número seguido de un espacio en lugar de un salto de línea, el resultado final es una sola línea larga: `1 2 3 4 ... 100`.

---

### 5.3 Números naturales del 1 al 100 con while

**📌 Enunciado:** Lograr el mismo resultado del ejercicio 5.1 pero utilizando un bucle `while` en lugar de `for`.

**💡 Explicación / Definición:** El `while` repite un bloque mientras una condición sea verdadera. A diferencia del `for` con `range`, aquí es necesario declarar manualmente un contador (`contador = 1`) e incrementarlo dentro del bucle (`contador += 1`), o se produciría un bucle infinito.

```python
contador = 1
while contador <= 100:
    print(contador)
    contador += 1  # Suma 1 en cada vuelta para avanzar
```

**⚙️ Comentario de funcionamiento:** En cada iteración se imprime el valor actual de `contador` y luego se incrementa en 1; cuando `contador` llega a 101, la condición `contador <= 100` se vuelve `False` y el bucle termina.

---

### 5.4 Números pares del 1 al 100 con for (paso de 2)

**📌 Enunciado:** Mostrar únicamente los números pares del 1 al 100 usando el tercer parámetro de `range()`.

**💡 Explicación / Definición:** `range(inicio, fin, paso)` permite definir un incremento distinto de 1. Empezando en 2 y saltando de 2 en 2, se obtienen solo números pares.

```python
# Empezamos en 2, vamos hasta el 101 (para incluir el 100) y saltamos de 2 en 2
for i in range(2, 101, 2):
    print(i, end=" ")
```

**⚙️ Comentario de funcionamiento:** `range(2, 101, 2)` genera 2, 4, 6, ..., 100, evitando así tener que usar un `if` para filtrar pares.

---

### 5.5 Números pares del 1 al 100 con while (paso de 2)

**📌 Enunciado:** Igual al anterior, pero con `while`.

**💡 Explicación / Definición:** El contador se inicializa en 2 y se incrementa de 2 en 2 en cada vuelta, replicando manualmente el comportamiento del `range` con paso.

```python
contador = 2

while contador <= 100:
    print(contador, end=" ")
    contador += 2  # Incrementa de dos en dos
```

**⚙️ Comentario de funcionamiento:** El bucle continúa mientras `contador` sea menor o igual a 100, sumando 2 en cada vuelta hasta superar ese límite.

---

### 5.6 Números pares con while True y break

**📌 Enunciado:** Mostrar los números pares del 1 al 100 utilizando un bucle infinito controlado por `break`.

**💡 Explicación / Definición:** `while True` crea un bucle que se repetiría para siempre si no existiera una condición de salida explícita. `break` interrumpe el bucle inmediatamente cuando se cumple la condición indicada, sin importar en qué punto del bloque se encuentre.

```python
contador = 2

while True:
    print(contador, end=" ")
    contador += 2
    
    # Condición de salida al final del bloque (evalúa después de ejecutar)
    if contador > 100:
        break  # Rompe y sale del bucle
```

**⚙️ Comentario de funcionamiento:** A diferencia de un `while` normal, aquí la condición de salida se evalúa **después** de imprimir y de incrementar, por eso se coloca un `if` con `break` al final del bloque.

---

## 6. Números pares e impares

### 6.1 Pares del 1 al 100 usando el operador módulo

**📌 Enunciado:** Identificar los números pares del 1 al 100 utilizando el operador `%` (módulo), que devuelve el residuo de una división.

**💡 Explicación / Definición:** Un número es par si el residuo de dividirlo entre 2 es 0 (`i % 2 == 0`).

```python
for i in range(1, 101):
    if i % 2 == 0:
        print(f"{i} es par")
```

**⚙️ Comentario de funcionamiento:** El bucle recorre todos los números del 1 al 100 y, para cada uno, evalúa si el residuo de dividir entre 2 es 0; si lo es, se considera par y se imprime.

---

### 6.2 Pares hasta un límite ingresado por el usuario (for)

**📌 Enunciado:** Igual al anterior, pero el límite superior lo define el usuario.

**💡 Explicación / Definición:** Se suma 1 al límite dentro de `range()` porque el segundo argumento de `range` es exclusivo; sumar 1 asegura que el número límite también se evalúe.

```python
# Pedimos al usuario hasta qué número quiere evaluar
limite = int(input("Ingresa el número límite: "))

# Sumamos +1 al límite para que incluya ese número en la evaluación
for i in range(1, limite + 1):
    if i % 2 == 0:
        print(f"{i} es par")
```

**⚙️ Comentario de funcionamiento:** Si el usuario ingresa, por ejemplo, 20, `range(1, 21)` recorrerá del 1 al 20 inclusive, evaluando la paridad de cada número.

---

### 6.3 Pares hasta un límite ingresado por el usuario (while)

**📌 Enunciado:** Misma lógica que 6.2, pero con `while`.

**💡 Explicación / Definición:** Se controla el avance manualmente con un contador `i` que se incrementa de 1 en 1, comparándolo en cada vuelta contra `limite`.

```python
limite = int(input("Ingresa el número límite (while): "))
i = 1

while i <= limite:
    if i % 2 == 0:
        print(f"{i} es par")
    i += 1  # Avanzamos de uno en uno
```

**⚙️ Comentario de funcionamiento:** El bucle sigue ejecutándose mientras `i` no supere `limite`; en cada vuelta se evalúa la paridad y luego se incrementa `i`.

---

### 6.4 Impares del 1 al 100 (for)

**📌 Enunciado:** Mostrar los números impares del 1 al 100.

**💡 Explicación / Definición:** Un número es impar si el residuo de dividirlo entre 2 es distinto de 0 (`i % 2 != 0`, donde `!=` significa "diferente de").

```python
# Recorremos del 1 al 100
for i in range(1, 101):
    if i % 2 != 0:  # != significa "diferente de"
        print(f"{i} es impar")
```

**⚙️ Comentario de funcionamiento:** Complementa el ejercicio 6.1: en lugar de buscar residuo 0, busca residuo distinto de 0, capturando así todos los números impares.

---

### 6.5 Impares del 1 al 100 (while)

**📌 Enunciado:** Igual al 6.4, con `while`.

```python
i = 1
while i <= 100:
    if i % 2 != 0:
        print(f"{i} es impar")
    i += 1
```

**⚙️ Comentario de funcionamiento:** Recorre del 1 al 100 con un contador manual, imprimiendo únicamente los valores cuyo residuo al dividir entre 2 no sea 0.

---

### 6.6 Impares hasta un límite (for)

```python
limite = int(input("Ingresa el número límite (for impares): "))

for i in range(1, limite + 1):
    if i % 2 != 0:
        print(f"{i} es impar")
```

**⚙️ Comentario de funcionamiento:** Combina la lógica de límite dinámico (ejercicio 6.2) con la detección de impares (ejercicio 6.4).

---

### 6.7 Impares hasta un límite (while)

```python
limite = int(input("Ingresa el número límite (while impares): "))
i = 1

while i <= limite:
    if i % 2 != 0:
        print(f"{i} es impar")
    i += 1
```

**⚙️ Comentario de funcionamiento:** Misma lógica que 6.6, pero controlada con `while` y un contador manual.

---

### 6.8 Impares con range de paso 2 (versión corta)

**📌 Enunciado:** Obtener los números impares hasta un límite sin usar `if`, aprovechando el paso de `range()`.

**💡 Explicación / Definición:** Al iniciar en 1 y saltar de 2 en 2, `range()` genera directamente solo números impares, evitando la necesidad de validar con el operador módulo.

```python
# Ejemplo ultra corto con for
limite = int(input("Ingresa el límite: "))
for i in range(1, limite + 1, 2):
    print(f"{i} es impar")
```

**⚙️ Comentario de funcionamiento:** `range(1, limite+1, 2)` genera 1, 3, 5, 7... hasta el límite, por lo que cada valor generado ya es impar por construcción.

---

## 7. Tablas de multiplicar

### 7.1 Todas las tablas del 1 al 10 (bucles anidados)

**📌 Enunciado:** Mostrar las tablas de multiplicar del 1 al 10, cada una completa del 1 al 10.

**💡 Explicación / Definición:** Un **bucle anidado** es un bucle dentro de otro. El bucle externo (`i`) controla qué tabla se muestra, y el bucle interno (`j`) controla los multiplicadores del 1 al 10 para esa tabla.

```python
# El primer bucle va del 1 al 10 (las tablas)
for i in range(1, 11):
    print(f"\n=== TABLA DEL {i} ===") # Título para separar cada tabla
    
    # El segundo bucle va del 1 al 10 (los multiplicadores)
    for j in range(1, 11):
        resultado = i * j
        print(f"{i} x {j} = {resultado}")
```

**⚙️ Comentario de funcionamiento:** Por cada valor de `i` (1 a 10), el bucle interno recorre completamente `j` (1 a 10) antes de que `i` avance al siguiente número, generando así las 10 tablas completas en orden.

---

### 7.2 Tabla específica elegida por el usuario

**📌 Enunciado:** Mostrar solo la tabla de multiplicar que el usuario indique.

```python
# Pedimos al usuario el número de la tabla que desea ver
numero_tabla = int(input("¿Qué tabla de multiplicar quieres ver?: "))

print(f"\n=== Mostrando la tabla del {numero_tabla} ===")

# Un solo bucle que va del 1 al 10
for i in range(1, 11):
    resultado = numero_tabla * i
    print(f"{numero_tabla} x {i} = {resultado}")
```

**⚙️ Comentario de funcionamiento:** Al fijar `numero_tabla` como uno de los factores, ya no se necesita bucle anidado: un solo `for` de 1 a 10 basta para generar la tabla completa de ese número.

---

### 7.3 Tabla con rango de multiplicadores personalizado

**📌 Enunciado:** Igual al anterior, pero el usuario también decide hasta qué número multiplicar.

```python
# Variación rápida
tabla = int(input("¿Qué tabla quieres?: "))
hasta = int(input("¿Hasta qué número quieres multiplicar?: "))

for i in range(1, hasta + 1):
    print(f"{tabla} x {i} = {tabla * i}")
```

**⚙️ Comentario de funcionamiento:** El límite superior del bucle ahora depende de la variable `hasta` ingresada por el usuario, en vez de estar fijo en 10, dando mayor flexibilidad al ejercicio.

---

## 8. Números primos

### 8.1 Primos hasta 100 (método de fuerza bruta)

**📌 Enunciado:** Encontrar todos los números primos entre 2 y 100.

**💡 Explicación / Definición:** Un número primo es aquel que solo es divisible entre 1 y sí mismo. La estrategia de "fuerza bruta" consiste en, para cada número, probar si algún valor menor lo divide exactamente; si se encuentra un divisor, deja de ser primo. La bandera `es_primo` (booleana) se usa para recordar ese estado dentro del bucle.

```python
print("=== NÚMEROS PRIMOS HASTA EL 100 ===")

# Recorremos los números del 2 al 100 (el 1 no es primo)
for num in range(2, 101):
    es_primo = True  # Asumimos que el número es primo inicialmente
    
    # Buscamos si tiene algún divisor entre 2 y el número anterior a él
    for i in range(2, num):
        if num % i == 0:
            es_primo = False  # Encontramos un divisor, ya no es primo
            break             # Rompemos el bucle interno para ahorrar tiempo
            
    # Si ningún número lo dividió de forma exacta, es primo
    if es_primo:
        print(num, end=" ")
```

**⚙️ Comentario de funcionamiento:** Para cada `num`, el bucle interno prueba divisores desde 2 hasta `num-1`; en cuanto encuentra uno que divide exacto (`num % i == 0`), marca `es_primo = False` y corta el bucle interno con `break` (no tiene sentido seguir probando). Si el bucle interno termina sin encontrar divisores, `num` es primo.

---

### 8.2 Primos hasta un límite ingresado por el usuario

```python
# Pedimos el número límite al usuario
limite = int(input("¿Hasta qué número quieres buscar números primos?: "))

print(f"\n=== Números primos encontrados hasta el {limite} ===")

for num in range(2, limite + 1):
    es_primo = True
    
    for i in range(2, num):
        if num % i == 0:
            es_primo = False
            break
            
    if es_primo:
        print(num, end=" ")
```

**⚙️ Comentario de funcionamiento:** Misma lógica de fuerza bruta del ejercicio 8.1, pero el límite superior de búsqueda ahora es dinámico según lo que escriba el usuario.

---

### 8.3 Primos con for-else (método corto)

**📌 Enunciado:** Repetir la búsqueda de primos usando la cláusula `else` asociada a un `for`, en vez de una variable bandera.

**💡 Explicación / Definición:** En Python, un bucle `for` puede tener un bloque `else` que se ejecuta **solo si el bucle terminó completo sin ejecutar un `break`**. Esto permite prescindir de la variable `es_primo`.

```python
limite = int(input("Ingresa el límite (método corto): "))

for num in range(2, limite + 1):
    for i in range(2, num):
        if num % i == 0:
            break  # Si encuentra divisor, rompe el bucle y NO va al else
    else:
        # Solo se ejecuta si el bucle 'for i' terminó sin encontrar divisores
        print(num, end=" ")
```

**⚙️ Comentario de funcionamiento:** Si el bucle interno (`for i`) encuentra un divisor exacto, ejecuta `break` y por lo tanto **se salta** el `else`; si el bucle interno termina "de forma natural" (recorrió todos los valores sin romperse), el `else` se dispara y confirma que `num` es primo.

---

## 9. Serie de Fibonacci

### 9.1 Fibonacci con cantidad fija de términos

**📌 Enunciado:** Mostrar los primeros 10 términos de la serie de Fibonacci.

**💡 Explicación / Definición:** La serie de Fibonacci comienza en 0 y 1, y cada término siguiente es la suma de los dos anteriores. La asignación múltiple `a, b = b, a + b` es una característica de Python que permite actualizar ambas variables **al mismo tiempo**, sin necesitar una variable temporal auxiliar.

```python
# Definimos cuántos números queremos mostrar
limite_fijo = 10

# Inicializamos los dos primeros números de la serie
a = 0
b = 1

print("=== FIBONACCI (PRIMEROS 10 TÉRMINOS) ===")

# Usamos el for para repetir el proceso la cantidad de veces exacta
for _ in range(limite_fijo):
    print(a, end=" ")
    
    # Truco de Python: Actualizamos ambos valores al mismo tiempo
    # 'a' toma el valor de 'b', y 'b' toma la suma de ambos (el nuevo número)
    a, b = b, a + b
```

**⚙️ Comentario de funcionamiento:** El guion bajo `_` como variable del `for` indica que no nos interesa su valor (solo se usa para repetir 10 veces). En cada vuelta se imprime `a` (el término actual) y luego se recalculan `a` y `b` para la siguiente iteración.

---

### 9.2 Fibonacci con cantidad de términos ingresada por el usuario

```python
# Pedimos la cantidad de términos al usuario
cant_terminos = int(input("¿Cuántos números de la serie de Fibonacci quieres ver?: "))

a = 0
b = 1

print(f"\n=== MUESTRAN CO PRINCIPIO DE LA SERIE ({cant_terminos} TÉRMINOS) ===")

# El bucle for se adaptará al número que escribió el usuario
for _ in range(cant_terminos):
    print(a, end=" ")
    a, b = b, a + b
```

**⚙️ Comentario de funcionamiento:** Idéntico al 9.1, pero `limite_fijo` se reemplaza por `cant_terminos`, un valor dinámico proporcionado por el usuario.

---

## 10. Factorial y permutaciones

### 10.1 Factorial manual con bucle for (n=5)

**📌 Enunciado:** Calcular el factorial de un número (`n!`) usando un bucle, sin funciones predefinidas.

**💡 Explicación / Definición:** El factorial de `n` es el producto de todos los enteros positivos desde 1 hasta `n` (ej.: `5! = 1×2×3×4×5 = 120`). El operador `*=` multiplica la variable por el valor de la derecha y guarda el resultado en la misma variable (equivalente a `factorial = factorial * i`).

```python
# El factorial se calcula multiplicando todos los números desde 1 hasta n.
n = 5
factorial = 1

for i in range(1, n + 1):
    factorial *= i

print(f"El factorial de {n} es: {factorial}")
```

**⚙️ Comentario de funcionamiento:** `factorial` se inicializa en 1 (elemento neutro de la multiplicación) y se va multiplicando por cada número de 1 a `n`, acumulando el resultado final.

---

### 10.2 Factorial manual con bucle for (n=6, versión comentada)

```python
# EJERCICIO: Calcular el factorial de un número usando un bucle for

n = 6
factorial = 1

for i in range(1, n + 1):
    factorial *= i

print(f"El factorial de {n} es: {factorial}")

# ¿CÓMO FUNCIONA?
# El factorial se obtiene multiplicando todos los números desde 1 hasta n.
# El bucle for recorre: 1, 2, 3, 4, 5, 6
# En cada vuelta, factorial = factorial * i
# Resultado final: 720
```

**⚙️ Comentario de funcionamiento:** Misma lógica del ejercicio 10.1 aplicada a `n = 6`; el resultado esperado es `720` (1×2×3×4×5×6).

---

### 10.3 Permutaciones de tres números con bucles anidados

**📌 Enunciado:** Generar todas las combinaciones posibles ordenando tres números distintos, sin repetir ninguno en la misma permutación.

**💡 Explicación / Definición:** Se usan **tres bucles anidados** (`i`, `j`, `k`), cada uno recorriendo los índices de la lista. Las condiciones `if j != i` y `if k != i and k != j` garantizan que no se repita la misma posición en una misma permutación.

```python
# EJERCICIO: Generar todas las permutaciones posibles de tres números usando bucles

numeros = [1, 2, 3]

for i in range(len(numeros)):
    for j in range(len(numeros)):
        if j != i:
            for k in range(len(numeros)):
                if k != i and k != j:
                    print(numeros[i], numeros[j], numeros[k])

# ¿CÓMO FUNCIONA?
# Se usan tres bucles para elegir posiciones distintas.
# i, j y k representan índices diferentes.
# Las condiciones evitan repetir el mismo número en la misma permutación.
# Se generan las 6 permutaciones posibles:
# 1 2 3
# 1 3 2
# 2 1 3
# 2 3 1
# 3 1 2
# 3 2 1
```

**⚙️ Comentario de funcionamiento:** `len(numeros)` es 3, por lo que `i`, `j` y `k` recorren los índices 0, 1 y 2. Cada combinación válida de índices distintos entre sí produce una permutación única de los tres números, dando un total de 3! = 6 resultados.

---

### 10.4 Permutación P(n, r) sin usar factorial

**📌 Enunciado:** Calcular la permutación P(n, r) —es decir, de cuántas formas se pueden ordenar `r` elementos elegidos de un total de `n`— usando un bucle descendente en lugar de la fórmula con factoriales.

**💡 Explicación / Definición:** La fórmula matemática es `P(n, r) = n × (n-1) × (n-2) × ... × (n-r+1)`. `range(n, n - r, -1)` genera una secuencia descendente con `r` valores exactos, evitando calcular factoriales completos (más costoso computacionalmente para números grandes).

```python
# EJERCICIO: Calcular la permutación P(n, r) usando un bucle sin factorial

n = 7
r = 4

resultado = 1
for i in range(n, n - r, -1):
    resultado *= i

print(f"P({n}, {r}) = {resultado}")

# ¿CÓMO FUNCIONA?
# La fórmula P(n, r) = n * (n-1) * (n-2) ... (n-r+1)
# El bucle recorre: 7, 6, 5, 4  (cuatro valores porque r = 4)
# Multiplica cada uno para obtener la permutación.
# Resultado final: 840
```

**⚙️ Comentario de funcionamiento:** Con `n=7` y `r=4`, `range(7, 3, -1)` genera 7, 6, 5, 4; multiplicando estos cuatro valores se obtiene `840`, equivalente a `7! / (7-4)!` pero sin calcular los factoriales completos.

---

### 10.5 Factorial con la librería math

**📌 Enunciado:** Calcular un factorial utilizando la función predefinida de Python en lugar de un bucle manual.

**💡 Explicación / Definición:** El módulo `math` de la biblioteca estándar incluye `math.factorial(n)`, una función optimizada que evita tener que programar el bucle manualmente.

```python
import math

# Ejemplo de factorial
n = 5
resultado = math.factorial(n)
print(f"El factorial de {n} es: {resultado}")
```

**⚙️ Comentario de funcionamiento:** `math.factorial(5)` devuelve directamente `120`, el mismo resultado que el bucle manual del ejercicio 10.1, pero con una sola línea de código.

---

### 10.6 Permutación P(n, r) con la librería math

**📌 Enunciado:** Calcular P(n, r) utilizando `math.factorial` en lugar de un bucle.

**💡 Explicación / Definición:** La fórmula `P(n, r) = n! / (n-r)!` se traduce directamente a código usando divisón entera (`//`) para obtener un resultado sin decimales.

```python
import math

# Permutación P(n, r)
n = 5
r = 3

permutacion = math.factorial(n) // math.factorial(n - r)
print(f"P({n}, {r}) = {permutacion}")
```

**⚙️ Comentario de funcionamiento:** Se calcula `5! = 120` y `(5-3)! = 2! = 2`, y la división entera `120 // 2` da como resultado `60`.

---

### 10.7 Permutaciones con la librería itertools

**📌 Enunciado:** Generar todas las permutaciones posibles de un conjunto de elementos usando una herramienta especializada de Python.

**💡 Explicación / Definición:** El módulo `itertools` ofrece `permutations()`, una función que genera automáticamente todas las combinaciones ordenadas posibles de una lista, sin necesidad de escribir bucles anidados manualmente (como en el ejercicio 10.3).

```python
import itertools

elementos = ['A', 'B', 'C']
perms = list(itertools.permutations(elementos))

print("Permutaciones de A, B, C:")
for p in perms:
    print(p)
```

**⚙️ Comentario de funcionamiento:** `itertools.permutations(elementos)` devuelve un objeto iterador que se convierte en lista con `list()`; cada elemento de esa lista es una tupla que representa un orden distinto de `'A'`, `'B'`, `'C'` (6 permutaciones en total, igual que en el ejercicio 10.3 pero sin bucles manuales).

---

## 11. Funciones (def)

### 11.1 Función sin parámetros: calcular el cuadrado de un número fijo

**📌 Enunciado:** Crear una función que calcule el cuadrado de un número definido dentro de ella misma (sin recibir parámetros).

**💡 Explicación / Definición:** Una **función** se define con la palabra clave `def`, seguida del nombre y paréntesis. El código dentro de ella no se ejecuta hasta que la función es **llamada** explícitamente (`calcular_cuadrado()`). Al no recibir parámetros, todos los datos que usa están definidos dentro de su propio cuerpo.

```python
# EJERCICIO: Crear una función que calcule el cuadrado de un número fijo

def calcular_cuadrado():
    numero = 5
    resultado = numero * numero
    print(f"El cuadrado de {numero} es: {resultado}")

calcular_cuadrado()

# ¿CÓMO FUNCIONA?
# La función calcular_cuadrado NO recibe parámetros.
# Dentro de ella se define el número 5.
# Luego se multiplica 5 * 5 y se imprime el resultado.
# La función se ejecuta cuando llamamos: calcular_cuadrado()
```

**⚙️ Comentario de funcionamiento:** Al llamar `calcular_cuadrado()`, Python ejecuta todo el bloque indentado bajo `def`: asigna `numero = 5`, calcula `5 * 5` y lo imprime. Si la función nunca se llama, su cuerpo nunca se ejecuta, aunque esté definida.

---

### 11.2 Función que recibe datos por input y devuelve el factorial

**📌 Enunciado:** Crear una función que solicite un número al usuario mediante `input()` y calcule e imprima su factorial.

**💡 Explicación / Definición:** A diferencia del ejercicio 11.1, aquí el dato que usa la función no está fijo en el código, sino que se captura interactivamente **dentro** de la propia función mediante `input()`. Esto combina el concepto de función con el de entrada de datos y bucles ya vistos en la sección de factorial.

```python
# EJERCICIO: Crear una función que reciba un número por input y devuelva su factorial

def factorial_input():
    n = int(input("Escribe un número para calcular su factorial: "))
    factorial = 1

    for i in range(1, n + 1):
        factorial *= i

    print(f"El factorial de {n} es: {factorial}")

factorial_input()

# ¿CÓMO FUNCIONA?
# La función factorial_input pide un número al usuario usando input().
# Convierte ese valor a entero con int().
# Luego usa un bucle for para multiplicar todos los números desde 1 hasta n.
# Finalmente imprime el resultado.
# La función se ejecuta cuando llamamos: factorial_input()
```

**⚙️ Comentario de funcionamiento:** Al llamar `factorial_input()`, la función pausa la ejecución esperando que el usuario escriba un número, lo convierte con `int()`, y reutiliza la misma lógica del bucle `for` con `*=` vista en el ejercicio 10.1, pero ahora encapsulada dentro de una función reutilizable.

---

## 12. Visualización de datos con matplotlib (gráficos individuales)

### 12.1 Gráfico de líneas: tendencia de ventas mensuales

**📌 Enunciado:** Crear un gráfico de líneas que muestre la evolución de las ventas a lo largo de 5 meses.

**💡 Explicación / Definición:** `plt.plot(x, y)` dibuja una línea que conecta los puntos definidos por dos listas paralelas: una de valores en el eje X (meses) y otra en el eje Y (ventas). El parámetro `marker='o'` añade un punto circular visible en cada dato. `plt.grid()` dibuja una cuadrícula de fondo para facilitar la lectura de valores. Este tipo de gráfico es ideal para mostrar **tendencias a lo largo del tiempo**.

```python
# EJERCICIO: Crear un gráfico de líneas para mostrar la tendencia de ventas mensuales

import matplotlib.pyplot as plt

meses = [1, 2, 3, 4, 5]
ventas = [10, 15, 20, 18, 25]

plt.plot(meses, ventas, marker='o')
plt.title("Ventas Mensuales")
plt.xlabel("Mes")
plt.ylabel("Ventas")
plt.grid()
plt.show()

# ¿CÓMO FUNCIONA?
# plt.plot() dibuja una línea conectando los puntos.
# marker='o' coloca un punto en cada valor.
# Se usa para mostrar tendencias en el tiempo.
```

**⚙️ Comentario de funcionamiento:** Cada posición de la lista `meses` se empareja con la posición correspondiente de `ventas` (mes 1 → 10, mes 2 → 15, etc.); `plt.plot()` traza una línea recta entre esos puntos consecutivos, y `plt.show()` abre la ventana con el gráfico renderizado.

> ℹ️ **Nota:** este ejercicio aparece duplicado de forma idéntica en el material original (mismo código, misma explicación); se conserva documentado una sola vez para evitar redundancia.

---

### 12.2 Gráfico de barras: ventas por categoría

**📌 Enunciado:** Comparar visualmente las ventas obtenidas por tres categorías distintas (A, B, C).

**💡 Explicación / Definición:** `plt.bar(categorias, valores)` dibuja una barra vertical por cada categoría, cuya altura representa el valor asociado. Los gráficos de barras son ideales para **comparar magnitudes entre grupos discretos** (a diferencia de las líneas, que muestran continuidad/tendencia).

```python
# EJERCICIO: Crear un gráfico de barras para comparar ventas por categoría

import matplotlib.pyplot as plt

categorias = ["A", "B", "C"]
ventas = [30, 45, 20]

plt.bar(categorias, ventas, color='orange')
plt.title("Ventas por Categoría")
plt.xlabel("Categoría")
plt.ylabel("Ventas")
plt.show()

# ¿CÓMO FUNCIONA?
# plt.bar() crea barras verticales.
# Cada barra representa una categoría.
# Se usa para comparar valores entre grupos.
```

**⚙️ Comentario de funcionamiento:** `plt.bar()` asocia cada elemento de `categorias` con su valor correspondiente en `ventas`, dibujando tres barras de distinta altura (30, 45 y 20) coloreadas en naranja.

---

### 12.3 Gráfico de dispersión: relación entre horas estudiadas y nota

**📌 Enunciado:** Visualizar si existe relación entre la cantidad de horas que estudia una persona y la nota obtenida.

**💡 Explicación / Definición:** `plt.scatter(x, y)` dibuja **puntos individuales** (no conectados por líneas) para cada par de valores. Este tipo de gráfico se usa para detectar **correlaciones** entre dos variables numéricas: si los puntos siguen una tendencia ascendente o descendente clara, sugiere una relación entre ambas.

```python
# EJERCICIO: Crear un gráfico de dispersión para ver la relación entre horas estudiadas y nota

import matplotlib.pyplot as plt

horas = [2, 3, 4, 5, 6]
notas = [60, 65, 70, 75, 80]

plt.scatter(horas, notas, color='red')
plt.title("Relación entre horas y nota")
plt.xlabel("Horas estudiadas")
plt.ylabel("Nota")
plt.show()

# ¿CÓMO FUNCIONA?
# plt.scatter() dibuja puntos individuales.
# Sirve para ver correlaciones entre dos variables.
# Aquí se observa que más horas → mejor nota.
```

**⚙️ Comentario de funcionamiento:** Cada punto rojo representa un par `(horas, nota)`; al observar que los puntos ascienden de izquierda a derecha, se puede inferir visualmente una relación positiva entre horas estudiadas y la nota obtenida.

---

### 12.4 Gráfico de pastel: participación de mercado

**📌 Enunciado:** Mostrar qué porcentaje del mercado ocupa cada una de tres marcas.

**💡 Explicación / Definición:** `plt.pie(valores, labels=..., autopct=...)` dibuja un gráfico circular dividido en porciones proporcionales a cada valor. El parámetro `autopct="%1.1f%%"` es un formato de cadena que muestra el porcentaje de cada porción con un decimal, seguido del símbolo `%`. Se usa para representar **proporciones de un total** (que en conjunto suman 100%).

```python
# EJERCICIO: Crear un gráfico de pastel para mostrar participación de mercado

import matplotlib.pyplot as plt

marcas = ["X", "Y", "Z"]
porcentaje = [50, 30, 20]

plt.pie(porcentaje, labels=marcas, autopct="%1.1f%%")
plt.title("Participación de Mercado")
plt.show()

# ¿CÓMO FUNCIONA?
# plt.pie() crea un gráfico circular.
# autopct muestra el porcentaje dentro del pastel.
# Se usa para ver proporciones de un total.
```

**⚙️ Comentario de funcionamiento:** Los valores `[50, 30, 20]` suman 100, por lo que cada porción del pastel ocupa exactamente ese porcentaje del círculo completo; `autopct` calcula y escribe automáticamente el porcentaje dentro de cada sección.

---

### 12.5 Histograma: distribución de edades

**📌 Enunciado:** Analizar cómo se distribuye un conjunto de edades agrupándolas en rangos.

**💡 Explicación / Definición:** `plt.hist(datos, bins=n)` agrupa los valores numéricos en `n` intervalos ("bins" o "cubetas") de igual tamaño y dibuja una barra por cada intervalo, cuya altura representa cuántos datos caen dentro de ese rango. A diferencia de `plt.bar()` (que usa categorías ya definidas), el histograma **construye los rangos automáticamente** a partir de los datos.

```python
# EJERCICIO: Crear un histograma para mostrar la distribución de edades

import matplotlib.pyplot as plt

edades = [20, 22, 25, 30, 30, 32, 35, 40]

plt.hist(edades, bins=5, color='green')
plt.title("Distribución de Edades")
plt.xlabel("Edad")
plt.ylabel("Frecuencia")
plt.show()

# ¿CÓMO FUNCIONA?
# plt.hist() agrupa los valores en rangos (bins).
# Muestra cuántas veces aparece cada rango.
# Se usa para analizar distribuciones.
```

**⚙️ Comentario de funcionamiento:** `bins=5` le indica a matplotlib que divida el rango total de edades (de 20 a 40) en 5 intervalos iguales, y cuenta cuántas edades de la lista `edades` caen dentro de cada intervalo, dibujando una barra verde por cada uno según esa frecuencia.

---

## 13. Dashboards comparativos con subplots (dos gráficos lado a lado)

> 💡 **Concepto común a toda esta sección:** `plt.subplots(1, 2, figsize=(12,5))` crea **una sola figura** dividida en 1 fila y 2 columnas, devolviendo dos "ejes" (`ax1`, `ax2`) que funcionan como lienzos independientes donde dibujar cada gráfico por separado. Esto permite comparar dos variables relacionadas **sin que se superpongan ni compitan por el mismo espacio**. `plt.tight_layout()` ajusta automáticamente los márgenes para que los títulos y etiquetas no se corten ni se encimen.

### 13.1 Depósitos mensuales e intereses ganados

**📌 Enunciado:** Mostrar en dos gráficos separados, uno al lado del otro, la evolución de los depósitos mensuales (línea) y los intereses ganados (barras), sin usar tablas que puedan desordenar el diseño.

```python
# EJERCICIO: Mostrar depósitos e intereses en dos gráficos lado a lado (sin tabla)

import matplotlib.pyplot as plt

meses = ["Ene","Feb","Mar","Abr","May"]
depositos = [1000, 1500, 1800, 2000, 2500]
intereses = [10, 15, 18, 20, 25]

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12,5))

ax1.plot(meses, depositos, marker='o', color='blue')
ax1.set_title("Depósitos Mensuales")
ax1.set_xlabel("Mes")
ax1.set_ylabel("Monto")

ax2.bar(meses, intereses, color='green')
ax2.set_title("Intereses Ganados")
ax2.set_xlabel("Mes")
ax2.set_ylabel("Interés")

plt.tight_layout()
plt.show()

# ¿CÓMO FUNCIONA?
# Se crean dos gráficos lado a lado usando subplots(1,2).
# No hay tabla, así nada se encima.
# Dashboard limpio y profesional.
```

**⚙️ Comentario de funcionamiento:** `ax1` recibe el gráfico de línea de los depósitos (tendencia de crecimiento mes a mes) y `ax2` recibe el gráfico de barras de los intereses; ambos se dibujan en la misma figura `fig`, pero en espacios completamente independientes gracias al desempaquetado `(ax1, ax2)`.

---

### 13.2 Cartera total y morosidad

**📌 Enunciado:** Comparar el crecimiento de la cartera total de préstamos frente al porcentaje de morosidad mes a mes.

```python
# EJERCICIO: Mostrar cartera total y morosidad en dos gráficos lado a lado

import matplotlib.pyplot as plt

meses = ["Ene","Feb","Mar","Abr","May"]
cartera = [50000, 52000, 54000, 56000, 60000]
morosidad = [5, 4.8, 4.5, 4.3, 4.1]

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12,5))

ax1.plot(meses, cartera, marker='o', color='purple')
ax1.set_title("Cartera Total")
ax1.set_xlabel("Mes")
ax1.set_ylabel("Monto")

ax2.bar(meses, morosidad, color='red')
ax2.set_title("Morosidad (%)")
ax2.set_xlabel("Mes")
ax2.set_ylabel("Porcentaje")

plt.tight_layout()
plt.show()

# ¿CÓMO FUNCIONA?
# Línea para cartera (crecimiento).
# Barras para morosidad (riesgo).
# Sin tabla → nada se desborda.
```

**⚙️ Comentario de funcionamiento:** El gráfico de línea (`ax1`) resalta la tendencia de crecimiento constante de la cartera, mientras que el gráfico de barras (`ax2`) permite comparar visualmente el nivel de riesgo (morosidad) mes a mes; al estar en ejes separados, una escala de miles (cartera) no distorsiona la lectura de una escala de porcentaje (morosidad).

---

### 13.3 Ingresos por intereses y gastos operativos

**📌 Enunciado:** Comparar los ingresos por intereses contra los gastos operativos mes a mes, para evaluar la rentabilidad.

```python
# EJERCICIO: Comparar ingresos por intereses y gastos operativos con dos gráficos

import matplotlib.pyplot as plt

meses = ["Ene","Feb","Mar","Abr","May"]
ingresos = [8000, 8200, 8500, 9000, 9500]
gastos = [3000, 3200, 3100, 3300, 3400]

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12,5))

ax1.plot(meses, ingresos, marker='o', color='green')
ax1.set_title("Ingresos por Intereses")
ax1.set_xlabel("Mes")
ax1.set_ylabel("Monto")

ax2.bar(meses, gastos, color='gray')
ax2.set_title("Gastos Operativos")
ax2.set_xlabel("Mes")
ax2.set_ylabel("Monto")

plt.tight_layout()
plt.show()

# ¿CÓMO FUNCIONA?
# Dos gráficos separados y claros.
# Ideal para ver rentabilidad mensual.
```

**⚙️ Comentario de funcionamiento:** Al colocar ingresos (línea verde) y gastos (barras grises) en paneles separados pero alineados, resulta fácil comparar visualmente si los ingresos crecen más rápido que los gastos mes a mes, sin que ambas series compitan por la misma escala del eje Y.

---

### 13.4 Ahorros acumulados y rendimiento mensual

**📌 Enunciado:** Mostrar cómo crecen los ahorros acumulados junto con el rendimiento (interés) que generan cada mes.

```python
# EJERCICIO: Mostrar ahorros acumulados y rendimiento mensual en dos gráficos

import matplotlib.pyplot as plt

meses = ["Ene","Feb","Mar","Abr","May"]
ahorros = [2000, 2500, 3000, 3500, 4200]
rendimiento = [20, 25, 30, 35, 42]

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12,5))

ax1.plot(meses, ahorros, marker='o', color='blue')
ax1.set_title("Ahorros Acumulados")
ax1.set_xlabel("Mes")
ax1.set_ylabel("Monto")

ax2.bar(meses, rendimiento, color='orange')
ax2.set_title("Rendimiento Mensual")
ax2.set_xlabel("Mes")
ax2.set_ylabel("Interés")

plt.tight_layout()
plt.show()

# ¿CÓMO FUNCIONA?
# Línea para ahorros (acumulación).
# Barras para rendimiento (interés).
# Presentación limpia sin tablas.
```

**⚙️ Comentario de funcionamiento:** El patrón se repite: variable acumulativa/tendencia → gráfico de línea (`ax1`); variable puntual por período → gráfico de barras (`ax2`). Aquí se observa cómo, a medida que los ahorros acumulados crecen, el rendimiento mensual generado también aumenta proporcionalmente.

---

### 13.5 Transacciones y comisiones

**📌 Enunciado:** Comparar el volumen de transacciones procesadas contra los ingresos generados por comisiones cada mes.

```python
# EJERCICIO: Mostrar transacciones y comisiones en dos gráficos lado a lado

import matplotlib.pyplot as plt

meses = ["Ene","Feb","Mar","Abr","May"]
transacciones = [1200, 1300, 1400, 1500, 1600]
comisiones = [300, 320, 350, 380, 400]

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12,5))

ax1.plot(meses, transacciones, marker='o', color='brown')
ax1.set_title("Transacciones")
ax1.set_xlabel("Mes")
ax1.set_ylabel("Cantidad")

ax2.bar(meses, comisiones, color='cyan')
ax2.set_title("Comisiones")
ax2.set_xlabel("Mes")
ax2.set_ylabel("Monto")

plt.tight_layout()
plt.show()

# ¿CÓMO FUNCIONA?
# Línea para volumen de transacciones.
# Barras para ingresos por comisiones.
# Nada se encime porque no hay tablas.
```

**⚙️ Comentario de funcionamiento:** El eje `ax1` traza la cantidad de transacciones procesadas mes a mes (volumen operativo), mientras que `ax2` muestra el monto de comisiones generadas; al crecer ambas variables de forma paralela, el dashboard permite validar visualmente que más transacciones se traducen en más ingresos por comisión.

---

## 14. Caso integrador: Sistema de análisis de ventas

### 14.1 Definición de categorías y estructura de una venta

**📌 Enunciado:** Modelar los datos base de un sistema de ventas: productos, vendedores, regiones y métodos de pago, además de la estructura que representará cada venta individual.

**💡 Explicación / Definición:** Las **listas** (`[]`) agrupan valores relacionados (como los nombres de productos). Un **diccionario** (`{}`) representa un registro con pares clave-valor, ideal para modelar una "venta" con sus distintos atributos (cliente, vendedor, producto, etc.). La comprensión de listas `[f"Cliente {i}" for i in range(1, 41)]` genera automáticamente 40 nombres de clientes sin escribirlos uno por uno.

```python
# 1. DEFINICIÓN DE NUESTRAS CATEGORÍAS (Tus datos base)
productos = ["Laptop", "Celular", "Tablet", "Audífonos", "Monitor"]
vendedores = ["Ana", "Carlos", "Beatriz", "Diego", "Elena"]
regiones = ["Norte", "Sur", "Centro"]
metodos_pago = ["Efectivo", "Tarjeta", "Transferencia"]

# Nota: Para los 40 clientes, en vez de escribir una lista gigante, 
# los identificaremos de forma automática como 'Cliente 1', 'Cliente 2', etc.


# 2. MODELADO DE UNA VENTA INDIVIDUAL (Ejemplo de estructura de un ticket)
# Cada venta realizada será un diccionario con esta forma:
venta_ejemplo = {
    "cliente": "Cliente 24",       # Del 1 al 40
    "vendedor": "Ana",            # Uno de los 5
    "producto": "Laptop",          # Uno de los 5
    "metodo_pago": "Tarjeta",      # Uno de los 3
    "region": "Norte",             # Una de las 3
    "total": 1200.50               # El dinero de la venta
}


# 3. HISTORIAL GENERAL DE VENTAS (Tu base de datos temporal)
# Aquí guardarás todas las ventas que se vayan registrando en el día
historial_ventas = [
    {"cliente": "Cliente 5", "vendedor": "Carlos", "producto": "Celular", "metodo_pago": "Efectivo", "region": "Sur", "total": 500.00},
    {"cliente": "Cliente 12", "vendedor": "Ana", "producto": "Laptop", "metodo_pago": "Tarjeta", "region": "Norte", "total": 1200.00},
    {"cliente": "Cliente 5", "vendedor": "Carlos", "producto": "Audífonos", "metodo_pago": "Transferencia", "region": "Sur", "total": 150.00},
    {"cliente": "Cliente 38", "vendedor": "Elena", "producto": "Monitor", "metodo_pago": "Tarjeta", "region": "Centro", "total": 350.00}
]


# 4. CÓMO GENERAR LOS RESÚMENES (Ejemplo con un bucle)
# Supongamos que queremos saber cuánto vendió cada REGIÓN en total:

print("=== RESUMEN DE VENTAS POR REGIÓN ===")

# Creamos un diccionario para acumular el dinero por cada región
ventas_por_region = {"Norte": 0.0, "Sur": 0.0, "Centro": 0.0}

# Recorremos nuestro historial sumando los totales
for venta in historial_ventas:
    region_venta = venta["region"]
    monto = venta["total"]
    
    # Sumamos el monto a la región correspondiente
    ventas_por_region[region_venta] += monto

# Mostramos los resultados en pantalla con el formato de 2 decimales que aprendiste
for region, total in ventas_por_region.items():
    print(f"Región {region}: ${total:.2f}")
```

**⚙️ Comentario de funcionamiento:** Se define primero el "catálogo" de valores posibles (listas), luego la forma de un registro individual (diccionario `venta_ejemplo`), y después una lista de diccionarios (`historial_ventas`) que simula varias ventas ya registradas. El bucle final recorre cada venta, extrae su región y su total, y acumula el monto en el diccionario `ventas_por_region` usando `+=`. El formato `:.2f` dentro del f-string limita la salida a 2 decimales, típico para mostrar montos monetarios.

---

### 14.2 Simulación de 100 ventas aleatorias y reportes por categoría

**📌 Enunciado:** Generar 100 ventas simuladas con datos aleatorios y producir reportes acumulados por producto, vendedor, región, método de pago y un top 5 de clientes.

**💡 Explicación / Definición:** El módulo `random` permite generar valores aleatorios: `random.choice(lista)` elige un elemento al azar de una lista, y `random.uniform(min, max)` genera un número decimal aleatorio dentro de un rango. `round(x, 2)` redondea a 2 decimales. La función `sorted()` con el parámetro `key=lambda x: x[1]` ordena una lista de tuplas por su segundo valor (el monto), y `reverse=True` la ordena de mayor a menor.

```python
import random

# 1. DEFINICIÓN DE DATOS BASE
productos = ["Laptop", "Celular", "Tablet", "Audífonos", "Monitor"]
vendedores = ["Ana", "Carlos", "Beatriz", "Diego", "Elena"]
regiones = ["Norte", "Sur", "Centro"]
metodos_pago = ["Efectivo", "Tarjeta", "Transferencia"]
# Creamos una lista automática de 40 clientes: ['Cliente 1', 'Cliente 2', ..., 'Cliente 40']
clientes = [f"Cliente {i}" for i in range(1, 41)]

# 2. SIMULACIÓN DE HISTORIAL DE VENTAS (Generamos 100 ventas aleatorias)
historial_ventas = []
for _ in range(100):
    venta = {
        "cliente": random.choice(clientes),
        "vendedor": random.choice(vendedores),
        "producto": random.choice(productos),
        "metodo_pago": random.choice(metodos_pago),
        "region": random.choice(regiones),
        "total": round(random.uniform(50, 1500), 2)  # Ventas aleatorias entre $50 y $1500
    }
    historial_ventas.add(venta) if hasattr(historial_ventas, 'add') else historial_ventas.append(venta)

# 3. CREACIÓN DE DICCIONARIOS PARA ACUMULAR LOS TOTALES
resumen_productos = {p: 0.0 for p in productos}
resumen_vendedores = {v: 0.0 for v in vendedores}
resumen_regiones = {r: 0.0 for r in regiones}
resumen_pagos = {m: 0.0 for m in metodos_pago}
resumen_clientes = {c: 0.0 for c in clientes}

# 4. PROCESAMIENTO GENERAL (Un solo bucle clasifica todo)
for v in historial_ventas:
    resumen_productos[v["producto"]] += v["total"]
    resumen_vendedores[v["vendedor"]] += v["total"]
    resumen_regiones[v["region"]] += v["total"]
    resumen_pagos[v["metodo_pago"]] += v["total"]
    resumen_clientes[v["cliente"]] += v["total"]

# 5. PRESENTACIÓN DE LOS REPORTES EN CONSOLA
print("==================================================")
print("       REPORTE GLOBAL GENERAL DE VENTAS           ")
print("==================================================")

print("\n📊 VENTAS POR PRODUCTO:")
for k, v in resumen_productos.items():
    print(f"  - {k}: ${v:.2f}")

print("\n➡️ VENTAS POR VENDEDOR:")
for k, v in resumen_vendedores.items():
    print(f"  - {k}: ${v:.2f}")

print("\n📌 VENTAS POR REGIÓN:")
for k, v in resumen_regiones.items():
    print(f"  - {k}: ${v:.2f}")

print("\n💡 VENTAS POR MÉTODO DE PAGO:")
for k, v in resumen_pagos.items():
    print(f"  - {k}: ${v:.2f}")

print("\n🗒️ TOP 5 CLIENTES CON MAYORES COMPRAS:")
# Ordenamos los clientes de mayor a menor gasto y extraemos los primeros 5
clientes_ordenados = sorted(resumen_clientes.items(), key=lambda x: x[1], reverse=True)
for k, v in clientes_ordenados[:5]:
    print(f"  - {k}: ${v:.2f}")
```

**⚙️ Comentario de funcionamiento:** Se generan 100 ventas aleatorias con `random.choice()` y `random.uniform()`, guardando cada una como diccionario dentro de la lista `historial_ventas`. Luego, un único bucle recorre esa lista una sola vez y acumula los montos simultáneamente en cinco diccionarios de resumen distintos (por producto, vendedor, región, método de pago y cliente), usando el nombre de cada categoría como clave. Finalmente, `sorted()` con `key=lambda x: x[1]` ordena los clientes por su total de compras de mayor a menor, y `[:5]` (slicing) toma solo los primeros cinco resultados para el top de clientes.

> ⚠️ **Nota de funcionamiento (documentación, no se altera el código):** la línea `historial_ventas.add(venta) if hasattr(historial_ventas, 'add') else historial_ventas.append(venta)` comprueba si la lista tiene el método `.add()` (propio de los `set`, no de las listas) antes de decidir cómo agregar el elemento; como una lista de Python nunca tiene `.add()`, esta condición siempre es `False` y en la práctica siempre se ejecuta `historial_ventas.append(venta)`.

---

### 14.3 Reportes con distribución por rangos de monto y dashboard visual

**📌 Enunciado:** Extender el sistema de ventas anterior añadiendo una clasificación de las ventas por rangos de monto y visualizando todos los resultados en un dashboard de 6 gráficos con `matplotlib`.

**💡 Explicación / Definición:** `matplotlib.pyplot` es la librería estándar de Python para crear gráficos. `plt.subplots(filas, columnas)` crea una cuadrícula de gráficos (aquí 3 filas × 2 columnas = 6 gráficos) dentro de una sola figura (`fig`), y cada posición se referencia como `axs[fila, columna]`. Se usan distintos tipos de gráfico: barras horizontales (`barh`), barras verticales (`bar`), gráfico de pastel (`pie`) y gráfico de dona (un `pie` con un círculo blanco superpuesto en el centro mediante `plt.Circle`).

```python
import random
import matplotlib.pyplot as plt

# 1. DEFINICIÓN DE DATOS BASE
productos = ["Laptop", "Celular", "Tablet", "Audífonos", "Monitor"]
vendedores = ["Ana", "Carlos", "Beatriz", "Diego", "Elena"]
regiones = ["Norte", "Sur", "Centro"]
metodos_pago = ["Efectivo", "Tarjeta", "Transferencia"]
clientes = [f"Cliente {i}" for i in range(1, 41)]

# 2. SIMULACIÓN DE HISTORIAL DE VENTAS (100 ventas aleatorias)
historial_ventas = []
for _ in range(100):
    venta = {
        "cliente": random.choice(clientes),
        "vendedor": random.choice(vendedores),
        "producto": random.choice(productos),
        "metodo_pago": random.choice(metodos_pago),
        "region": random.choice(regiones),
        "total": round(random.uniform(50, 1500), 2)
    }
    historial_ventas.append(venta)

# 3. DICCIONARIOS DE ACUMULACIÓN
resumen_productos = {p: 0.0 for p in productos}
resumen_vendedores = {v: 0.0 for v in vendedores}
resumen_regiones = {r: 0.0 for r in regiones}
resumen_pagos = {m: 0.0 for m in metodos_pago}
resumen_clientes = {c: 0.0 for c in clientes}

# NUEVO: Rangos de venta
rangos = {
    "50 - 300": 0,
    "301 - 700": 0,
    "701 - 1100": 0,
    "1101 - 1500": 0
}

# 4. PROCESAMIENTO GENERAL
for v in historial_ventas:
    resumen_productos[v["producto"]] += v["total"]
    resumen_vendedores[v["vendedor"]] += v["total"]
    resumen_regiones[v["region"]] += v["total"]
    resumen_pagos[v["metodo_pago"]] += v["total"]
    resumen_clientes[v["cliente"]] += v["total"]

    # Clasificación por rangos
    t = v["total"]
    if 50 <= t <= 300:
        rangos["50 - 300"] += 1
    elif 301 <= t <= 700:
        rangos["301 - 700"] += 1
    elif 701 <= t <= 1100:
        rangos["701 - 1100"] += 1
    else:
        rangos["1101 - 1500"] += 1

# 5. REPORTES EN CONSOLA
print("==================================================")
print("       REPORTE GLOBAL GENERAL DE VENTAS           ")
print("==================================================")

print("\n📊 VENTAS POR PRODUCTO:")
for k, v in resumen_productos.items():
    print(f"  - {k}: ${v:.2f}")

print("\n➡️ VENTAS POR VENDEDOR:")
for k, v in resumen_vendedores.items():
    print(f"  - {k}: ${v:.2f}")

print("\n📌 VENTAS POR REGIÓN:")
for k, v in resumen_regiones.items():
    print(f"  - {k}: ${v:.2f}")

print("\n💡 VENTAS POR MÉTODO DE PAGO:")
for k, v in resumen_pagos.items():
    print(f"  - {k}: ${v:.2f}")

print("\n🗒️ TOP 5 CLIENTES CON MAYORES COMPRAS:")
clientes_ordenados = sorted(resumen_clientes.items(), key=lambda x: x[1], reverse=True)
top_5_clientes = clientes_ordenados[:5]
for k, v in top_5_clientes:
    print(f"  - {k}: ${v:.2f}")

print("\n📈 DISTRIBUCIÓN POR RANGOS DE MONTO:")
for k, v in rangos.items():
    print(f"  - {k}: {v} ventas")

# ==========================================================
# 6. DASHBOARD DE 6 GRÁFICOS
# ==========================================================
fig, axs = plt.subplots(3, 2, figsize=(14, 15))
fig.suptitle("DASHBOARD INTEGRADO DE RESUMEN DE VENTAS", fontsize=16, fontweight='bold')

# --- 1. Ventas por Producto ---
bars1 = axs[0, 0].barh(list(resumen_productos.keys()), list(resumen_productos.values()), color='skyblue')
axs[0, 0].set_title("Ventas por Producto ($)")
axs[0, 0].bar_label(bars1, fmt='$%1.2f', padding=3)

# --- 2. Ventas por Vendedor ---
bars2 = axs[0, 1].bar(list(resumen_vendedores.keys()), list(resumen_vendedores.values()), color='lightgreen')
axs[0, 1].set_title("Desempeño por Vendedor ($)")
axs[0, 1].bar_label(bars2, fmt='$%1.2f', padding=3)

# --- 3. Distribución por Región ---
axs[1, 0].pie(list(resumen_regiones.values()), labels=list(resumen_regiones.keys()),
              autopct='%1.1f%%', startangle=90, colors=['gold', 'coral', 'lightcyan'])
axs[1, 0].set_title("Participación por Región")

# --- 4. Métodos de Pago (Dona) ---
axs[1, 1].pie(list(resumen_pagos.values()), labels=list(resumen_pagos.keys()),
              autopct='%1.1f%%', startangle=140, colors=['violet', 'aquamarine', 'lightgray'])
centro = plt.Circle((0,0), 0.70, fc='white')
axs[1, 1].add_artist(centro)
axs[1, 1].set_title("Uso de Métodos de Pago")

# --- 5. Top 5 Clientes ---
bars5 = axs[2, 0].bar([c[0] for c in top_5_clientes], [c[1] for c in top_5_clientes], color='orchid')
axs[2, 0].set_title("Top 5 Clientes ($)")
axs[2, 0].bar_label(bars5, fmt='$%1.2f', padding=3)

# --- 6. NUEVO: Gráfico de Rangos de Venta ---
axs[2, 1].bar(list(rangos.keys()), list(rangos.values()), color='orange')
axs[2, 1].set_title("Distribución por Rangos de Monto")
axs[2, 1].set_ylabel("Cantidad de Ventas")

plt.tight_layout(rect=[0, 0, 1, 0.96])
plt.show()
```

**⚙️ Comentario de funcionamiento:**
- **Procesamiento:** dentro del mismo bucle que acumula los totales por categoría, se añade una cadena `if/elif/else` que clasifica cada venta (`t = v["total"]`) en uno de cuatro rangos de monto, incrementando el contador correspondiente en el diccionario `rangos`.
- **Dashboard:** `plt.subplots(3, 2, figsize=(14, 15))` crea una figura con 6 espacios organizados en 3 filas y 2 columnas; cada `axs[fila, columna]` es un "subgráfico" independiente donde se dibuja un tipo distinto de visualización (barras horizontales, barras verticales, pastel, dona).
- `bar_label()` añade automáticamente el valor numérico encima de cada barra, con el formato de moneda `'$%1.2f'`.
- El gráfico de dona (gráfico 4) es en realidad un `pie` normal al que se le superpone un círculo blanco (`plt.Circle`) en el centro mediante `add_artist()`, creando el efecto visual de "anillo".
- `plt.tight_layout()` ajusta automáticamente los espacios entre subgráficos para que no se superpongan los títulos, y `plt.show()` finalmente renderiza la ventana con el dashboard completo.

---

### 14.4 Generar un archivo Excel con 500 registros reales

**📌 Enunciado:** Crear un archivo `.xlsx` con 500 registros de ventas simuladas usando nombres de clientes reales (en lugar de "Cliente 1, Cliente 2...").

**💡 Explicación / Definición:** La librería `pandas` permite trabajar con datos tabulares mediante la estructura `DataFrame` (similar a una hoja de cálculo). `pd.DataFrame(lista_de_diccionarios)` convierte una lista de registros en una tabla, y `.to_excel("archivo.xlsx", index=False)` la exporta a un archivo Excel real; `index=False` evita que pandas agregue una columna extra con el número de fila.

```python
# ✅ PRIMERO: GENERAR EL ARCHIVO EXCEL (500 registros reales)

import pandas as pd
import random

# Nombres reales (lista compacta pero auténtica)
nombres_reales = [
    "Juan Pérez", "María Gómez", "Carlos Ramírez", "Ana Martínez", "Luis Rodríguez",
    "Pedro Sánchez", "Laura Fernández", "José Castillo", "Elena Vargas", "Miguel Torres",
    "Beatriz Herrera", "Diego Cruz", "Sofía Morales", "Ricardo Peña", "Valeria Soto",
    "Gabriel Navarro", "Camila Duarte", "Andrés Paredes", "Paola Jiménez", "Samuel Batista",
    "Rosa Méndez", "Javier Aquino", "Patricia Lora", "Fernando Gil", "Daniela Rivas",
    "Héctor Guzmán", "Isabel Cabrera", "Manuel Tejada", "Carmen Salcedo", "Roberto Núñez"
]

productos = ["Laptop", "Celular", "Tablet", "Audífonos", "Monitor"]
vendedores = ["Ana", "Carlos", "Beatriz", "Diego", "Elena"]
regiones = ["Norte", "Sur", "Centro"]
metodos_pago = ["Efectivo", "Tarjeta", "Transferencia"]

# Generar 500 registros reales
data = []
for _ in range(500):
    data.append({
        "Cliente": random.choice(nombres_reales),
        "Vendedor": random.choice(vendedores),
        "Producto": random.choice(productos),
        "Método_Pago": random.choice(metodos_pago),
        "Región": random.choice(regiones),
        "Total": round(random.uniform(50, 1500), 2)
    })

df = pd.DataFrame(data)

# Guardar archivo Excel
df.to_excel("ventas_500_registros.xlsx", index=False)

print("Archivo Excel generado correctamente: ventas_500_registros.xlsx")
```

**⚙️ Comentario de funcionamiento:** Se construye primero una lista de 30 nombres reales; luego un bucle `for _ in range(500)` genera 500 diccionarios, cada uno eligiendo aleatoriamente un nombre, vendedor, producto, método de pago, región y un total decimal aleatorio. Esa lista de 500 diccionarios se convierte en un `DataFrame` de pandas y se exporta directamente a un archivo `.xlsx` en el directorio de trabajo.

---

### 14.5 Dashboard leyendo los datos desde el archivo Excel generado

**📌 Enunciado:** Ajustar el dashboard de 6 gráficos para que, en lugar de generar datos aleatorios en memoria, lea los 500 registros directamente desde el archivo Excel creado en el ejercicio anterior.

**💡 Explicación / Definición:** `pd.read_excel("archivo.xlsx")` carga el contenido del archivo en un `DataFrame`. `.to_dict(orient="records")` convierte ese `DataFrame` en una lista de diccionarios (misma estructura que `historial_ventas` en los ejercicios anteriores), y `.unique()` extrae los valores distintos de una columna (por ejemplo, todos los productos sin repetir), permitiendo reconstruir los diccionarios de resumen sin tener que escribir las categorías manualmente.

```python
# ✅ SEGUNDO: AJUSTAR TU DASHBOARD PARA LEER EL EXCEL DESDE TU PC

import pandas as pd
import matplotlib.pyplot as plt

# === LEER ARCHIVO DESDE TU PC ===
df = pd.read_excel("ventas_500_registros.xlsx")

# === EXTRAER COLUMNAS ===
historial_ventas = df.to_dict(orient="records")

# === DICCIONARIOS DE ACUMULACIÓN ===
productos = df["Producto"].unique()
vendedores = df["Vendedor"].unique()
regiones = df["Región"].unique()
metodos_pago = df["Método_Pago"].unique()
clientes = df["Cliente"].unique()

resumen_productos = {p: 0.0 for p in productos}
resumen_vendedores = {v: 0.0 for v in vendedores}
resumen_regiones = {r: 0.0 for r in regiones}
resumen_pagos = {m: 0.0 for m in metodos_pago}
resumen_clientes = {c: 0.0 for c in clientes}

rangos = {
    "50 - 300": 0,
    "301 - 700": 0,
    "701 - 1100": 0,
    "1101 - 1500": 0
}

# === PROCESAMIENTO ===
for v in historial_ventas:
    resumen_productos[v["Producto"]] += v["Total"]
    resumen_vendedores[v["Vendedor"]] += v["Total"]
    resumen_regiones[v["Región"]] += v["Total"]
    resumen_pagos[v["Método_Pago"]] += v["Total"]
    resumen_clientes[v["Cliente"]] += v["Total"]

    t = v["Total"]
    if 50 <= t <= 300:
        rangos["50 - 300"] += 1
    elif 301 <= t <= 700:
        rangos["301 - 700"] += 1
    elif 701 <= t <= 1100:
        rangos["701 - 1100"] += 1
    else:
        rangos["1101 - 1500"] += 1

# === GRÁFICOS (los mismos 6 que ya tienes) ===
fig, axs = plt.subplots(3, 2, figsize=(14, 15))
fig.suptitle("DASHBOARD INTEGRADO DE RESUMEN DE VENTAS (500 registros reales)", fontsize=16, fontweight='bold')

# 1. Producto
bars1 = axs[0, 0].barh(list(resumen_productos.keys()), list(resumen_productos.values()), color='skyblue')
axs[0, 0].set_title("Ventas por Producto")
axs[0, 0].bar_label(bars1, fmt='$%1.2f')

# 2. Vendedor
bars2 = axs[0, 1].bar(list(resumen_vendedores.keys()), list(resumen_vendedores.values()), color='lightgreen')
axs[0, 1].set_title("Ventas por Vendedor")
axs[0, 1].bar_label(bars2, fmt='$%1.2f')

# 3. Región
axs[1, 0].pie(list(resumen_regiones.values()), labels=list(resumen_regiones.keys()), autopct='%1.1f%%')
axs[1, 0].set_title("Ventas por Región")

# 4. Método de Pago (Dona)
axs[1, 1].pie(list(resumen_pagos.values()), labels=list(resumen_pagos.keys()), autopct='%1.1f%%')
centro = plt.Circle((0,0), 0.70, fc='white')
axs[1, 1].add_artist(centro)
axs[1, 1].set_title("Métodos de Pago")

# 5. Top 5 Clientes
top_5 = sorted(resumen_clientes.items(), key=lambda x: x[1], reverse=True)[:5]
bars5 = axs[2, 0].bar([c[0] for c in top_5], [c[1] for c in top_5], color='orchid')
axs[2, 0].set_title("Top 5 Clientes")
axs[2, 0].bar_label(bars5, fmt='$%1.2f')

# 6. Rangos
axs[2, 1].bar(list(rangos.keys()), list(rangos.values()), color='orange')
axs[2, 1].set_title("Rangos de Monto")

plt.tight_layout(rect=[0, 0, 1, 0.96])
plt.show()
```

**⚙️ Comentario de funcionamiento:** En lugar de simular datos con `random`, el script lee el archivo `ventas_500_registros.xlsx` generado en el ejercicio 14.4 usando `pd.read_excel()`. Las categorías (productos, vendedores, regiones, etc.) ya no se escriben manualmente en listas, sino que se extraen dinámicamente de las columnas del propio archivo con `.unique()`. El resto de la lógica de acumulación, clasificación por rangos y generación del dashboard de 6 gráficos es idéntica a la del ejercicio 14.3, demostrando cómo pasar de datos simulados en memoria a datos reales provenientes de una fuente externa.

---

## 🧾 Glosario rápido de conceptos usados

| Concepto | Definición breve |
|---|---|
| `if / elif / else` | Estructura condicional: ejecuta código según si una condición es verdadera o falsa. |
| `and` | Operador lógico: requiere que ambas condiciones sean verdaderas. |
| `match / case` | Estructura de comparación de patrones (alternativa moderna a múltiples `if/elif`). |
| `try / except` | Manejo de errores: evita que el programa se detenga ante una excepción. |
| `for` | Bucle que recorre una secuencia (lista, rango, etc.) un número definido de veces. |
| `while` | Bucle que se repite mientras una condición sea verdadera. |
| `range(inicio, fin, paso)` | Genera una secuencia de números; el `fin` no se incluye. |
| `break` | Corta la ejecución de un bucle inmediatamente. |
| `for...else` | El `else` de un `for` se ejecuta solo si el bucle terminó sin `break`. |
| `%` (módulo) | Devuelve el residuo de una división; útil para par/impar. |
| Bucle anidado | Un bucle dentro de otro (por ejemplo, para tablas de multiplicar o permutaciones). |
| `def` (función) | Bloque de código reutilizable que se define una vez y se ejecuta al ser llamado. |
| Lista (`[]`) | Colección ordenada y modificable de elementos. |
| Diccionario (`{}`) | Colección de pares clave-valor. |
| Comprensión de listas | Forma compacta de crear listas, ej.: `[f"Cliente {i}" for i in range(1,41)]`. |
| `random.choice()` / `random.uniform()` | Selección y generación de valores aleatorios. |
| `sorted(..., key=..., reverse=True)` | Ordena una colección según un criterio, de mayor a menor. |
| `pandas.DataFrame` | Estructura tabular para manejar datos (como una hoja de cálculo). |
| `matplotlib.pyplot` | Librería para crear gráficos y visualizaciones. |
| `plt.plot()` | Gráfico de líneas; muestra tendencias en el tiempo. |
| `plt.bar()` / `plt.barh()` | Gráfico de barras verticales/horizontales; compara magnitudes entre categorías. |
| `plt.scatter()` | Gráfico de dispersión; muestra correlación entre dos variables. |
| `plt.pie()` | Gráfico de pastel; muestra proporciones de un total. |
| `plt.hist()` | Histograma; muestra la distribución/frecuencia de datos agrupados en rangos. |
| `plt.subplots(filas, columnas)` | Crea una figura con varios gráficos organizados en cuadrícula. |
