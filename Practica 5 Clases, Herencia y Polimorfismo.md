# Práctica 5: Herencia y polimorfismo — Sistema de invernadero inteligente 🌱

## 1. Datos generales

**Modalidad:** individual  
**Lenguaje:** Java  
**Herramientas:** IntelliJ IDEA, Git y GitHub  
**Tipo de programa:** aplicación de consola  
**Unidad:** 2. Clases y objetos

### Conceptos que se trabajarán

- Clases y objetos.
- Atributos y métodos de instancia.
- Constructores.
- Encapsulación.
- Modificadores de acceso `private` y `public`.
- Herencia.
- Superclases y subclases.
- Uso de `super`.
- Sobrescritura de métodos.
- Uso de `@Override`.
- Polimorfismo.
- Enlace dinámico (*dynamic binding*).
- Conversión de tipos de objetos (*casting*).
- Operador `instanceof`.
- Relaciones entre objetos.
- UML.
- Git y GitHub para documentar el proceso de desarrollo.

### Restricciones

En esta práctica no será necesario utilizar:

- interfaces;
- clases abstractas;
- interfaz gráfica;
- conexión con sensores físicos;
- Arduino o microcontroladores;
- manejo de excepciones;
- pruebas unitarias con JUnit.

Estos elementos podrán estudiarse o incorporarse posteriormente.

---

# 2. Propósito

Diseñar e implementar individualmente un pequeño sistema orientado a objetos que represente elementos de un **invernadero inteligente**, utilizando herencia y polimorfismo para organizar clases relacionadas.

En la Práctica 4 trabajaste con clases, objetos, atributos, métodos, constructores, encapsulación y relaciones sencillas entre objetos.

En esta práctica avanzarás hacia un nuevo problema:

> ¿Qué sucede cuando varias clases representan objetos diferentes, pero comparten características y comportamientos?

A partir de esta pregunta trabajarás con **generalización y especialización**, de manera que puedas identificar características comunes, definir una superclase y crear clases especializadas mediante herencia.

Al finalizar la práctica deberás demostrar que puedes:

1. identificar características y comportamientos comunes entre diferentes clases;
2. reconocer relaciones de generalización y especialización;
3. diseñar una jerarquía de clases;
4. implementar superclases y subclases;
5. utilizar `super` en los constructores;
6. sobrescribir métodos mediante `@Override`;
7. utilizar referencias de la superclase para trabajar con objetos de diferentes subclases;
8. aplicar polimorfismo;
9. explicar y demostrar el enlace dinámico;
10. utilizar `instanceof` y casting cuando sean necesarios;
11. distinguir entre herencia y otras relaciones entre objetos;
12. actualizar un modelo UML después de la implementación;
13. documentar mediante Git y GitHub la evolución del análisis, diseño e implementación.

---

# 3. Problema

Desarrollarás una aplicación de consola que represente de manera simplificada un **sistema de invernadero inteligente**.

Antes de comenzar deberás leer:

```text
Contexto_Invernadero_Inteligente.md
```

En ese documento encontrarás la información necesaria para comprender:

- qué es un invernadero inteligente;
- qué función cumplen los sensores;
- qué variables se observarán;
- cómo se interpretarán las mediciones;
- qué función tendrá el sistema de riego.

No necesitas investigar electrónica, agricultura, Arduino ni funcionamiento físico de sensores.

Para esta práctica se considerarán al menos:

- temperatura del aire;
- humedad ambiental;
- humedad del suelo;
- sistema de riego.

Las mediciones serán simuladas desde el programa.

> **Importante:** el documento de contexto describe el sistema que deberás representar, pero no define las clases que debes implementar. Parte de la práctica consiste precisamente en analizar el problema y proponer el modelo orientado a objetos.

> **Importante:** no comiences programando inmediatamente. Primero deberás analizar el problema, identificar los objetos, estudiar sus relaciones y elaborar un diseño UML inicial.

---

# Desarrollo de la práctica

# Fase 1. Creación del repositorio y análisis orientado a objetos

En esta fase crearás el proyecto y comenzarás el documento que utilizarás para registrar tu proceso de análisis y diseño.

## 1. Creación del proyecto

Crea en IntelliJ IDEA un proyecto Java llamado:

```text
SistemaInvernadero
```

Crea un repositorio en GitHub y publica el proyecto.

La estructura inicial deberá ser semejante a:

```text
sistema-invernadero-java/
│
├── src/
│
├── docs/
│   └── 01-analisis-diseno.md
│
└── README.md
```

El archivo:

```text
docs/01-analisis-diseno.md
```

será tu documento de trabajo durante toda la práctica.

Crea también una clase principal mínima que permita comprobar que el proyecto funciona.

Por ejemplo:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Sistema de invernadero inteligente");
    }
}
```

Realiza `commit` y `push`.

### Commit obligatorio

```text
Inicializa proyecto y documento de análisis
```

---

## 2. Descripción del problema

Lee `Contexto_Invernadero_Inteligente.md`.

Después explica con tus propias palabras en `01-analisis-diseno.md`:

- qué sistema vas a representar;
- qué información necesita manejar;
- qué elementos intervienen;
- qué operaciones generales deberá realizar.

No copies únicamente el documento de contexto.

La intención es demostrar que **comprendiste el problema antes de comenzar a diseñar las clases**.

---

## 3. Identificación de objetos

Responde:

> ¿Qué elementos del problema pueden representarse mediante objetos?

Para cada objeto propuesto explica:

- qué representa;
- por qué consideras que debe existir como objeto;
- qué responsabilidad tendría dentro del sistema.

---

## 4. Estado y comportamiento

Completa una tabla como la siguiente:

| Objeto propuesto | Responsabilidad | Información que debe conservar | Comportamientos que debe realizar |
|---|---|---|---|
| ... | ... | ... | ... |
| ... | ... | ... | ... |

### Importante

En este momento piensa en términos de **responsabilidades**, no todavía en nombres exactos de atributos y métodos.

Por ejemplo, en lugar de escribir:

```text
crear método getMedicion()
```

es preferible escribir:

```text
El sensor debe permitir conocer su última medición.
```

La traducción de estas responsabilidades a atributos y métodos se realizará posteriormente.

---

## 5. Características comunes y especialización

Compara los diferentes sensores descritos en el documento de contexto.

Responde:

1. ¿Qué información tienen en común?
2. ¿Qué comportamientos tienen en común?
3. ¿Qué características cambian dependiendo del tipo de sensor?
4. ¿Existe un concepto general que permita representar a todos los sensores?
5. ¿Qué elementos podrían representar especializaciones de ese concepto?

---

## 6. Relaciones entre objetos

Analiza las relaciones existentes.

Distingue especialmente entre:

```text
ES UN
```

y

```text
TIENE / UTILIZA UN
```

Por ejemplo:

```text
Un sensor de temperatura ES UN sensor.
```

Esto podría indicar una relación de generalización/especialización.

En cambio:

```text
Un sistema utiliza información de sensores.
```

no significa necesariamente que ambos objetos deban pertenecer a la misma jerarquía.

Explica:

- qué objetos necesitan colaborar;
- qué información necesita un objeto de otro;
- cuáles relaciones podrían representarse mediante herencia;
- cuáles no deberían representarse mediante herencia;
- qué responsabilidades no deberían duplicarse.

Responde también:

> ¿Por qué `SistemaRiego` no debería ser una subclase de `Sensor`?

### Commits sugeridos

```text
Documenta análisis inicial del problema
```

```text
Identifica objetos y responsabilidades del sistema
```

```text
Documenta relaciones y posibles especializaciones
```

### Evidencia de la fase 1

Al finalizar esta fase tu repositorio deberá contener:

- proyecto Java funcional;
- `README.md`;
- `docs/01-analisis-diseno.md`;
- descripción del problema;
- identificación de objetos;
- tabla de estado y comportamiento;
- análisis de características comunes;
- análisis de relaciones;
- commits correspondientes al análisis.

---

# Fase 2. Diseño orientado a objetos y UML

> En esta fase todavía **NO deberás implementar las clases definitivas del sistema**.

Continúa trabajando en:

```text
docs/01-analisis-diseno.md
```

## 1. Diseño de clases

Transforma los objetos y responsabilidades identificados anteriormente en una propuesta de clases.

Completa una tabla:

| Clase | Atributos propuestos | Tipo de dato | Métodos propuestos | Responsabilidad |
|---|---|---|---|---|
| ... | ... | ... | ... | ... |

Para cada clase analiza:

- qué atributos necesita;
- qué atributos deben ser `private`;
- qué información debe recibirse mediante el constructor;
- qué operaciones deben implementarse mediante métodos;
- qué información debería poder consultarse desde otras clases;
- qué elementos pertenecen a una clase general;
- qué elementos pertenecen solamente a clases especializadas.

---

## 2. Jerarquía de clases

Tu modelo deberá permitir representar como mínimo:

- un concepto general de sensor;
- sensor de temperatura;
- sensor de humedad ambiental;
- sensor de humedad del suelo;
- sistema de riego.

Analiza qué clases forman parte de una misma jerarquía y cuáles solamente colaboran entre sí.

No dupliques en las clases especializadas información que pueda pertenecer razonablemente a una clase general.

---

## 3. Diagrama UML inicial

Elabora un diagrama UML a partir de tu propuesta.

Cada clase deberá mostrar:

```text
Nombre de la clase
-------------------------
atributos
-------------------------
constructor(es)
métodos
```

Utiliza la notación:

```text
- atributo privado
+ método público
```

Representa también correctamente las relaciones de herencia.

Guarda el diagrama como:

```text
docs/uml-inicial.png
```

e insértalo dentro de `01-analisis-diseno.md`:

```markdown
## Diagrama UML inicial

![Diagrama UML inicial](uml-inicial.png)
```

---

## 4. Justificación del diseño

Responde dentro del mismo documento:

1. ¿Por qué propusiste esas clases?
2. ¿Cuál es la responsabilidad principal de cada una?
3. ¿Por qué determinados atributos serán `private`?
4. ¿Qué información proporcionarás mediante los constructores?
5. ¿Cuál será la superclase?
6. ¿Qué clases serán subclases?
7. ¿Por qué existe una relación “es un” entre ellas?
8. ¿Qué información o comportamiento decidiste colocar en la superclase?
9. ¿Qué elementos permanecerán en las subclases?
10. ¿Por qué `SistemaRiego` no pertenece a la jerarquía de sensores?
11. ¿Qué decisiones tomaste para evitar duplicar responsabilidades?

---

## Punto de control obligatorio

> ## ⛔ NO INICIES LA CODIFICACIÓN DE LAS CLASES TODAVÍA
>
> Antes de continuar, tu repositorio deberá contener:
>
> - `docs/01-analisis-diseno.md` con el análisis completo;
> - descripción del problema;
> - identificación de objetos;
> - tabla de responsabilidades;
> - análisis de relaciones;
> - análisis de generalización y especialización;
> - propuesta de clases, atributos y métodos;
> - análisis de encapsulación;
> - `docs/uml-inicial.png`;
> - UML insertado en el documento;
> - justificación del diseño.

El último commit de esta etapa deberá ser:

```text
Completa análisis y diseño UML previo a implementación
```

Solo después de este punto deberás comenzar a implementar las clases.

---

# Fase 3. Implementación de la jerarquía y sobrescritura

Implementa ahora las clases definidas en tu UML.

Tu código deberá basarse en el diseño realizado previamente. Si durante la implementación descubres que necesitas modificar el diseño, podrás hacerlo, pero deberás documentar posteriormente esos cambios.

## 1. Implementación de la superclase

Implementa la clase general que representa a los sensores.

Deberá conservar la información común identificada durante tu análisis.

Como mínimo deberá permitir representar:

- identificación;
- ubicación;
- estado;
- última medición.

Deberás aplicar encapsulación.

Los atributos principales no deberán modificarse directamente desde `Main`.

Por ejemplo, evita instrucciones como:

```java
sensor.ultimaMedicion = 25;
```

Los cambios deberán realizarse mediante comportamientos definidos por los objetos.

---

## 2. Implementación de las subclases

Implementa al menos las especializaciones necesarias para representar:

```text
SensorTemperatura
SensorHumedad
SensorHumedadSuelo
```

Cada una deberá heredar de la clase general.

No vuelvas a declarar innecesariamente atributos que ya pertenecen a la superclase.

Cada subclase deberá incorporar al menos una característica o comportamiento que tenga sentido para ese tipo particular de sensor.

---

## 3. Constructores y `super`

Implementa constructores adecuados.

Los constructores de las subclases deberán utilizar `super(...)` para inicializar la parte del objeto correspondiente a la superclase.

Documenta en `01-analisis-diseno.md`:

1. ¿Los constructores de la superclase se heredan?
2. Cuando creas un objeto de una subclase, ¿qué constructor se ejecuta primero?
3. ¿Para qué utilizaste `super(...)`?

---

## 4. Sobrescritura

Define en la superclase un comportamiento relacionado con la interpretación de una medición.

Cada tipo de sensor deberá proporcionar su propia implementación.

Utiliza:

```java
@Override
```

Los criterios para interpretar las mediciones se encuentran en `Contexto_Invernadero_Inteligente.md`.

Comprueba que el mismo comportamiento produzca resultados apropiados dependiendo del tipo de sensor.

---

## 5. Reflexión sobre la sobrescritura

Responde en `01-analisis-diseno.md`:

1. ¿Qué método sobrescribiste?
2. ¿Qué indica `@Override`?
3. ¿Por qué utilizaste el mismo nombre de método en las diferentes subclases?
4. ¿Qué ventaja tiene esto frente a crear un método completamente diferente para cada tipo de sensor?

### Commits obligatorios

Como mínimo:

```text
Implementa superclase y encapsulación de Sensor
```

```text
Implementa subclases de sensores y constructores
```

```text
Agrega sobrescritura del comportamiento de medición
```

Posteriormente realiza `push`.

### Evidencia de la fase 3

- Superclase implementada.
- Subclases implementadas.
- Encapsulación.
- Constructores.
- Uso de `super`.
- Sobrescritura.
- Uso de `@Override`.
- Reflexiones documentadas.
- Commits significativos.

---

# Fase 4. Polimorfismo y enlace dinámico

En esta fase utilizarás la jerarquía de clases para trabajar con diferentes objetos mediante un tipo común.

## 1. Colección de sensores

Crea una colección capaz de almacenar objetos de diferentes subclases utilizando el tipo de la superclase.

Por ejemplo:

```java
Sensor[] sensores;
```

o alguna colección equivalente.

Deberás almacenar objetos de diferentes tipos.

Conceptualmente:

```java
Sensor sensor1 = new SensorTemperatura(...);
Sensor sensor2 = new SensorHumedad(...);
Sensor sensor3 = new SensorHumedadSuelo(...);
```

Observa la diferencia entre:

```text
tipo de la referencia
```

y:

```text
tipo real del objeto
```

---

## 2. Procesamiento polimórfico

Recorre la colección y ejecuta el método sobrescrito para cada objeto.

Por ejemplo:

```java
for (Sensor sensor : sensores) {
    sensor.evaluarMedicion();
}
```

No utilices una cadena de `if/else` para decidir manualmente qué método de evaluación debe ejecutarse.

---

## 3. Enlace dinámico

Registra en `01-analisis-diseno.md`:

| Tipo de referencia | Tipo real del objeto | Método que se ejecuta |
|---|---|---|
| `Sensor` | `SensorTemperatura` | ... |
| `Sensor` | `SensorHumedad` | ... |
| `Sensor` | `SensorHumedadSuelo` | ... |

Después explica con tus propias palabras:

1. ¿Por qué una referencia de tipo `Sensor` puede apuntar a un objeto `SensorTemperatura`?
2. ¿Puede una referencia `SensorTemperatura` apuntar directamente a cualquier objeto `Sensor`?
3. Cuando ejecutas `sensor.evaluarMedicion()`, ¿qué versión del método se ejecuta?
4. ¿Cómo determina Java cuál implementación utilizar?
5. ¿Dónde puedes observar el polimorfismo?
6. ¿Dónde puedes observar el enlace dinámico?

No copies únicamente definiciones. Relaciona tus respuestas con **tu propio código**.

### Commits obligatorios

```text
Agrega colección polimórfica de sensores
```

```text
Demuestra polimorfismo y enlace dinámico
```

### Evidencia de la fase 4

- Colección con diferentes tipos de sensores.
- Referencias de tipo `Sensor`.
- Ejecución polimórfica.
- Evidencia del enlace dinámico.
- Tabla y explicación en `01-analisis-diseno.md`.
- Commits correspondientes.

---

# Fase 5. `instanceof`, casting e integración del sistema

En esta fase analizarás situaciones en las que necesitas acceder a características específicas de una subclase y posteriormente integrarás el sistema de riego.

## 1. Comportamiento específico

Agrega al menos un comportamiento que tenga sentido únicamente para una de las subclases.

No agregues ese comportamiento a la superclase únicamente para poder acceder a él.

---

## 2. Uso de `instanceof`

Trabaja con una referencia de tipo `Sensor` y comprueba el tipo real del objeto mediante:

```java
instanceof
```

Por ejemplo:

```java
if (sensor instanceof SensorTemperatura) {
    // ...
}
```

---

## 3. Casting

Después de comprobar el tipo, realiza el casting necesario para acceder al comportamiento específico.

Por ejemplo:

```java
SensorTemperatura temperatura =
        (SensorTemperatura) sensor;
```

Utiliza posteriormente el método específico que diseñaste.

---

## 4. Análisis

Documenta en `01-analisis-diseno.md`:

1. ¿Por qué fue necesario realizar el casting?
2. ¿Qué comprueba `instanceof`?
3. ¿Qué podría ocurrir si intentaras convertir un objeto a una subclase incorrecta?
4. ¿Por qué no debes utilizar `instanceof` para sustituir innecesariamente el polimorfismo?

---

## 5. Sistema de riego

Implementa la clase que represente el sistema de riego.

Como mínimo deberá permitir:

- activar el riego;
- desactivar el riego;
- consultar su estado.

Integra posteriormente esta clase con el resto del sistema.

Tu programa deberá demostrar al menos una situación en la que la medición de humedad del suelo pueda utilizarse para decidir si el riego debe activarse o permanecer inactivo.

No necesitas implementar un controlador automático complejo.

Lo importante es demostrar que los objetos **colaboran sin confundir sus responsabilidades**.

Responde:

> ¿El sistema de riego “es un” sensor o utiliza información proporcionada por los sensores?

Explica cómo representaste esta relación en el código y en el UML.

### Commits obligatorios

```text
Agrega uso justificado de instanceof y casting
```

```text
Implementa e integra sistema de riego
```

### Evidencia de la fase 5

- Comportamiento específico de una subclase.
- Uso de `instanceof`.
- Casting.
- Sistema de riego.
- Integración entre objetos.
- Análisis documentado.
- Commits correspondientes.

---

# Fase 6. Integración, pruebas, actualización del UML y documentación

En esta fase demostrarás el funcionamiento completo del sistema y compararás el diseño inicial con la implementación final.

## 1. Integración del sistema

El programa deberá trabajar al menos con:

```text
1 SensorTemperatura
1 SensorHumedad
1 SensorHumedadSuelo
1 SistemaRiego
```

La ejecución deberá demostrar:

1. creación de objetos mediante constructores;
2. consulta de información;
3. métodos heredados;
4. métodos sobrescritos;
5. uso de `super`;
6. diferentes subclases almacenadas mediante referencias `Sensor`;
7. procesamiento polimórfico;
8. enlace dinámico;
9. uso justificado de `instanceof`;
10. casting;
11. activación o desactivación del sistema de riego.

La salida del programa puede diseñarse libremente siempre que permita observar claramente estos comportamientos.

---

## 2. Pruebas obligatorias

Comprueba y documenta como mínimo:

| Caso | Resultado esperado |
|---|---|
| Crear los diferentes sensores | Los objetos conservan correctamente su estado |
| Evaluar temperatura baja, adecuada y alta | Se obtiene la interpretación correspondiente |
| Evaluar humedad ambiental baja, adecuada y alta | Se obtiene la interpretación correspondiente |
| Evaluar humedad del suelo baja, adecuada y alta | Se obtiene la interpretación correspondiente |
| Procesar distintos sensores mediante referencias `Sensor` | Cada objeto ejecuta su propia implementación |
| Recorrer la colección de sensores | Todos los objetos pueden procesarse mediante el tipo común |
| Comprobar un objeto mediante `instanceof` | Se identifica correctamente su tipo |
| Realizar casting después de comprobar el tipo | Es posible utilizar el comportamiento específico |
| Humedad del suelo baja | El sistema permite activar el riego |
| Humedad del suelo adecuada o alta | El riego puede permanecer o pasar a inactivo |

Las pruebas podrán realizarse mediante una clase Java destinada a ejecutar diferentes escenarios.

No es necesario utilizar JUnit.

---

## 3. Actualización del UML

Compara:

```text
UML inicial
vs.
implementación final
```

Si durante la programación cambiaste:

- atributos;
- tipos de datos;
- métodos;
- constructores;
- responsabilidades;
- relaciones;
- jerarquía de clases;

actualiza el diagrama.

Guarda la versión final como:

```text
docs/uml-final.png
```

Agrega a `docs/01-analisis-diseno.md`:

```markdown
## Cambios realizados al diseño
```

Explica qué cambió entre el UML inicial y el final y por qué.

Incluye también:

```markdown
## Diagrama UML final

![Diagrama UML final](uml-final.png)
```

### Commit obligatorio

```text
Actualiza UML de acuerdo con implementación final
```

---

## 4. Documentación final

El archivo `README.md` deberá contener como mínimo:

```text
Nombre del proyecto
Descripción breve del sistema
Clases implementadas
Responsabilidad de cada clase
Instrucciones para ejecutar el programa
Conceptos de POO aplicados
Pruebas realizadas
Enlace al documento de análisis y diseño
Conclusión
```

En **Conceptos de POO aplicados** identifica en tu propio programa dónde utilizaste:

- encapsulación;
- herencia;
- `super`;
- sobrescritura;
- polimorfismo;
- enlace dinámico;
- `instanceof`;
- casting.

No escribas únicamente las definiciones.

Explica **dónde pueden observarse en tu implementación**.

### Commit obligatorio

```text
Completa pruebas y documentación final
```

---

# Entregables

Deberás entregar:

1. enlace al repositorio de GitHub;
2. proyecto Java ejecutable desde `main`;
3. `docs/01-analisis-diseno.md`;
4. análisis inicial de objetos y responsabilidades;
5. análisis de generalización y especialización;
6. diseño de clases;
7. `docs/uml-inicial.png`;
8. `docs/uml-final.png`;
9. implementación de la superclase y subclases;
10. evidencia de encapsulación;
11. evidencia de herencia y uso de `super`;
12. evidencia de sobrescritura y polimorfismo;
13. evidencia de enlace dinámico;
14. evidencia de `instanceof` y casting;
15. implementación e integración del sistema de riego;
16. evidencia de las pruebas realizadas;
17. historial de commits significativos;
18. `README.md` actualizado.

---

# Evidencia individual

Debido a que esta práctica es individual, deberás ser capaz de explicar las decisiones tomadas durante todo el desarrollo.

En el `README.md`, incluye una sección denominada:

```markdown
## Reflexión final
```

Responde brevemente:

1. ¿Cuál es la superclase de tu sistema y cuáles son sus subclases?
2. ¿Por qué existe una relación de herencia entre ellas?
3. ¿Qué atributos o comportamientos decidiste colocar en la superclase y por qué?
4. ¿Para qué utilizaste `super`?
5. ¿Qué método sobrescribiste?
6. ¿Dónde puedes observar polimorfismo en tu programa?
7. ¿Dónde puedes observar enlace dinámico?
8. ¿Para qué utilizaste `instanceof` y casting?
9. ¿Qué cambio realizaste entre tu UML inicial y tu UML final?
10. Si tuvieras que agregar un `SensorLuminosidad`, ¿qué partes del programa tendrías que modificar?

No memorices únicamente las definiciones. Utiliza tu propio código para explicar tus respuestas.

---

# Criterios de evaluación

| Criterio | Porcentaje |
|---|---:|
| Modelo de clases | 25 % |
| Implementación orientada a objetos | 35 % |
| Aplicación al problema | 15 % |
| Pruebas y repositorio | 25 % |
| **Total** | **100 %** |

## Modelo de clases — 25 %

El UML deberá representar clases, atributos, métodos, relaciones, herencia y responsabilidades coherentes.

Se considerará también:

- calidad del análisis previo;
- correspondencia entre problema, responsabilidades y clases;
- identificación correcta de generalización y especialización;
- claridad de la jerarquía;
- justificación de las decisiones de diseño;
- encapsulación propuesta;
- actualización del modelo después de la implementación.

---

## Implementación orientada a objetos — 35 %

Se evaluará que:

- existan objetos creados mediante constructores;
- los atributos estén adecuadamente encapsulados;
- se utilicen correctamente los modificadores de acceso;
- exista una jerarquía coherente de clases;
- se reutilicen atributos y comportamientos mediante herencia;
- se utilice correctamente `super`;
- exista sobrescritura mediante `@Override`;
- se utilice polimorfismo;
- pueda observarse el enlace dinámico;
- `instanceof` y casting se utilicen de manera justificada;
- cada clase conserve responsabilidades claramente definidas;
- el código corresponda razonablemente con el diseño propuesto.

---

## Aplicación al problema — 15 %

El modelo deberá representar de manera coherente el sistema de invernadero propuesto.

Se evaluará especialmente:

- representación de los diferentes sensores;
- interpretación coherente de las mediciones;
- diferenciación entre características generales y especializadas;
- representación del sistema de riego;
- relación lógica entre la humedad del suelo y el riego;
- separación adecuada de responsabilidades.

Los conocimientos agronómicos o electrónicos **no forman parte de este criterio**. Los valores y reglas establecidos en `Contexto_Invernadero_Inteligente.md` son suficientes para realizar la práctica.

---

## Pruebas y repositorio — 25 %

Se evaluará:

- funcionamiento demostrable;
- casos de prueba documentados;
- `README.md` actualizado;
- archivo `docs/01-analisis-diseno.md`;
- UML inicial y final;
- commits significativos;
- trazabilidad del proceso;
- evidencia de que el análisis y diseño fueron realizados antes de la implementación;
- reflexión final sobre el propio código.

---

# Condición de trabajo individual

Esta práctica es individual.

El historial del repositorio deberá permitir observar tu proceso de trabajo mediante commits significativos correspondientes al análisis, diseño, implementación, pruebas y documentación.

No se considerará evidencia suficiente:

- subir todo el proyecto mediante un único commit al finalizar;
- realizar únicamente cambios de formato;
- incluir un análisis creado después de haber terminado la implementación;
- presentar un UML inicial generado después del código;
- incluir documentación que no corresponda con el programa entregado.

---

# Regla importante sobre el proceso

El análisis y el diseño **no son actividades posteriores para justificar código ya terminado**.

Por ello:

> El archivo `docs/01-analisis-diseno.md` y `docs/uml-inicial.png` deberán existir en el historial del repositorio **antes de la implementación de las clases**.

Si durante el desarrollo descubres que tu diseño necesita cambios, no hay problema.

Realiza las modificaciones necesarias, documenta posteriormente las decisiones tomadas y conserva mediante nuevos commits la evolución de tu trabajo.

El objetivo no es que tu primer diseño sea perfecto.

El objetivo es que puedas demostrar el proceso:

```text
problema
   ↓
análisis
   ↓
diseño
   ↓
implementación
   ↓
pruebas
   ↓
revisión del diseño
```

