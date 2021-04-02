# Mínimo

El capítulo anterior introdujo la función estándar Math.min que devuelve su
argumento más pequeño. Nosotros podemos construir algo como eso ahora.
Escribe una función min que tome dos argumentos y retorne su mínimo.

# Recursión

Hemos visto que % (el operador de residuo) se puede usar para probar si un
número es par o impar usando % 2 para ver si es divisible entre dos. Aquí hay
otra manera de definir si un número entero positivo es par o impar:
• Zero es par.
• Uno es impar.
• Para cualquier otro número N, su paridad es la misma que N - 2.
Define una función recursiva esPar que corresponda a esta descripción. La
función debe aceptar un solo parámetro (un número entero, positivo) y devolver
un Booleano. Pruébalo con 50 y 75. Observa cómo se comporta con -1. Por qué? Puedes
pensar en una forma de arreglar esto?

# Conteo de frijoles

Puedes obtener el N-ésimo carácter, o letra, de un string escribiendo "string"[
N]. El valor devuelto será un string que contiene solo un carácter (por ejemplo,
"f"). El primer carácter tiene posición cero, lo que hace que el último se
encuentre en la posición string.length - 1. En otras palabras, un string de
dos caracteres tiene una longitud de 2, y sus carácteres tendrán las posiciones
0 y 1.
Escribe una función contarFs que tome un string como su único argumento
y devuelva un número que indica cuántos caracteres “F” en mayúsculas haya
en el string.
Después, escribe una función llamada contarCaracteres que se comporte
como contarFs, excepto que toma un segundo argumento que indica el carácter
que debe ser contado (en lugar de contar solo caracteres “F” en mayúscula).
Reescribe contarFs para que haga uso de esta nueva función.
