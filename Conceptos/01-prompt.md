# Prompt

## Definicion simple

Un prompt es la instruccion o entrada que una persona le da a un sistema de IA para pedirle algo.

Dicho de forma sencilla: es la manera de decirle a la IA que quieres que haga.

## Explicacion tecnica

En sistemas basados en modelos de lenguaje, un prompt es el texto de entrada que condiciona la salida del modelo. Puede incluir preguntas, instrucciones, ejemplos, restricciones de formato, contexto adicional o una combinacion de todo eso.

Desde el punto de vista tecnico, el prompt no es solo una frase suelta. Es parte del estado de entrada que el modelo recibe antes de generar tokens de respuesta. Un prompt puede contener:

- una tarea: "resume este texto"
- una restriccion: "hazlo en tres lineas"
- un rol: "actua como profesor"
- ejemplos previos: "entrada -> salida"
- contexto: datos del problema, documentos o instrucciones del sistema

Cuanto mejor definido este el prompt, mas facil es que el modelo produzca una salida util y estable.

## Ejemplo practico

### Prompt debil

"Habla de energia solar"

Este pedido es muy abierto. La IA puede responder con historia, ventajas, definiciones o cualquier otro angulo.

### Prompt mejorado

"Explica que es la energia solar para estudiantes de secundaria. Usa lenguaje sencillo, menciona 3 ventajas y termina con un ejemplo de uso en casa."

Aqui la tarea, el publico, la profundidad y la estructura quedan mucho mas claras.

## Analogía facil

Un prompt se parece a pedir un taxi.

Si solo dices "quiero ir", el conductor no sabe a donde, por que ruta ni con que prioridad.

Si dices "llevame al aeropuerto por la ruta mas rapida y evita peajes", la instruccion es mucho mas util. Con la IA pasa lo mismo.

## Relacion con los demas conceptos

- Se relaciona con [Prompt engineering](02-prompt-engineering.md) porque esa disciplina busca diseñar prompts mas claros y efectivos.
- Se relaciona con [Contexto](03-contexto.md) porque muchas veces el prompt por si solo no basta y necesita informacion adicional.
- Se relaciona con [Tokens](04-tokens.md) porque el modelo no "lee" texto como una persona: convierte el prompt en piezas mas pequenas.
- Se relaciona con [LLM](05-llm.md) porque el LLM es quien interpreta el prompt y genera la respuesta.
- Se relaciona con [Skill](08-skill.md) y [MCP](09-mcp.md) cuando el prompt no solo pide texto, sino tambien acciones apoyadas por herramientas.
- Se relaciona con [Prompt dentro de MCP](10-prompt-en-mcp.md) porque, en sistemas conectados, el prompt puede viajar como parte de una interaccion mas grande entre modelo y herramientas.

## Idea clave

El prompt es el punto de partida. Si la pregunta esta mal planteada, incluso un buen modelo tendra mas dificultad para responder bien.