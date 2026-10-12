# Tarea 3 · La factura bajo el microscopio
Pareja: Irene, Adam y Angela Colorado Sousa · GitHub: adammurga013, Irenegmez04 y ACS-cd 

## Reto 1 · Compilar desde la terminal
- Comando usado y resultado. javac factura.java , no compila. dir para detectar los archivos creados.
- ¿Qué es Factura.java? ¿Y Factura.class? ¿Quién ejecuta el .class? Factura.java es un archivo java. Es una clase dentro de java (bytecode). La máquina virtual de Java,
- ¿Por qué no se ha generado Factura.class la primera vez? El archivo no puede compilar y por ello no puede crear un .java en automático.

## Reto 2 · Errores de compilación
| Nº | Línea | Mensaje de javac | Tipo (léxico / sintaxis / semántica) | Corrección |
|----|-------|------------------|--------------------------------------|------------|
| 1  | 3     | The public type Factura must be defined in its own file | Sintaxis / Estructural | Renombrar el archivo de `factura.java` a `Factura.java` para que coincida con el nombre de la clase pública. |
| 2  | 15    | Invalid Character (carácter no válido `#`) | Léxico | Eliminar el símbolo `#` en la declaración de la variable precio (`double precio = sc.nextDouble();`). |
| 3  | 29    | Type mismatch: cannot convert from double to int | Semántica | Cambiar el tipo de la variable `int total` a `double total` para que admita números decimales. |
Captura del programa funcionando: capturas/reto2.png

## Reto 3 · Depuración del error lógico
| Variable | Valor esperado | Valor real |
|----------|----------------|------------|
| descuento | 18,00 €        | 6,00 €     |
| total     | 123,42 €       | 137,94 €   |
- Línea del error y explicación: Líneas 23-28. El error lógico ocurre porque el segundo `if` (`if (socio.equals("s"))`) sobrescribe el valor de la variable `descuento` (calculando solo el 5% = 6 €) en lugar de acumularlo con el 10% anterior (que era de 12 €), perdiendo el descuento por volumen.
- Corrección: Acumular el descuento en lugar de reasignarlo: `descuento += base * 0.05;` (o sumar ambos condicionales).
- Mi propia prueba (producto, precio, cantidad, socio → total): Camiseta, 60, 2, s → 123,42 €
Captura del depurador: capturas/reto3.png

## Reto 4 · Reutilización
- Métodos creados y para qué sirve cada uno:
    ·calcularDescuento: recibe la base imponible y si el cliente es socio. Aplica un 10% de descuento si la base supera 100€ y suma un 5% más si es socio. Devuelve el descuento total.
    ·aplicarIVA: recibe un importe y lo devuelve con el IVA (21%) aplicado, usando la constante IVA.
    ·pedirDecimal: muestra el mensaje por pantalla y devuelve el número decimal que escribe el usuario, para no repetir print + nextDouble.
- ¿Qué ventaja tiene frente al código anterior?
    ·Reutilización: los cálculos se pueden llamar desde cualquier parte del programa sin copiar código.
    ·Mantenimiento: si cambian las reglas del desucneto o el IVA, solo se modifica un método.
    ·Pruebas y depuración: cada método se puede comprobar por separado.

## Reto 5 · ¿Qué lenguaje elegirías?
- Caso A (web de la tienda):
- Caso B (propuesta en ensamblador):