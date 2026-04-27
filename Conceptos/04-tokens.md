# Tokens

## Definicion simple

Los tokens son las piezas pequeñas en las que un modelo divide el texto para poder procesarlo.

No siempre equivalen a palabras completas: pueden ser palabras, partes de palabras, signos o fragmentos frecuentes.

## Explicacion tecnica

Los modelos de lenguaje no trabajan directamente con texto humano como si leyeran una pagina. Primero convierten el texto en tokens mediante un proceso de tokenizacion. Cada token se representa como un identificador numerico que luego el modelo transforma en vectores matematicos.

Esto importa por varias razones:

- el costo de uso suele medirse en tokens
- la velocidad depende en parte del numero de tokens
- la ventana de contexto tiene un limite de tokens
- prompts y respuestas compiten por el mismo presupuesto de espacio

Por eso, cuando se habla de entradas largas o limites del modelo, en realidad se esta hablando de tokens.

## Ejemplo practico

La frase:

"Inteligencia artificial moderna"

podria dividirse en unidades como:

- "Inteligencia"
- "artificial"
- "moderna"

Pero otra frase menos comun podria romperse en partes mas pequeñas. Lo importante es que el modelo procesa estas piezas, no el texto bruto tal como lo ve una persona.

## Analogia facil

Piensa en fichas de construccion.

Una persona ve una casa completa, pero el sistema trabaja con ladrillos. Los tokens son esos ladrillos con los que el modelo arma y entiende el texto.

## Relacion con los demas conceptos

- El [Prompt](01-prompt.md) termina convertido en tokens antes de llegar al modelo.
- El [Prompt engineering](02-prompt-engineering.md) suele buscar claridad sin desperdiciar tokens.
- El [Contexto](03-contexto.md) tambien ocupa tokens, por lo que incluir demasiado puede dejar menos espacio para la respuesta.
- El [LLM](05-llm.md) opera sobre secuencias de tokens, no sobre palabras en sentido humano.
- Los [Embeddings](06-embeddings.md) tambien parten de texto convertido en representaciones numericas, aunque con un objetivo distinto.
- En flujos con [MCP](09-mcp.md), las instrucciones y datos compartidos entre componentes tambien acaban entrando al modelo como tokens.

## Idea clave

Entender los tokens ayuda a entender costo, limites de contexto y comportamiento real de un sistema de lenguaje.