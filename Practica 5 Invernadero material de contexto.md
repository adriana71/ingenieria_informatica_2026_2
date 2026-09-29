# Contexto: Sistema de invernadero inteligente 🌱

Antes de comenzar la **Práctica 5. Herencia y polimorfismo**, necesitas comprender el sistema que utilizarás como caso de estudio.

No necesitas tener conocimientos de agricultura, electrónica, automatización ni instrumentación para realizar la práctica. Este documento explica únicamente los elementos del invernadero que necesitas conocer para poder **analizar el problema y posteriormente representarlo mediante clases y objetos**.

> **Importante:** este documento describe el problema, pero **no define cómo debes diseñar las clases de tu programa**. Parte de tu trabajo consiste precisamente en analizar esta información y proponer tu propio modelo orientado a objetos.

---

# 1. ¿Qué es un invernadero?

Un **invernadero** es un espacio destinado al cultivo de plantas en el que es posible observar y, en algunos casos, modificar las condiciones ambientales en las que se desarrolla el cultivo.

Dentro de un invernadero pueden resultar importantes variables como:

- temperatura del aire;
- humedad ambiental;
- humedad del suelo;
- cantidad de luz;
- concentración de determinados gases;
- disponibilidad de agua.

En un invernadero tradicional, una persona puede observar algunas de estas condiciones y tomar decisiones, por ejemplo, regar las plantas cuando considera que el suelo está demasiado seco.

En un **invernadero inteligente**, algunos de estos procesos pueden apoyarse mediante sensores y sistemas de actuación.

---

# 2. ¿Qué hace que un invernadero sea “inteligente”?

Un sistema de este tipo puede realizar tres actividades generales:

```text
OBSERVAR  →  EVALUAR  →  ACTUAR
```

### Observar

Los **sensores** permiten obtener información sobre las condiciones del invernadero.

Por ejemplo:

```text
Temperatura del aire → 32 °C
Humedad ambiental    → 55 %
Humedad del suelo    → 22 %
```

### Evaluar

Las mediciones pueden compararse con determinados criterios para conocer el estado de una variable.

Por ejemplo:

```text
32 °C → temperatura alta

55 % de humedad ambiental
      → humedad adecuada

22 % de humedad del suelo
      → humedad baja
```

### Actuar

La información obtenida puede utilizarse para tomar alguna acción.

Por ejemplo:

```text
Humedad del suelo baja
          ↓
Es necesario regar
          ↓
Activar sistema de riego
```

En sistemas reales, estos procesos pueden ser mucho más complejos. Para esta práctica utilizaremos deliberadamente un **modelo simplificado**.

---

# 3. El invernadero de esta práctica

Para nuestro problema solamente consideraremos tres variables ambientales:

1. **temperatura del aire**;
2. **humedad ambiental**;
3. **humedad del suelo**.

Cada una será observada mediante un sensor diferente.

Además, el invernadero contará con un **sistema de riego**.

Una representación general del sistema sería:

```text
                         INVERNADERO
                              │
             ┌────────────────┼────────────────┐
             │                │                │
             ▼                ▼                ▼
       Temperatura         Humedad          Humedad
        del aire          ambiental         del suelo
             │                │                │
             ▼                ▼                ▼
           Sensor           Sensor           Sensor
                                                │
                                                │ información
                                                ▼
                                         Sistema de riego
```

Este esquema representa el **funcionamiento conceptual del sistema**.

**No es un diagrama UML ni representa las clases que deberás programar.**

---

# 4. ¿Qué es un sensor?

Un **sensor** es un dispositivo que permite obtener información sobre alguna variable del entorno.

Para esta práctica no necesitas conocer cómo funciona electrónicamente.

Nos interesa únicamente que comprendas que un sensor:

- tiene alguna forma de identificarse;
- se encuentra instalado en algún lugar;
- puede encontrarse activo o inactivo;
- obtiene una medición;
- la medición tiene un significado dependiendo de la variable observada.

Por ejemplo, considera estos tres dispositivos:

```text
Sensor A
Ubicación: zona norte
Medición: 27

Sensor B
Ubicación: zona central
Medición: 58

Sensor C
Ubicación: zona sur
Medición: 24
```

El número por sí solo no proporciona suficiente información.

Necesitamos saber **qué está midiendo cada sensor**.

Si el sensor A mide temperatura:

```text
27 °C
```

Si el sensor B mide humedad ambiental:

```text
58 %
```

Si el sensor C mide humedad del suelo:

```text
24 %
```

Por lo tanto, diferentes sensores pueden compartir ciertas características generales, pero **no necesariamente interpretan sus mediciones de la misma manera**.

Esta observación será importante cuando diseñes posteriormente tu programa.

---

# 5. Sensor de temperatura

El sensor de temperatura permite conocer la **temperatura del aire dentro del invernadero**.

En esta práctica expresaremos la temperatura en:

```text
grados Celsius (°C)
```

Algunos ejemplos de mediciones serían:

```text
15 °C
23 °C
31 °C
```

Para simplificar el ejercicio utilizaremos los siguientes criterios:

| Temperatura | Interpretación |
|---|---|
| Menor a 18 °C | Temperatura baja |
| Entre 18 °C y 30 °C | Temperatura adecuada |
| Mayor a 30 °C | Temperatura alta |

Por ejemplo:

```text
Medición: 15 °C
Resultado: temperatura baja
```

```text
Medición: 25 °C
Resultado: temperatura adecuada
```

```text
Medición: 34 °C
Resultado: temperatura alta
```

> **Nota:** estos rangos se utilizarán únicamente para simplificar la programación de la práctica. No deben interpretarse como recomendaciones agronómicas para un cultivo específico.

---

# 6. Sensor de humedad ambiental

La **humedad ambiental** indica la cantidad de humedad presente en el aire.

Para nuestra simulación se representará mediante un porcentaje:

```text
0 % a 100 %
```

Utilizaremos los siguientes criterios:

| Humedad ambiental | Interpretación |
|---|---|
| Menor a 40 % | Humedad baja |
| Entre 40 % y 70 % | Humedad adecuada |
| Mayor a 70 % | Humedad alta |

Por ejemplo:

```text
Medición: 32 %
Resultado: humedad ambiental baja
```

```text
Medición: 55 %
Resultado: humedad ambiental adecuada
```

```text
Medición: 82 %
Resultado: humedad ambiental alta
```

Nuevamente, estos valores son **criterios simplificados para esta práctica**.

---

# 7. Sensor de humedad del suelo

El sensor de humedad del suelo permite estimar qué tan húmedo o seco se encuentra el suelo donde están las plantas.

Para simplificar la simulación representaremos también esta medición mediante valores entre:

```text
0 % y 100 %
```

Para nuestro ejercicio interpretaremos:

```text
0 %   → suelo completamente seco

100 % → nivel máximo de humedad considerado
         por nuestra simulación
```

Utilizaremos los siguientes criterios:

| Humedad del suelo | Interpretación |
|---|---|
| Menor a 30 % | Humedad baja |
| Entre 30 % y 70 % | Humedad adecuada |
| Mayor a 70 % | Humedad alta |

Por ejemplo:

```text
Medición: 18 %
Resultado: humedad del suelo baja
```

```text
Medición: 48 %
Resultado: humedad del suelo adecuada
```

```text
Medición: 83 %
Resultado: humedad del suelo alta
```

> Estos porcentajes representan una **simplificación para fines de programación**. Un sensor físico real puede utilizar otras unidades, escalas, procesos de calibración o formas de interpretar sus mediciones.

---

# 8. Los sensores tienen semejanzas y diferencias

Observa ahora los tres tipos de sensores:

| Característica | Temperatura | Humedad ambiental | Humedad del suelo |
|---|---|---|---|
| Produce una medición | Sí | Sí | Sí |
| Puede identificarse | Sí | Sí | Sí |
| Tiene una ubicación | Sí | Sí | Sí |
| Puede estar activo/inactivo | Sí | Sí | Sí |
| Unidad | °C | % | % |
| Interpreta su medición | Sí | Sí | Sí |
| Criterios de interpretación | Propios | Propios | Propios |

Esto plantea una situación interesante.

Los tres dispositivos tienen **características comunes**, pero también presentan **características y comportamientos particulares**.

Por ejemplo, todos pueden proporcionar una medición, pero interpretar:

```text
32
```

depende del tipo de sensor.

Para un sensor de temperatura:

```text
32 °C → temperatura alta
```

mientras que para un sensor de humedad ambiental:

```text
32 % → humedad ambiental baja
```

y para un sensor de humedad del suelo:

```text
32 % → humedad del suelo adecuada
```

Esta combinación de **semejanzas y diferencias** será importante cuando analices cómo representar el sistema mediante programación orientada a objetos.

---

# 9. ¿Qué es el sistema de riego?

Además de observar las condiciones del invernadero, queremos representar una acción sencilla: **regar las plantas**.

Para ello consideraremos un sistema de riego que solamente puede encontrarse en uno de dos estados:

```text
ACTIVO
```

o

```text
INACTIVO
```

Cuando el sistema está activo:

```text
Sistema de riego → suministrando agua
```

Cuando está inactivo:

```text
Sistema de riego → riego detenido
```

No necesitas conocer cómo funcionan físicamente bombas, tuberías, electroválvulas o controladores.

Para esta práctica únicamente nos interesa representar **el estado y las acciones básicas del sistema de riego**.

---

# 10. Relación entre la humedad del suelo y el riego

La medición de humedad del suelo puede utilizarse para decidir si es necesario regar.

Para nuestra simulación utilizaremos una regla muy sencilla:

```text
Humedad del suelo baja
          ↓
      activar riego
```

Si la humedad del suelo ya es suficiente:

```text
Humedad del suelo adecuada o alta
          ↓
    mantener o detener riego
```

Por ejemplo:

```text
Humedad del suelo: 22 %

Interpretación:
Humedad baja

Decisión:
Activar sistema de riego
```

En cambio:

```text
Humedad del suelo: 55 %

Interpretación:
Humedad adecuada

Decisión:
El riego no necesita activarse
```

Este comportamiento está simplificado deliberadamente.

En un sistema real podrían intervenir muchas otras variables y reglas.

---

# 11. Un ejemplo completo

Imagina que en determinado momento el invernadero presenta las siguientes mediciones:

```text
Temperatura del aire:    32 °C
Humedad ambiental:       55 %
Humedad del suelo:       22 %
```

Cada medición se interpreta de acuerdo con el tipo de variable:

```text
Temperatura
32 °C
   ↓
Temperatura alta
```

```text
Humedad ambiental
55 %
   ↓
Humedad adecuada
```

```text
Humedad del suelo
22 %
   ↓
Humedad baja
```

La última medición puede provocar una acción:

```text
Humedad del suelo baja
          ↓
    requiere riego
          ↓
Sistema de riego ACTIVO
```

Podemos representar todo el proceso como:

```text
              INVERNADERO

                   │
       ┌───────────┼───────────┐
       │           │           │
       ▼           ▼           ▼
     32 °C        55 %        22 %
       │           │           │
       ▼           ▼           ▼
 Temperatura     Humedad      Humedad
    alta         adecuada      baja
                                 │
                                 ▼
                          requiere riego
                                 │
                                 ▼
                         SISTEMA DE RIEGO
                              ACTIVO
```

---

# 12. Otro escenario

Ahora considera:

```text
Temperatura:             24 °C
Humedad ambiental:       62 %
Humedad del suelo:       51 %
```

Las interpretaciones serían:

```text
24 °C → temperatura adecuada

62 %  → humedad ambiental adecuada

51 %  → humedad del suelo adecuada
```

Por lo tanto:

```text
Humedad del suelo adecuada
          ↓
No es necesario activar el riego
          ↓
Sistema de riego INACTIVO
```

---

# 13. ¿Las mediciones siempre serán reales?

No.

En esta práctica **simularás las mediciones**.

Por ejemplo, durante una prueba puedes establecer:

```text
Temperatura = 33
Humedad ambiental = 45
Humedad del suelo = 20
```

y comprobar cómo responde tu programa.

También puedes realizar otra prueba con:

```text
Temperatura = 22
Humedad ambiental = 55
Humedad del suelo = 60
```

El objetivo es que puedas probar diferentes situaciones sin necesitar sensores físicos.

---

# 14. ¿Qué información puedes asumir?

Para realizar la práctica puedes partir de los siguientes supuestos:

| Elemento | Supuesto para la práctica |
|---|---|
| Temperatura | Se expresa en °C |
| Humedad ambiental | Se expresa de 0 a 100 % |
| Humedad del suelo | Se expresa de 0 a 100 % |
| Sensor | Puede identificarse y ubicarse |
| Estado de un sensor | Puede estar activo o inactivo |
| Medición | Cada sensor mantiene o proporciona un valor |
| Interpretación | Depende del tipo de variable medida |
| Sistema de riego | Puede estar activo o inactivo |
| Decisión de riego | Puede basarse en la humedad del suelo |
| Mediciones | Son simuladas |

---

# 15. ¿Qué NO necesitas investigar?

Para realizar esta práctica **no necesitas investigar**:

- electrónica de sensores;
- Arduino;
- microcontroladores;
- conexiones eléctricas;
- protocolos de comunicación;
- calibración de sensores reales;
- bombas de agua;
- electroválvulas;
- presión o caudal;
- técnicas de cultivo;
- requerimientos de especies vegetales específicas;
- teoría de control;
- automatización industrial.

Si alguno de estos temas te interesa, puedes investigarlo por tu cuenta, pero **no forma parte de los requisitos de esta práctica**.

Tu objetivo es utilizar el invernadero como un **caso de estudio para programación orientada a objetos**.

---

# 16. Lo que este documento NO te está diciendo

Este documento te proporciona información sobre **cómo funciona el sistema que debes representar**, pero deliberadamente no responde preguntas como:

- ¿Cuántas clases debes crear?
- ¿Qué atributos debe tener exactamente cada clase?
- ¿Qué atributos deben ser `private`?
- ¿Qué métodos debe contener cada clase?
- ¿Qué constructor debes implementar?
- ¿Qué clases deben heredar de otras?
- ¿Dónde debes utilizar `super`?
- ¿Qué método debes sobrescribir?
- ¿Cómo debes implementar el polimorfismo?
- ¿Qué colección debes utilizar?
- ¿Cómo debe ser tu diagrama UML?

Responder esas preguntas **forma parte de la Práctica 5**.

---

# 17. Antes de comenzar la práctica

Después de leer este documento deberías poder explicar, sin pensar todavía en código:

1. ¿Qué información proporciona un sensor?
2. ¿Qué tienen en común los diferentes sensores del invernadero?
3. ¿En qué se diferencian?
4. ¿Por qué el número de una medición no tiene significado suficiente si no conocemos qué variable representa?
5. ¿Qué diferencia existe entre observar una variable y actuar sobre el sistema?
6. ¿Qué función cumple el sistema de riego?
7. ¿Qué información puede utilizarse para decidir si se activa el riego?
8. ¿Por qué un sensor y un sistema de riego cumplen funciones diferentes?

Si puedes responder estas preguntas, ya tienes suficiente conocimiento del problema para comenzar a diseñar tu solución.

---

## Ahora sí: pasa a la Práctica 5

Tu siguiente tarea será transformar este problema en un **modelo orientado a objetos**.

No intentes trasladar literalmente cada elemento de este documento a una clase.

Primero pregúntate:

> **¿Qué objetos existen, qué responsabilidad tiene cada uno y qué características o comportamientos comparten?**

A partir de ese análisis podrás comenzar a construir tu modelo UML y posteriormente implementarlo en Java.

Me parece especialmente importante haber incluido las secciones **“¿Qué NO necesitas investigar?”** y **“Lo que este documento NO te está diciendo”**. La primera acota el problema para que el alumno no se distraiga investigando hardware o agricultura; la segunda evita que interprete el documento de contexto como una especificación de clases.

También dejé los rangos explícitamente como **valores simplificados para la práctica**, no como valores agronómicos reales. Así pueden utilizarlos directamente para probar `evaluarMedicion()` sin que la validez agronómica se convierta en parte de la evaluación.
