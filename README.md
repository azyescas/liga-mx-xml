# Práctica guiada: Diseño y validación de resultados de Liga MX con XML y DTD

## Name: Azkahira Ziret Yescas Diaz

## Expediente: 222213158

## 1. Propósito

Diseñar un formato XML para representar información estructurada de
partidos de fútbol y definir mediante un DTD las reglas que deben
cumplir los documentos creados con dicho formato.

Al finalizar, serás capaz de identificar entidades de
información, diseñar una estructura XML jerárquica, distinguir elementos
y atributos, construir XML bien formado, definir un DTD, validar el XML
y documentar el trabajo mediante Git.

## 2. Problema

Se desea almacenar en XML los resultados y estadísticas de los partidos
correspondientes a una jornada de Liga MX. La fuente indicada en el
ejercicio es la sección de resultados de ESPN México. La solución debe
representar el marcador, la jornada y las estadísticas disponibles de
cada encuentro.

## 3. Actividad 1 - Analizar la información

**Tiempo: 15 minutos**

Antes de escribir XML, consultar la información disponible para un
partido e identifique los datos necesarios.

  | Jornada     | Partido          | Estadísticas     |
  |-------------|------------------|------------------|
  | Fecha       | Equipo local     | Posesión         |
  | Competencia | Equipo visitante | Tiros            |
  | Temporada   | Marcador         | Tiros a puerta   |
  |             | Estadio          | Faltas           |
  |             | Estado           | Tarjetas         |
  |             |                  | Tiros de esquina |

### Preguntas de análisis

1.  ¿Cuál debería ser el elemento raíz?
2.  ¿Una jornada puede contener varios partidos?
3.  ¿Cada partido debe contener exactamente dos equipos?
4.  ¿Cómo distinguirían al equipo local del visitante?
5.  ¿El marcador debe representarse como un solo dato o separar los
    goles?
6.  ¿Las estadísticas pertenecen al partido o a cada equipo?
7.  ¿Qué datos son obligatorios?
8.  ¿Cuáles podrían ser opcionales?

## 4. Actividad 2 - Diseñar el modelo conceptual

**Tiempo: 15 minutos**

Gráficamente podríamos tener la siguiente jerarquía. 
Este esquema no constituye la solución definitiva. 
Cada equipo deberá ampliarlo.

``` text
liga
│
└── jornada
    │
    ├── partido
    │   ├── equipoLocal
    │   ├── equipoVisitante
    │   ├── marcador
    │   └── estadisticas
    ├── partido
    └── partido
```

Determinar si cada dato se representa como elemento o atributo (*Completar la tabla*):

  | Información        | Elemento/Atributo | Justificación |
  |--------------------|-------------------|---------------|
  | Jornada            | Elemento        |Contenedor principal|
  | Fecha              | Atributo        |Metadato descriptivo|
  | ID del partido     | Atributo        |Identificado único  |
  | Equipo local       | Elemento        |Entidad principal   |
  | Equipo visitante   | Elemento        |Entidad principal   |
  | Goles              |Elemento/Atributo|Parte de la entidad marcador|
  | Estadio            | Atributo        |Metadato descriptivo|
  | Estado del partido | Atributo        |Propiedad/metadato del partido|
  | Posesión           | Elemento        |Forma parte de los datos estadísticos|
  | Tarjetas           | Elemento        |Métrica compleja de estadísticas|

Registrar los cambios en el repositorio.
``` bash
git commit -m "Actividad 2"
```

## 5. Actividad 3 - Construir un XML mínimo

**Tiempo: 15 minutos**

Crear el documento  `xml/resultados.xml` con:

``` xml
<?xml version="1.0" encoding="UTF-8"?>
```

Implemente un solo partido con identificación, fecha, equipo local,
equipo visitante y marcador.

Comprobar que existe un solo elemento raíz, todas las etiquetas están
cerradas, el anidamiento es correcto, los atributos están entre comillas
y no existen etiquetas cruzadas.

Registrar los cambios en el repositorio.
``` bash
git commit -m "Actividad 3"
```

## 6. Actividad 4 - Incorporar estadísticas

**Tiempo: 15 minutos**

Ampliar el primer partido para incluir estadísticas relevantes. Decidir
cómo relacionar cada estadística con el equipo correspondiente.

``` text
Partido
        │
        ├──────────────┐
        ▼              ▼
     Local          Visitante
        │              │
        ▼              ▼
 Estadísticas     Estadísticas
```
# Práctica guiada: Diseño y validación de resultados de Liga MX con XML y DTD

## 1. Propósito

Diseñar un formato XML para representar información estructurada de
partidos de fútbol y definir mediante un DTD las reglas que deben
cumplir los documentos creados con dicho formato.

Al finalizar, serás capaz de identificar entidades de
información, diseñar una estructura XML jerárquica, distinguir elementos
y atributos, construir XML bien formado, definir un DTD, validar el XML
y documentar el trabajo mediante Git.

## 2. Problema

Se desea almacenar en XML los resultados y estadísticas de los partidos
correspondientes a una jornada de Liga MX. La fuente indicada en el
ejercicio es la sección de resultados de ESPN México. La solución debe
representar el marcador, la jornada y las estadísticas disponibles de
cada encuentro.

## 3. Actividad 1 - Analizar la información

**Tiempo: 15 minutos**

Antes de escribir XML, consultar la información disponible para un
partido e identifique los datos necesarios.

  | Jornada     | Partido          | Estadísticas     |
  |-------------|------------------|------------------|
  | Fecha       | Equipo local     | Posesión         |
  | Competencia | Equipo visitante | Tiros            |
  | Temporada   | Marcador         | Tiros a puerta   |
  |             | Estadio          | Faltas           |
  |             | Estado           | Tarjetas         |
  |             |                  | Tiros de esquina |

### Preguntas de análisis

1.  ¿Cuál debería ser el elemento raíz?
2.  ¿Una jornada puede contener varios partidos?
3.  ¿Cada partido debe contener exactamente dos equipos?
4.  ¿Cómo distinguirían al equipo local del visitante?
5.  ¿El marcador debe representarse como un solo dato o separar los
    goles?
6.  ¿Las estadísticas pertenecen al partido o a cada equipo?
7.  ¿Qué datos son obligatorios?
8.  ¿Cuáles podrían ser opcionales?

## 4. Actividad 2 - Diseñar el modelo conceptual

**Tiempo: 15 minutos**

Gráficamente podríamos tener la siguiente jerarquía. 
Este esquema no constituye la solución definitiva. 
Cada equipo deberá ampliarlo.

``` text
liga
│
└── jornada
    │
    ├── partido
    │   ├── equipoLocal
    │   ├── equipoVisitante
    │   ├── marcador
    │   └── estadisticas
    ├── partido
    └── partido
```

Determinar si cada dato se representa como elemento o atributo (*Completar la tabla*):

  | Información        | Elemento/Atributo | Justificación |
  |--------------------|-------------------|---------------|
  | Jornada            | Elemento        |Contenedor principal|
  | Fecha              | Atributo        |Metadato descriptivo|
  | ID del partido     | Atributo        |Identificado único  |
  | Equipo local       | Elemento        |Entidad principal   |
  | Equipo visitante   | Elemento        |Entidad principal   |
  | Goles              |Elemento/Atributo|Parte de la entidad marcador|
  | Estadio            | Atributo        |Metadato descriptivo|
  | Estado del partido | Atributo        |Propiedad/metadato del partido|
  | Posesión           | Elemento        |Forma parte de los datos estadísticos|
  | Tarjetas           | Elemento        |Métrica compleja de estadísticas|

Registrar los cambios en el repositorio.
``` bash
git commit -m "Actividad 2"
```

## 5. Actividad 3 - Construir un XML mínimo

**Tiempo: 15 minutos**

Crear el documento  `xml/resultados.xml` con:

``` xml
<?xml version="1.0" encoding="UTF-8"?>
```

Implemente un solo partido con identificación, fecha, equipo local,
equipo visitante y marcador.

Comprobar que existe un solo elemento raíz, todas las etiquetas están
cerradas, el anidamiento es correcto, los atributos están entre comillas
y no existen etiquetas cruzadas.

Registrar los cambios en el repositorio.
``` bash
git commit -m "Actividad 3"
```

## 6. Actividad 4 - Incorporar estadísticas

**Tiempo: 15 minutos**

Ampliar el primer partido para incluir estadísticas relevantes. Decidir
cómo relacionar cada estadística con el equipo correspondiente.

``` text
Partido
        │
        ├──────────────┐
        ▼              ▼
     Local          Visitante
        │              │
        ▼              ▼
 Estadísticas     Estadísticas
```

Discutir qué diseño es más comprensible, reduce duplicación, facilita el
procesamiento y permite agregar estadísticas. Registre la decisión en
`README
