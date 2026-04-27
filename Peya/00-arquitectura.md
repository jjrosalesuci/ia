# Framework de decision para capacidades de IA en Peya

Este documento define como decidir dos cosas para cualquier capacidad de IA, nueva o existente:

1. que debe ser
2. si debe quedar disponible y en que alcance organizacional

La meta no es solo ordenar el catalogo actual. La meta es evitar tres problemas frecuentes:

- capacidades duplicadas
- capacidades publicadas con mas alcance del necesario
- capacidades mal clasificadas, por ejemplo una skill usada como si fuera tool o un prompt tratado como si fuera workflow

## 1. Regla base

Toda capacidad debe responder estas dos preguntas, en este orden:

1. cual es su responsabilidad principal
2. cual es el menor alcance organizacional en el que sigue siendo util

La politica por defecto es restrictiva:

- una capacidad nace en el nivel mas bajo posible
- solo se amplia cuando hay evidencia de reutilizacion y necesidad real
- toda promocion de alcance requiere aprobacion centralizada

La clasificacion siempre se hace por contrato principal, no por implementacion interna.

Ejemplo:

- una skill puede usar tools y prompts, pero sigue siendo skill si su contrato principal es resolver un workflow reutilizable
- un agente puede usar skills, tools y prompts, pero sigue siendo agente si su contrato principal es coordinar pasos para cumplir un objetivo

## 2. Estructura organizacional

La organizacion se entiende en cuatro niveles:

- Equipo: capacidad usada y mantenida por un solo equipo
- Dominio: capacidad compartida por uno o mas equipos que trabajan sobre el mismo espacio de negocio o tecnologia
- Tribu: capacidad compartida por varios dominios de una misma tribu
- Empresa: capacidad transversal a varias tribus o estandar corporativo

Regla general:

- cuanto mayor es el alcance, mayor es el radio de impacto
- cuanto mayor es el radio de impacto, mayores deben ser los controles, la documentacion y la gobernanza

## 3. Mapa de capacidades

En Peya trabajamos con cuatro tipos principales de capacidad:

1. agente
2. skill
3. tool
4. prompt MCP

### 3.1 Agente

Un agente es la capa que recibe un objetivo y decide como avanzar. Puede planificar, elegir pasos, usar tools, invocar skills, consumir prompts y revisar resultados intermedios.

Un agente se usa cuando el usuario no solo necesita una respuesta, sino que necesita ejecucion guiada hacia una meta.

Ejemplo:

- gemini-cli actuando sobre un repositorio para leer archivos, proponer cambios y validar resultados

### 3.2 Skill

Una skill es un flujo de trabajo reutilizable orientado a una tarea concreta. Encapsula criterio de negocio, pasos recurrentes, formato de salida esperado y, si hace falta, uso de tools o prompts.

Una skill se usa cuando la organizacion quiere repetir siempre una misma forma de resolver una tarea.

Ejemplos:

- resumir una reunion con formato estandar
- analizar un incidente y devolver hallazgos, riesgos y proximos pasos

Para Peya, una skill no es solo una idea. Debe existir como artefacto tecnico empaquetado, con una estructura reconocible por la plataforma.

Estructura minima esperada de una skill:

- una carpeta propia
- un archivo `SKILL.md` obligatorio
- `scripts/` opcional para codigo ejecutable
- `references/` opcional para documentacion cargable bajo demanda
- `assets/` opcional para plantillas u otros recursos

Dentro de `SKILL.md`, el frontmatter cumple una funcion critica: describir que hace la skill y cuando debe activarse. El cuerpo del archivo contiene las instrucciones completas. Los archivos enlazados en `references/` o `assets/` deben usarse para ampliar contexto sin inflar innecesariamente la carga inicial.

Regla importante:

- una skill debe enseñar a la IA como ejecutar un workflow de forma consistente
- una tool le da acceso a un sistema
- un prompt MCP estandariza una instruccion
- una skill puede usar tools y prompts, pero no se reemplaza por ellos

### 3.3 Tool

Una tool es una capacidad atomica que opera sobre un sistema, un dato o una integracion externa. Su contrato debe ser claro, parametrizable y auditable.

Una tool se usa cuando hace falta leer o ejecutar una operacion concreta sobre un sistema.

Ejemplos:

- consultar dashboards en Grafana
- buscar repositorios o pull requests en GitHub
- recuperar logs para un servicio y un intervalo de tiempo

### 3.4 Prompt MCP

Un prompt MCP es una instruccion reutilizable, parametrizable y publicada dentro del ecosistema MCP. Sirve para estandarizar una forma de pedirle algo al modelo sin convertir esa necesidad en una skill completa.

Un prompt MCP se usa cuando el valor principal esta en la forma de razonar o formatear la respuesta, no en ejecutar un workflow multi paso ni en operar directamente sobre un sistema.

Ejemplos:

- analizar un incidente a partir de descripcion, logs y severidad
- resumir un cambio tecnico en formato de changelog ejecutivo

## 4. Que debe ser cada capacidad

Usar esta secuencia de decision.

### Paso 1: decide si estas frente a un agente

Clasificar como agente si la capacidad:

- recibe objetivos amplios en lugar de una sola operacion
- decide que pasos seguir
- elige cuando usar tools, skills o prompts
- puede iterar segun resultados intermedios

Si no cumple eso, seguir al paso 2.

### Paso 2: decide si estas frente a una tool

Clasificar como tool si la capacidad:

- expone una operacion concreta sobre un sistema o fuente de datos
- tiene parametros de entrada explicitos
- tiene una salida clara y auditable
- puede requerir permisos, trazabilidad o controles de acceso

Senales de que no deberia ser tool:

- resuelve un flujo de negocio completo
- depende de mucho criterio narrativo del modelo
- su valor principal esta en la redaccion de la instruccion y no en la operacion del sistema

Si no cumple eso, seguir al paso 3.

### Paso 3: decide si estas frente a un prompt MCP

Clasificar como prompt MCP si la capacidad:

- estandariza una forma de pedir analisis, sintesis o generacion
- no ejecuta efectos laterales por si misma
- puede reutilizarse con variables de entrada bien definidas
- sirve como componente reusable dentro del MCP Server

Senales de que no deberia ser prompt MCP:

- necesita orquestacion real entre multiples pasos
- necesita usar herramientas como parte esencial de su contrato
- el consumidor espera una capacidad operativa mas que una instruccion reusable

Si no cumple eso, seguir al paso 4.

### Paso 4: clasificar como skill

Clasificar como skill si la capacidad:

- encapsula un flujo de trabajo reusable
- combina criterio de negocio con una salida esperada
- puede usar prompts, contexto, tools o pasos secuenciales
- resuelve una tarea repetitiva mejor como capacidad empaquetada que como instruccion ad hoc

Regla de desempate:

- si una capacidad mezcla varias cosas, se clasifica por lo que promete al consumidor
- si promete una operacion puntual, es tool
- si promete una instruccion reusable, es prompt MCP
- si promete resolver una tarea recurrente, es skill
- si promete coordinar capacidades para lograr un objetivo, es agente

## 5. Criterios minimos para crear cada tipo

Una capacidad no deberia existir solo porque es posible implementarla. Debe tener un contrato claro y un responsable claro.

### 5.1 Criterios minimos para crear una skill

Crear una skill solo si existen todos estos elementos:

- problema recurrente y reutilizable
- inputs y outputs definidos
- flujo de trabajo estable, aunque pueda evolucionar
- criterio de negocio explicito
- responsable funcional o tecnico
- limite de alcance claro: que resuelve y que no resuelve
- ejemplos de uso o casos de prueba basicos
- artefacto empaquetado en carpeta propia con `SKILL.md` obligatorio
- frontmatter valido con nombre y descripcion de activacion
- descripcion que diga explicitamente que hace la skill y cuando debe usarse
- instrucciones principales en `SKILL.md` y detalles auxiliares en `references/` o `assets/` cuando haga falta
- pruebas minimas de activacion, resultado y consistencia

Pruebas minimas esperadas para una skill:

- pruebas de activacion: verificar que la skill se dispare en consultas relevantes y no en consultas irrelevantes
- pruebas de resultado: verificar que el output tenga la estructura y calidad esperadas
- pruebas de consistencia: verificar que el workflow se complete de forma parecida en varias ejecuciones comparables

No crear una skill si:

- solo envuelve una unica llamada a un sistema
- solo cambia la forma de redactar una instruccion
- no hay claridad sobre quien la mantiene
- no existe forma clara de saber cuando debe activarse
- no puede expresarse como un `SKILL.md` mantenible con una descripcion de uso concreta

### 5.2 Criterios minimos para crear una tool

Crear una tool solo si existen todos estos elementos:

- operacion atomica bien definida
- parametros de entrada explicitos
- fuente de datos o sistema de destino identificado
- politica de permisos y acceso
- salida esperada y manejo de errores
- trazabilidad de uso
- responsable del sistema o integracion asociado

No crear una tool si:

- en realidad se necesita un workflow multi paso
- la herramienta esconderia demasiado criterio de negocio
- no existe un modelo claro de permisos o auditoria

### 5.3 Criterios minimos para crear un prompt MCP

Crear un prompt MCP solo si existen todos estos elementos:

- necesidad reusable de analisis, sintesis o generacion
- variables de entrada claramente nombradas
- contexto minimo esperado documentado
- formato de salida esperado
- ejemplos de entrada y salida o criterios de evaluacion
- responsable de mantener la instruccion

No crear un prompt MCP si:

- la necesidad requiere orquestacion real entre multiples pasos
- hace falta acceso operativo a sistemas externos
- la reutilizacion es demasiado local y no justifica entrar al catalogo MCP

### 5.4 Criterios minimos para crear un agente

Crear o extender un agente solo si existen todos estos elementos:

- objetivo amplio que no cabe en una sola skill, tool o prompt
- politica clara sobre que capacidades puede invocar
- reglas de parada y validacion
- manejo de errores y fallos intermedios
- responsable de la experiencia y del comportamiento
- controles para tareas de riesgo alto

No crear un agente si:

- basta con una skill o prompt reusable
- se esta usando el agente para esconder mala definicion de capacidades mas simples

## 6. Si debe quedar disponible y en que alcance

Despues de clasificar la capacidad, hay que decidir si debe publicarse y para quien.

Las cuatro dimensiones obligatorias son:

1. Seguridad y acceso a datos: que datos puede leer o exponer, y con que sensibilidad
2. Riesgo operativo: si puede causar cambios, errores, incidentes o decisiones equivocadas de alto impacto
3. Reutilizacion esperada: cuantos consumidores reales existen fuera del equipo creador
4. Especializacion del conocimiento: cuanto depende de lenguaje, contexto o reglas locales

### 6.1 Regla de publicacion por defecto

- si hay duda, quedarse en el nivel mas bajo posible
- si no hay responsable claro, no se publica
- si el riesgo es alto y no hay controles, no se amplia el alcance
- si la necesidad es muy local, no se publica fuera del equipo o dominio

### 6.2 Matriz de alcance

| Alcance | Cuando corresponde | Senales tipicas | Exigencia minima |
| --- | --- | --- | --- |
| Equipo | La capacidad sirve a un solo equipo o esta en etapa temprana | conocimiento muy local, baja reutilizacion, experimentacion controlada | responsable local, contrato basico, documentacion minima |
| Dominio | La capacidad sirve a dos o mas equipos del mismo dominio | vocabulario y procesos compartidos, reutilizacion dentro del dominio | responsable claro, usuarios identificados, controles de acceso acordes al dominio |
| Tribu | La capacidad sirve a varios dominios de una misma tribu | estandar comun de tribu, menor especializacion local | documentacion estable, soporte definido, observabilidad basica |
| Empresa | La capacidad es transversal a varias tribus o es un estandar corporativo | reutilizacion amplia, baja especializacion local, necesidad de consistencia global | responsable central, versionado, controles, trazabilidad, soporte y aprobacion centralizada |

### 6.3 Reglas practicas de promocion

Promover de Equipo a Dominio cuando:

- al menos dos equipos del mismo dominio la necesitan
- el conocimiento sigue siendo mayormente del mismo dominio
- el riesgo y los datos permiten compartirla dentro de ese limite

Promover de Dominio a Tribu cuando:

- al menos dos dominios de la misma tribu la necesitan
- existe un proceso o lenguaje comun suficiente para estandarizar
- ya no tiene sentido mantener variantes por dominio

Promover de Tribu a Empresa cuando:

- varias tribus tienen la misma necesidad
- el conocimiento requerido es transversal o estandar corporativo
- existe un responsable central capaz de mantener, versionar y gobernar la capacidad

No promover aunque haya reutilizacion si:

- expone datos sensibles sin controles adecuados
- introduce riesgo operativo alto sin controles preventivos
- depende fuertemente de conocimiento local
- no existe un responsable sostenible

## 7. Gobernanza de publicacion

La publicacion mas amplia no es un premio. Es una responsabilidad adicional.

### 7.1 Responsabilidades

- Creador: propone la capacidad, define contrato y documenta el caso de uso
- Responsable de capacidad: mantiene la capacidad y responde por calidad, versionado y adopcion
- Responsable de sistema o datos: valida tools o capacidades que leen o modifican sistemas concretos
- Gobernanza central: aprueba toda promocion de alcance por encima del nivel de origen

### 7.2 Regla de aprobacion

- crear algo para un solo equipo puede resolverse localmente si cumple las reglas de este documento
- ampliar una capacidad a Dominio, Tribu o Empresa requiere aprobacion centralizada
- cualquier capacidad con impacto alto sobre datos o sistemas puede requerir revision central incluso antes de salir de Equipo

## 8. Donde vive cada cosa en el stack actual

Este framework tambien sirve para reclasificar el inventario existente.

| Activo actual | Clasificacion correcta | Motivo |
| --- | --- | --- |
| gemini-cli | Agente | recibe objetivos, interactua con contexto y puede coordinar herramientas y pasos |
| Antigravity | Superficie de agente o cliente | no es skill ni tool; es una interfaz o canal de uso |
| Peya Gemini Extension | Catalogo y distribucion de skills | no es una skill en si misma; es la superficie donde se publican o descubren skills |
| Peya MCP Server | Superficie de publicacion MCP | no es una tool ni un prompt; es el servidor que expone tools y prompts |
| Acceso a Grafana | Tool | operacion sobre sistema externo con parametros y permisos |
| Acceso a GitHub | Tool | operacion sobre sistema externo con contrato definido |
| Analisis de logs | Tool o skill, segun contrato | si solo consulta logs es tool; si interpreta y resume un workflow recurrente, es skill |
| Biblioteca de prompts reutilizables | Prompt MCP | estandariza instrucciones parametrizables dentro del MCP Server |

## 9. Checklist operativo para developers y reviewers

Usar este checklist antes de crear o publicar una capacidad.

### 9.1 Primero: que debe ser

1. El consumidor necesita una operacion puntual sobre un sistema o dato externo.
	Si la respuesta es si, probablemente es tool.
2. El consumidor necesita una instruccion reusable para analizar, resumir o generar algo.
	Si la respuesta es si, probablemente es prompt MCP.
3. El consumidor necesita un workflow reusable con criterio de negocio y varios pasos.
	Si la respuesta es si, probablemente es skill.
4. El consumidor necesita cumplir un objetivo amplio y la capacidad debe decidir pasos o elegir otras capacidades.
	Si la respuesta es si, probablemente pertenece a la capa de agente.
5. Cual es el contrato principal que vera el consumidor.
	Esa respuesta define la clasificacion final.
6. Si se clasifica como skill, puede describirse con una carpeta clara, un `SKILL.md` mantenible y una descripcion de activacion concreta.
	Si la respuesta es no, probablemente aun no esta lista para publicarse como skill.

### 9.2 Segundo: si debe dejarse disponible

1. Que datos toca y que sensibilidad tienen.
2. Puede leer, escribir o modificar sistemas.
3. Que impacto tendria un uso incorrecto o una mala respuesta.
4. Cuantos equipos, dominios o tribus la necesitan realmente.
5. Cuanto depende de conocimiento local.
6. Quien la mantiene y quien aprueba cambios.
7. Que controles existen para trazabilidad, permisos y reversion.
8. Cual es el menor alcance en el que sigue siendo util.

### 9.3 Reglas de corte

No publicar si ocurre cualquiera de estas condiciones:

- no hay responsable claro
- no hay consumidor identificado
- no hay claridad sobre inputs, outputs o permisos
- el riesgo operativo es alto y no hay controles
- la capacidad esta mal clasificada y solo intenta esconder complejidad de diseño

## 10. Decision final esperada

Toda propuesta nueva o capacidad existente debe terminar con una decision explicita en este formato:

- Tipo: agente, skill, tool o prompt MCP
- Alcance inicial: Equipo, Dominio, Tribu o Empresa
- Justificacion de alcance: reutilizacion, especializacion, seguridad y riesgo
- Responsable: persona o equipo responsable
- Superficie de publicacion: agente, extension o MCP Server
- Condicion de promocion futura: que evidencia haria valido subir de alcance

## 11. Resumen ejecutivo

La pregunta correcta no es solo "podemos crear esta capacidad". Las preguntas correctas son:

1. cual es la capacidad correcta para este problema
2. cual es el menor alcance seguro y util para publicarla

En Peya:

- un agente coordina
- una skill resuelve workflows reusables
- una tool opera sobre sistemas
- un prompt MCP estandariza instrucciones reutilizables

Y en todos los casos aplica la misma regla: clasificar por responsabilidad principal, publicar en el menor alcance posible y ampliar solo cuando haya evidencia clara y aprobacion centralizada.