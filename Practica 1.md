# Práctica 1: gestor de gastos de un estudiante (Java)

## 1. Datos generales

**Modalidad:** parejas  
**Duración estimada:** 3 horas  
**Herramientas:** Java, IntelliJ IDEA, Git y GitHub  
**Tipo de programa:** aplicación de consola  

**Restricción:** no crear clases adicionales, objetos personalizados, interfaces ni utilizar programación orientada a objetos más allá de la clase principal.

Pueden emplear:

* Variables y constantes.
* Métodos estáticos.
* Condicionales (`if`, `switch`).
* Ciclos (`for`, `while`, `do-while`).
* `ArrayList`.
* Entrada y salida de datos (`Scanner`).
* Métodos estándar de Java.

---

# 2. Propósito

Desarrollar colaborativamente un programa que permita registrar y consultar los gastos semanales de un estudiante, utilizando GitHub como repositorio compartido.

Al finalizar, cada integrante deberá demostrar que sabe:

1. Vincular IntelliJ IDEA con GitHub.
2. Clonar un repositorio.
3. Crear y cambiar de rama.
4. Identificar archivos modificados.
5. Crear commits descriptivos.
6. Enviar cambios mediante `push`.
7. Descargar e integrar cambios mediante `pull`.
8. Crear y revisar un Pull Request.
9. Fusionar ramas mediante `merge`.
10. Resolver un conflicto sencillo.

---

# 3. Funcionamiento del programa

El sistema mostrará el siguiente menú:

```text
GESTOR SEMANAL DE GASTOS

1. Registrar gasto
2. Mostrar todos los gastos
3. Calcular gasto total
4. Mostrar gasto mayor
5. Mostrar gastos por categoría
6. Mostrar resumen semanal
7. Salir

Seleccione una opción:
```

Cada gasto tendrá:

* Concepto
* Categoría
* Monto

Las categorías permitidas serán:

1. Alimentos
2. Transporte
3. Materiales escolares
4. Entretenimiento
5. Otros

Como todavía no se utilizarán clases propias, los datos se almacenarán en tres listas relacionadas.

```java
ArrayList<String> conceptos = new ArrayList<>();
ArrayList<String> categorias = new ArrayList<>();
ArrayList<Double> montos = new ArrayList<>();
```

El elemento ubicado en la posición `0` de cada lista corresponde al mismo gasto.

---

# 4. Organización de la pareja

| Integrante   | Rama              | Responsabilidad inicial           |
| ------------ | ----------------- | --------------------------------- |
| Estudiante A | `registro-gastos` | Registro y presentación de gastos |
| Estudiante B | `analisis-gastos` | Cálculos y consultas              |

Después intercambiarán funciones para revisar e integrar el trabajo del compañero.

---

# Desarrollo de la práctica

## Fase 1. Creación del repositorio

### Actividad del estudiante A

1. Crear un proyecto Java llamado

```text
GestorGastosJava
```

2. Crear un repositorio llamado

```text
gestor-gastos-java
```

3. Vincular IntelliJ IDEA con GitHub.

4. Agregar un archivo `.gitignore`.

5. Crear la clase principal:

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Gestor semanal de gastos");
    }

}
```

6. Realizar el primer commit.

```text
Inicializa proyecto Java del gestor de gastos
```

7. Ejecutar `push`.

8. Agregar como colaborador al estudiante B.

---

### Actividad del estudiante B

1. Aceptar la invitación.
2. Clonar el repositorio.
3. Ejecutar el programa.
4. Verificar que aparezca:

```text
Gestor semanal de gastos
```

---

## Evidencia

* URL del repositorio.
* Captura del primer commit.
* Captura del proyecto clonado.

---

# Fase 2. Creación de ramas

Ambos estudiantes deberán hacer primero un `pull`.

### Estudiante A

Crear la rama

```text
registro-gastos
```

### Estudiante B

Crear la rama

```text
analisis-gastos
```

Verificar que cada uno esté trabajando sobre su propia rama.

---

# Fase 3. Trabajo del estudiante A

Implementará el método

```java
public static void registrarGasto(
        ArrayList<String> conceptos,
        ArrayList<String> categorias,
        ArrayList<Double> montos,
        Scanner scanner)
```

El método deberá:

* Solicitar el concepto.
* Mostrar las categorías disponibles.
* Validar la categoría.
* Solicitar el monto.
* Rechazar montos menores o iguales a cero.
* Agregar la información a las tres listas.

También implementará

```java
public static void mostrarGastos(
        ArrayList<String> conceptos,
        ArrayList<String> categorias,
        ArrayList<Double> montos)
```

La salida deberá ser semejante a:

```text
GASTOS REGISTRADOS

1. Comida      | Alimentos  | $85.00
2. Autobús     | Transporte | $22.00
3. Cuaderno    | Materiales | $48.50
```

---

## Commits obligatorios

```text
Agrega método para registrar gastos
```

```text
Agrega listado de gastos registrados
```

Posteriormente realizará `push`.

---

# Fase 4. Trabajo del estudiante B

Implementará los métodos

```java
public static double calcularTotal(ArrayList<Double> montos)
```

```java
public static int obtenerPosicionGastoMayor(ArrayList<Double> montos)
```

```java
public static double calcularTotalPorCategoria(
        ArrayList<String> categorias,
        ArrayList<Double> montos,
        String categoriaBuscada)
```

Las funciones deberán:

* Utilizar ciclos.
* Considerar listas vacías.
* Evitar variables globales.
* Regresar resultados sin imprimir.

También implementará

```java
public static void mostrarResumen(
        ArrayList<String> conceptos,
        ArrayList<String> categorias,
        ArrayList<Double> montos)
```

Ejemplo:

```text
RESUMEN SEMANAL

Número de gastos: 4
Gasto total: $378.50
Promedio por gasto: $94.63
Gasto mayor: Libro de Java, $180.00
```

---

## Commits obligatorios

```text
Agrega cálculos de total y gasto mayor
```

```text
Agrega cálculo por categoría y resumen semanal
```

Después realizará `push`.

---

# Fase 5. Primer Pull Request

Se realiza exactamente igual que en la práctica original.

El estudiante A crea el Pull Request:

```text
registro-gastos → main
```

El estudiante B:

* revisa el código;
* realiza al menos un comentario;
* verifica la corrección;
* aprueba;
* realiza el `merge`.

---

# Fase 6. Actualización mediante Pull

El estudiante B deberá:

1. Cambiar a `main`.
2. Ejecutar `pull`.
3. Cambiar a `analisis-gastos`.
4. Integrar `main` mediante `merge`.
5. Corregir posibles errores.
6. Ejecutar `push`.

---

# Fase 7. Segundo Pull Request

El estudiante B crea

```text
analisis-gastos → main
```

El estudiante A comprobará al menos:

| Prueba                | Resultado esperado               |
| --------------------- | -------------------------------- |
| Lista vacía           | No debe producir errores         |
| Un gasto              | Debe identificarse como el mayor |
| Varios gastos         | El total debe ser correcto       |
| Categoría inexistente | Debe regresar 0.0                |
| Decimales             | Deben calcularse correctamente   |

Después de las observaciones:

* Corrección.
* Nuevo commit.
* `push`.
* Aprobación.
* `merge`.

---

# Fase 8. Conflicto intencional

Después de actualizar `main`, ambos crean nuevas ramas.

### Estudiante A

```text
titulo-estudiante-a
```

### Estudiante B

```text
titulo-estudiante-b
```

Ambos modifican exactamente la misma línea:

Estudiante A

```java
System.out.println("CONTROL PERSONAL DE GASTOS");
```

Estudiante B

```java
System.out.println("SISTEMA SEMANAL DE GASTOS");
```

Después del conflicto, acuerdan dejar:

```java
System.out.println("SISTEMA PERSONAL DE CONTROL DE GASTOS");
```

Commit:

```text
Resuelve conflicto en el título del programa
```

---

# Fase 9. Integración del programa

Una posible estructura del programa principal es:

```java
public static void main(String[] args) {

    Scanner scanner = new Scanner(System.in);

    ArrayList<String> conceptos = new ArrayList<>();
    ArrayList<String> categorias = new ArrayList<>();
    ArrayList<Double> montos = new ArrayList<>();

    int opcion;

    do {

        mostrarMenu();

        opcion = scanner.nextInt();
        scanner.nextLine();

        switch (opcion) {

            case 1:
                registrarGasto(conceptos, categorias, montos, scanner);
                break;

            case 2:
                mostrarGastos(conceptos, categorias, montos);
                break;

            case 3:
                System.out.println("Total: $" + calcularTotal(montos));
                break;

            case 4:
                mostrarGastoMayor(conceptos, categorias, montos);
                break;

            case 5:
                consultarGastosPorCategoria(categorias, montos, scanner);
                break;

            case 6:
                mostrarResumen(conceptos, categorias, montos);
                break;

            case 7:
                System.out.println("Programa terminado.");
                break;

            default:
                System.out.println("Opción no válida.");

        }

    } while (opcion != 7);

    scanner.close();
}
```

Esta estructura es una guía; la pareja deberá completar los métodos faltantes y validar adecuadamente la entrada del usuario.

---

# Entregables

Cada pareja entregará:

1. Enlace al repositorio de GitHub.
2. Proyecto ejecutable en `main`.
3. Historial con al menos ocho commits significativos.
4. Ramas creadas por ambos estudiantes.
5. Dos Pull Requests principales.
6. Comentarios de revisión realizados por ambos.
7. Evidencia del conflicto y su resolución.
8. Archivo `README.md` con:

```text
Nombre del proyecto
Integrantes
Responsabilidades de cada integrante
Instrucciones para ejecutar el programa
Métodos implementados
Conflicto encontrado y forma de resolverlo
Conclusión individual de cada integrante
```

---

# Evidencia individual

Cada estudiante responderá en el `README.md`:

* ¿Qué diferencia encontró entre `commit` y `push`?
* ¿Por qué debe hacerse `pull` antes de modificar archivos?
* ¿Para qué sirve trabajar en ramas?
* ¿Qué ocasionó el conflicto?
* ¿Cómo decidió qué código conservar?
* ¿Qué aportó personalmente al programa?

---

# Criterios de evaluación

| Criterio                                              | Porcentaje |
| ----------------------------------------------------- | ---------: |
| Funcionamiento del programa en Java                   |       30 % |
| Uso correcto de métodos, condiciones, ciclos y listas |       15 % |
| Organización mediante ramas                           |       10 % |
| Calidad y distribución de commits                     |       15 % |
| Uso de `push`, `pull` y `merge`                       |       10 % |
| Pull Requests y revisión del compañero                |       10 % |
| Resolución del conflicto                              |        5 % |
| README y reflexión individual                         |        5 % |
| **Total**                                             |  **100 %** |

## Condición de participación individual

Cada estudiante deberá aparecer como autor de:

* Al menos tres commits funcionales.
* Una rama propia.
* Un Pull Request.
* Una corrección derivada de una revisión.
* Al menos un comentario de revisión al compañero.

No se considerará participación suficiente limitarse a descargar el proyecto, observar el trabajo del compañero o realizar únicamente cambios de formato.
