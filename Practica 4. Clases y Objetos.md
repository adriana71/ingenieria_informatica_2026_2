# Práctica 4: Sistema orientado a objetos para monitoreo de un proceso de automatización  🛢️

## 1. Datos generales

**Modalidad:** parejas  
**Lenguaje:** Java  
**Herramientas:** IntelliJ IDEA, Git y GitHub  
**Tipo de programa:** aplicación de consola  
**Unidad:** 2. Clases y objetos

### Conceptos que se trabajarán

- Clases y objetos.
- Atributos.
- Métodos de instancia.
- Constructores.
- Encapsulación.
- Modificadores de acceso `private` y `public`.
- Métodos de consulta y modificación cuando sean necesarios.
- Relaciones sencillas entre objetos.
- UML básico.
- Trabajo colaborativo mediante Git y GitHub.

### Restricciones

En esta práctica **no se utilizarán todavía**:

- Herencia.
- Polimorfismo.
- Interfaces.
- Clases abstractas.
- Interfaz gráfica.
- Manejo de excepciones.
- Pruebas unitarias con JUnit.

Estos contenidos se trabajarán posteriormente.

---

# 2. Propósito

Diseñar e implementar colaborativamente un pequeño sistema orientado a objetos que represente elementos de un proceso automatizado.

En las prácticas anteriores se trabajó principalmente con variables, métodos, estructuras de control y arreglos o colecciones. En esta práctica se dará el paso hacia la **programación orientada a objetos**, de manera que la información y las operaciones relacionadas con un elemento del problema queden organizadas dentro de clases.

Al finalizar la práctica, cada integrante deberá demostrar que puede:

1. Identificar objetos a partir de la descripción de un problema.
2. Determinar las responsabilidades de cada objeto.
3. Identificar qué información debe conservar cada objeto.
4. Proponer comportamientos adecuados para cada clase.
5. Diseñar clases mediante un diagrama UML básico.
6. Implementar atributos, constructores y métodos.
7. Aplicar encapsulación.
8. Utilizar correctamente modificadores de acceso.
9. Crear y utilizar objetos desde Java.
10. Establecer relaciones sencillas entre objetos.
11. Documentar el proceso de análisis, diseño e implementación.
12. Mantener evidencia del trabajo individual y colaborativo mediante GitHub.

---

# 3. Problema

Una pequeña instalación industrial cuenta con varios **tanques de almacenamiento**.

Cada tanque dispone de un sensor que permite conocer su nivel actual. Se requiere desarrollar una aplicación de consola que represente los tanques y permita realizar una simulación sencilla de su operación.

Cada tanque tendrá inicialmente:

- un identificador;
- una capacidad máxima en litros;
- un nivel actual en litros;
- un estado de operación.

Los estados de operación considerados serán:

```text
DETENIDO
LLENANDO
VACIANDO
```

El sistema deberá permitir realizar operaciones como:

- consultar la información de un tanque;
- llenar un tanque;
- vaciar un tanque;
- detener su operación;
- consultar su nivel;
- consultar su porcentaje de llenado;
- consultar su estado;
- obtener una lectura mediante un sensor de nivel.

El sistema deberá respetar las siguientes reglas:

```text
nivelActual >= 0
nivelActual <= capacidadMaxima
```

Por lo tanto, un tanque no podrá contener una cantidad negativa ni superar su capacidad máxima.

Una posible salida del programa sería:

```text
TANQUE T-01

Capacidad: 1000 L
Nivel actual: 650 L
Porcentaje: 65 %
Estado: LLENANDO
```

> **Importante:** no comiencen programando inmediatamente. Antes deberán analizar el problema, identificar los objetos y diseñar las clases.

---

# 4. Organización de la pareja

| Integrante | Responsabilidad inicial |
| --- | --- |
| Estudiante A | Análisis compartido + implementación principal del modelo de tanque |
| Estudiante B | Análisis compartido + implementación principal del modelo de sensor |
| Ambos | UML, revisiones, integración, pruebas, documentación y conclusiones |

Aunque exista una responsabilidad inicial, ambos estudiantes deberán conocer el funcionamiento completo del proyecto y participar en las revisiones e integración.

---

# Desarrollo de la práctica

# Fase 1. Creación del repositorio y del documento de análisis

## Actividad del estudiante A

1. Crear en IntelliJ IDEA un proyecto Java llamado:

```text
SistemaMonitoreo
```

2. Compartir proyecto de IntelliJ IDEA en GitHub:

 
3. Crear la estructura inicial:
  

```text
sistema-monitoreo-java/
│
├── src/
│
├── docs/
│   └── 01-analisis-diseno.md
│
└── README.md
```

4. El archivo:

```text
docs/01-analisis-diseno.md
```

será el documento de trabajo obligatorio para las fases 1, 2 y 3.

5. Crear una clase principal mínima que permita verificar que el proyecto funciona.

Por ejemplo:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Sistema de monitoreo");
    }
}
```

6. Realizar el primer commit:

```text
Inicializa proyecto y documento de análisis
```

7. Ejecutar `push`.
  
8. Agregar como colaborador al estudiante B.
  

---

## Actividad del estudiante B

1. Aceptar la invitación al repositorio.
2. Clonar el repositorio desde IntelliJ IDEA.
3. Ejecutar el programa.
4. Verificar que el proyecto funcione correctamente.
5. Abrir el archivo:

```text
docs/01-analisis-diseno.md
```

6. Agregar en ese documento los nombres de los integrantes y la fecha de inicio de la práctica.
7. Realizar un commit identificable.
8. Ejecutar `push`.

### Evidencia de la fase 1

- URL del repositorio.
- Proyecto creado correctamente.
- Archivo `docs/01-analisis-diseno.md`.
- Primeros commits de ambos estudiantes.
- Proyecto clonado por el estudiante B.

---

# Fase 2. Análisis orientado a objetos

> **En esta fase todavía NO deberán crear las clases Java del sistema.**

Todo el análisis deberá registrarse en:

```text
docs/01-analisis-diseno.md
```

El documento deberá contener las siguientes secciones.

## 1. Descripción del problema

Expliquen con sus propias palabras:

- qué sistema se pretende representar;
- qué información necesita manejar;
- qué operaciones debe realizar;
- qué restricciones deben respetarse.

No copien únicamente el enunciado de la práctica. La intención es demostrar que comprendieron el problema.

---

## 2. Identificación de objetos

Respondan:

**¿Qué elementos del problema pueden representarse mediante objetos?**

Para cada objeto propuesto, expliquen brevemente:

- qué representa;
- por qué consideran que debe existir como objeto;
- qué responsabilidad tendría dentro del sistema.

---

## 3. Estado y comportamiento

Completen una tabla como la siguiente:

| Objeto propuesto | Responsabilidad | Información que debe conservar | Comportamientos que debe realizar |
| --- | --- | --- | --- |
| ... | ... | ... | ... |
| ... | ... | ... | ... |

### Importante

En esta fase deberán pensar en términos de **responsabilidades**.

Por ejemplo, en lugar de escribir:

```text
crear método getNivel()
```

es preferible escribir:

```text
El tanque debe permitir conocer su nivel actual.
```

La traducción de esas responsabilidades a atributos y métodos se realizará en la siguiente fase.

---

## 4. Relaciones entre los objetos

Expliquen:

- qué objetos necesitan colaborar entre sí;
- qué información necesita un objeto de otro;
- por qué consideran necesaria esa relación;
- qué responsabilidades no deberían duplicarse entre clases.

### Commits sugeridos

```text
Documenta análisis inicial del problema
```

```text
Identifica objetos y responsabilidades del sistema
```

```text
Documenta relaciones entre objetos
```

---

# Fase 3. Diseño orientado a objetos y UML

> **Esta fase también deberá completarse antes de comenzar la implementación de las clases.**

La pareja continuará trabajando en:

```text
docs/01-analisis-diseno.md
```

y agregará las siguientes secciones.

---

## 5. Diseño de clases

Transformen los objetos identificados en la fase anterior en una propuesta de clases.

Completen una tabla:

| Clase | Atributos propuestos | Tipo de dato | Métodos propuestos | Responsabilidad |
| --- | --- | --- | --- | --- |
| ... | ... | ... | ... | ... |

Para cada clase deberán analizar:

- qué atributos necesita;
- qué atributos deben ser `private`;
- qué información debe recibirse mediante el constructor;
- qué operaciones deberán implementarse mediante métodos;
- qué información debería poder consultarse desde otras clases;
- qué información no debería modificarse directamente desde el exterior.

---

## 6. Diagrama UML inicial

Elaboren un diagrama UML básico a partir de su propuesta.

Cada clase deberá mostrar:

```text
Nombre de la clase
-------------------------
atributos
-------------------------
constructor(es)
métodos
```

Utilicen la notación:

```text
- atributo privado
+ método público
```

Ejemplo de notación:

```text
-------------------------
        Ejemplo
-------------------------
- atributo1 : String
- atributo2 : double
-------------------------
+ Ejemplo(...)
+ metodo1() : void
+ metodo2() : double
-------------------------
```

Guarden el diagrama como:

```text
docs/uml-inicial.png
```

e insértenlo dentro de `01-analisis-diseno.md`:

```markdown
## 6. Diagrama UML inicial

![Diagrama UML inicial](uml-inicial.png)
```

---

## 7. Justificación del diseño

Respondan dentro del mismo documento:

1. ¿Por qué propusieron esas clases?
2. ¿Cuál es la responsabilidad principal de cada clase?
3. ¿Por qué determinados atributos fueron definidos como privados?
4. ¿Qué información decidieron proporcionar mediante los constructores?
5. ¿Qué objetos se relacionan entre sí y por qué?
6. ¿Qué decisiones tomaron para evitar duplicar responsabilidades?
7. ¿Qué parte del diseño fue discutida entre ambos integrantes y qué decisión tomaron?

---

## Punto de control obligatorio

> ## ⛔ NO INICIAR LA CODIFICACIÓN DE LAS CLASES TODAVÍA
> 
> Antes de continuar, el repositorio deberá contener:
> 
> - `docs/01-analisis-diseno.md` completo hasta la sección 7;
> - descripción del problema;
> - identificación de objetos;
> - tabla de responsabilidades;
> - análisis de relaciones;
> - propuesta de clases, atributos y métodos;
> - análisis de encapsulación;
> - `docs/uml-inicial.png`;
> - UML insertado en el documento;
> - justificación del diseño;
> - commits que permitan identificar la participación de ambos estudiantes.

El último commit de esta etapa deberá ser:

```text
Completa análisis y diseño UML previo a implementación
```

Solo después de este punto podrán comenzar a implementar las clases Java.

---

# Fase 4. Creación de ramas de implementación

Ambos estudiantes deberán ejecutar primero:

```text
pull
```

Posteriormente crearán sus ramas.

## Estudiante A

Crear la rama:

```text
modelo-tanque
```

## Estudiante B

Crear la rama:

```text
modelo-sensor
```

Cada estudiante deberá verificar en IntelliJ IDEA que está trabajando en su propia rama antes de comenzar a modificar el código.

---

# Fase 5. Trabajo del estudiante A: modelo de Tanque

El estudiante A implementará la clase que represente un tanque.

Deberá basarse en el diseño UML elaborado previamente por la pareja.

La clase deberá permitir, como mínimo:

- conservar un identificador;
- conservar la capacidad máxima;
- conservar el nivel actual;
- conservar el estado de operación;
- consultar sus datos;
- llenar el tanque;
- vaciar el tanque;
- detener la operación;
- calcular el porcentaje de llenado;
- impedir que el nivel sea menor que cero;
- impedir que el nivel supere la capacidad máxima.

### Encapsulación

Los atributos principales deberán estar protegidos.

Por lo tanto, desde `Main` no deberá realizarse una modificación directa como:

```java
tanque.nivelActual = 500;
```

Los cambios en el estado del objeto deberán realizarse mediante sus métodos.

### Commits obligatorios

Como mínimo:

```text
Implementa atributos y constructor de Tanque
```

```text
Agrega comportamiento de llenado y vaciado
```

```text
Agrega consulta y control de estado del tanque
```

Posteriormente realizará `push`.

---

# Fase 6. Trabajo del estudiante B: modelo de SensorNivel

El estudiante B implementará una clase que represente el sensor de nivel asociado al sistema.

Deberá basarse en el UML previamente acordado.

La clase deberá permitir, como mínimo:

- conservar un identificador;
- realizar una lectura;
- proporcionar el valor medido;
- indicar si la lectura se encuentra dentro de un intervalo válido.

La pareja deberá respetar la relación entre el sensor y el tanque propuesta en su diseño.

### Importante

No deberán duplicar innecesariamente información o responsabilidades que ya pertenezcan a otra clase.

### Commits obligatorios

Como mínimo:

```text
Implementa clase SensorNivel
```

```text
Agrega lectura y validación del sensor
```

Posteriormente realizará `push`.

---

# Fase 7. Primer Pull Request

El estudiante A creará el Pull Request:

```text
modelo-tanque → main
```

El estudiante B deberá revisar el código.

La revisión no deberá limitarse a verificar que el código compile.

Deberá comprobar:

- correspondencia entre UML y código;
- encapsulación;
- nombres de atributos;
- constructor;
- responsabilidades de los métodos;
- validación de límites;
- claridad del código.

El estudiante B deberá realizar **al menos un comentario técnico** dentro del Pull Request.

Después de la revisión:

1. El estudiante A realizará las correcciones necesarias.
2. Creará un nuevo commit.
3. Ejecutará `push`.
4. El estudiante B comprobará las correcciones.
5. Aprobará el Pull Request.
6. Se realizará `merge`.

---

# Fase 8. Actualización y segundo Pull Request

El estudiante B deberá:

1. Cambiar a `main`.
2. Ejecutar `pull`.
3. Cambiar a `modelo-sensor`.
4. Integrar los cambios de `main`.
5. Resolver posibles conflictos.
6. Ejecutar `push`.

Posteriormente creará:

```text
modelo-sensor → main
```

El estudiante A realizará la revisión.

Deberá comprobar especialmente:

- que `SensorNivel` tenga una responsabilidad claramente definida;
- que no duplique responsabilidades del tanque;
- que exista encapsulación;
- que la relación entre los objetos corresponda al diseño;
- que el código sea coherente con el UML.

El estudiante A deberá realizar al menos un comentario técnico.

Después de las correcciones se realizará el `merge`.

---

# Fase 9. Integración del sistema

Después de integrar ambas clases, uno de los integrantes creará una rama:

```text
integracion-sistema
```

En esta fase deberán crear objetos y demostrar su funcionamiento.

El programa deberá trabajar al menos con:

```text
Tanque T-01
Tanque T-02
Tanque T-03
```

Los objetos deberán tener diferentes capacidades y niveles iniciales.

La ejecución deberá demostrar al menos:

1. creación de objetos mediante constructores;
2. consulta del estado inicial;
3. llenado;
4. vaciado;
5. intento de superar la capacidad máxima;
6. intento de disminuir el nivel por debajo de cero;
7. lectura mediante un sensor;
8. cálculo del porcentaje de llenado;
9. cambio de estado de operación.

Una salida posible sería:

```text
=== SISTEMA DE MONITOREO ===

Tanque: T-01
Capacidad: 1000 L
Nivel: 650 L
Ocupación: 65 %
Estado: DETENIDO

Iniciando llenado...

Nuevo nivel: 800 L
Estado: LLENANDO

Sensor SN-01
Lectura: 800 L

Deteniendo tanque...

Estado final: DETENIDO
```

La salida anterior es orientativa. Pueden diseñar otra presentación siempre que permita demostrar claramente el comportamiento de los objetos.

---

# Fase 10. Pruebas obligatorias

La pareja deberá comprobar y documentar como mínimo los siguientes casos:

| Caso | Resultado esperado |
| --- | --- |
| Crear tanque con datos válidos | El objeto conserva correctamente su estado |
| Llenar tanque | Aumenta su nivel |
| Intentar superar la capacidad | El nivel nunca supera la capacidad máxima |
| Vaciar tanque | Disminuye su nivel |
| Intentar obtener un nivel negativo | El nivel nunca es menor que cero |
| Consultar porcentaje | Se calcula correctamente |
| Cambiar el estado de operación | El estado refleja la operación realizada |
| Detener tanque | El estado cambia a `DETENIDO` |
| Consultar sensor | Proporciona una lectura coherente |

Las pruebas podrán realizarse mediante una clase Java destinada a ejecutar diferentes escenarios.

**No es necesario utilizar JUnit en esta práctica.**

---

# Fase 11. Actualización del UML

Después de finalizar la implementación deberán comparar:

```text
UML inicial
vs.
implementación final
```

Si durante la programación cambiaron:

- atributos;
- tipos de datos;
- métodos;
- constructores;
- responsabilidades;
- relaciones entre objetos;

deberán actualizar el diagrama.

Guarden la versión final como:

```text
docs/uml-final.png
```

Agreguen en `docs/01-analisis-diseno.md` una nueva sección:

```markdown
## 8. Cambios realizados al diseño

Explicar qué cambió entre el UML inicial y el UML final y por qué.
```

Incluyan también:

```markdown
## 9. Diagrama UML final

![Diagrama UML final](uml-final.png)
```

Commit obligatorio:

```text
Actualiza UML de acuerdo con implementación final
```

---

# Fase 12. Documentación final

El archivo `README.md` deberá contener como mínimo:

```text
Nombre del proyecto
Integrantes
Descripción breve del sistema
Clases implementadas
Responsabilidades de cada clase
Instrucciones para ejecutar el programa
Pruebas realizadas
Responsabilidades de cada integrante
Enlace al documento de análisis y diseño
Conclusiones individuales
```

El `README.md` deberá enlazar el documento:

```text
docs/01-analisis-diseno.md
```

---

# Entregables

Cada pareja entregará:

1. Enlace al repositorio de GitHub.
2. Proyecto Java ejecutable desde `main`.
3. Archivo `docs/01-analisis-diseno.md`.
4. Análisis inicial de objetos y responsabilidades.
5. Diseño de clases.
6. `docs/uml-inicial.png`.
7. `docs/uml-final.png`.
8. Implementación de las clases.
9. Evidencia de encapsulación.
10. Historial de commits significativos.
11. Ramas de trabajo de ambos estudiantes.
12. Dos Pull Requests principales.
13. Comentarios de revisión realizados por ambos estudiantes.
14. Evidencia de las pruebas realizadas.
15. `README.md` actualizado.
16. Evidencia de contribuciones individuales.

---

# Evidencia individual

Cada estudiante responderá en el `README.md`, identificando claramente su nombre:

1. ¿Qué diferencia existe entre una clase y un objeto?
2. Mencione tres objetos creados durante la ejecución del programa.
3. ¿Por qué los atributos principales fueron declarados `private`?
4. ¿Qué responsabilidad tiene la clase que representa al tanque?
5. ¿Qué responsabilidad tiene la clase que representa al sensor?
6. ¿Qué cambio realizaron al UML después de implementar el programa?
7. ¿Qué observación técnica realizó durante el Pull Request de su compañero?
8. ¿Qué corrección realizó a partir de una observación recibida?
9. ¿Qué aportó personalmente al proyecto?
10. ¿Qué decisión de diseño le pareció más importante y por qué?

---

# Criterios de evaluación

| Criterio | Porcentaje |
| --- | --- |
| Modelo de clases | 30 % |
| Implementación orientada a objetos | 30 % |
| Aplicación a automatización | 20 % |
| Pruebas y repositorio | 20 % |
| **Total** | **100 %** |

## Modelo de clases — 30 %

El UML representa clases, atributos, métodos, relaciones y responsabilidades coherentes.

Se considerará también:

- calidad del análisis previo;
- correspondencia entre problema, responsabilidades y clases;
- claridad del UML;
- justificación de las decisiones de diseño;
- actualización del modelo después de la implementación.

## Implementación orientada a objetos — 30 %

Se evaluará que:

- existan objetos creados mediante constructores;
- los atributos estén adecuadamente encapsulados;
- se utilicen correctamente modificadores de acceso;
- los métodos representen comportamientos coherentes;
- cada clase conserve responsabilidades claramente definidas;
- el código corresponda razonablemente con el diseño propuesto.

## Aplicación a automatización — 20 %

El modelo deberá representar de manera pertinente elementos de un sistema automatizado y sus comportamientos.

Se evaluará especialmente:

- representación del tanque;
- representación del sensor;
- coherencia de estados y operaciones;
- respeto de restricciones del proceso.

## Pruebas y repositorio — 20 %

Se evaluará:

- funcionamiento demostrable;
- casos de prueba documentados;
- README actualizado;
- archivo de análisis y diseño;
- commits significativos;
- uso de ramas;
- Pull Requests;
- revisiones entre compañeros;
- trazabilidad del proceso;
- contribución individual verificable.

---

# Condición de participación individual

Cada estudiante deberá aparecer como autor de:

- al menos tres commits funcionales o de diseño significativos;
- una rama propia;
- al menos un Pull Request o una participación claramente verificable en la integración;
- al menos una corrección derivada de una revisión;
- al menos un comentario técnico de revisión al compañero;
- aportaciones identificables al análisis y diseño.

No se considerará participación suficiente:

- limitarse a descargar o clonar el repositorio;
- observar el trabajo del compañero;
- realizar únicamente cambios de formato;
- subir archivos elaborados completamente por otra persona;
- aparecer únicamente en el documento final sin evidencia en el historial del repositorio.

---

# Regla importante sobre el proceso

El análisis y diseño no son actividades posteriores para justificar código ya terminado.

Por ello:

> **El archivo `docs/01-analisis-diseno.md` y el UML inicial deberán existir en el historial del repositorio antes de la implementación de las clases.**

Las correcciones realizadas después de recibir retroalimentación deberán conservarse mediante nuevos commits, sin eliminar la trazabilidad del proceso.
