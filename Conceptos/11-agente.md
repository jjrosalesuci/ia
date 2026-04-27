# Agente

## Definicion simple

Un agente de IA es un sistema que no solo responde texto, sino que tambien puede decidir pasos, usar herramientas y avanzar hacia un objetivo.

En simple: un agente se parece mas a un asistente operativo que a una sola caja de preguntas y respuestas.

## Explicacion tecnica

Un agente combina un modelo de lenguaje con logica de ejecucion, memoria de trabajo, acceso a herramientas y control de flujo. Su funcion principal es recibir un objetivo, descomponerlo en acciones y coordinar los recursos necesarios para completarlo.

Eso significa que un agente puede:

- interpretar una meta en lugar de una sola pregunta
- decidir si necesita mas contexto
- invocar herramientas o comandos
- consultar archivos, APIs o bases de conocimiento
- revisar resultados intermedios
- iterar hasta acercarse al objetivo

Un ejemplo cercano es una interfaz tipo linea de comandos como Gemini CLI: el usuario no solo pide una respuesta, sino que encarga una tarea. El agente puede leer archivos, proponer cambios, usar herramientas y devolver un resultado mas elaborado que una simple contestacion textual.

## Ejemplo practico

Supongamos que un usuario dice:

"Revisa este proyecto, identifica por que falla el build y propone una correccion minima."

Un modelo aislado podria dar sugerencias generales. Un agente, en cambio, puede:

1. inspeccionar archivos del proyecto
2. ejecutar una comprobacion o leer errores
3. localizar el punto exacto del fallo
4. editar el archivo necesario
5. validar si la correccion funciona

Eso es precisamente lo que distingue a un agente: no solo habla sobre la tarea, sino que trabaja sobre ella.

## Analogia facil

Un agente se parece a un jefe de operaciones.

No hace todo con sus propias manos, pero coordina personas, herramientas y pasos para que una meta se complete. El LLM seria como su capacidad de razonamiento linguistico; las herramientas serian el equipo que tiene disponible.

## Relacion con los demas conceptos

- Recibe objetivos o instrucciones formuladas como [Prompt](01-prompt.md).
- Se beneficia mucho del [Prompt engineering](02-prompt-engineering.md), porque objetivos mejor definidos producen planes mas utiles.
- Necesita [Contexto](03-contexto.md) para decidir bien que hacer y en que orden.
- Usa un [LLM](05-llm.md) como motor central para interpretar, razonar y redactar.
- Todo lo que procesa termina representado en [Tokens](04-tokens.md), tanto en la entrada como en la salida.
- Puede usar [Embeddings](06-embeddings.md) para recuperar informacion relevante antes de actuar.
- Puede funcionar sobre un modelo adaptado mediante [Fine-tuning](07-fine-tuning.md), aunque no depende obligatoriamente de ello.
- Puede activar un [Skill](08-skill.md) cuando necesita una capacidad especializada y reutilizable.
- Puede conectarse a herramientas y recursos externos mediante [MCP](09-mcp.md).
- Puede consumir un [Prompt dentro de MCP](10-prompt-en-mcp.md) como plantilla o instruccion estructurada dentro de un flujo mayor.

## Idea clave

Un agente no reemplaza al LLM: lo envuelve con capacidad de decidir pasos, usar herramientas y ejecutar tareas mas cercanas al trabajo real.