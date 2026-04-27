# Prompt dentro de MCP

## Definicion simple

Un prompt dentro de MCP es una instruccion reutilizable que forma parte de una arquitectura conectada por el Model Context Protocol.

En vez de ser solo un texto escrito manualmente por el usuario, puede venir preparado por una herramienta o servidor y usarse dentro de un flujo mas grande.

## Explicacion tecnica

Dentro del ecosistema MCP, un servidor puede exponer prompts reutilizables o ayudar a construir prompts a partir de datos, parametros y contexto externo. Eso permite que los clientes de IA consuman instrucciones estructuradas de manera consistente.

Desde una mirada tecnica, esto significa que el prompt deja de ser solo una cadena improvisada y pasa a ser parte de una interfaz compartida. Puede incluir:

- variables de entrada
- contexto recuperado por herramientas
- formato esperado de salida
- reglas del dominio
- pasos sugeridos para resolver una tarea

Eso mejora reutilizacion, control y consistencia dentro de sistemas con multiples componentes.

## Ejemplo practico

Supongamos que un servidor MCP ofrece un prompt llamado "analizar_incidente".

Ese prompt podria recibir como parametros:

- descripcion del incidente
- logs recientes
- severidad
- servicio afectado

El cliente usa ese prompt ya preparado y el modelo recibe una instruccion mucho mas rica y consistente que un mensaje improvisado cada vez.

## Analogia facil

Es como una plantilla profesional en una empresa.

En lugar de redactar desde cero cada informe, usas un formato aprobado con campos claros. Eso reduce errores y hace que todos trabajen con la misma base.

## Relacion con los demas conceptos

- Parte del concepto general de [Prompt](01-prompt.md), pero en un entorno mas estructurado.
- Suele ser resultado de [Prompt engineering](02-prompt-engineering.md), porque alguien tuvo que diseñarlo bien para que sea reutilizable.
- Integra [Contexto](03-contexto.md) procedente de herramientas, recursos o sistemas externos.
- Termina siendo procesado por un [LLM](05-llm.md), igual que cualquier otra instruccion.
- Puede incorporar informacion recuperada mediante [Embeddings](06-embeddings.md), por ejemplo documentos semanticamente relevantes.
- Puede formar parte de un [Skill](08-skill.md) que automatiza una tarea recurrente.
- Puede ser usado por un [Agente](11-agente.md) como parte de una secuencia de trabajo con herramientas y decisiones intermedias.
- Existe precisamente dentro de una arquitectura [MCP](09-mcp.md), que permite compartir prompts, recursos y herramientas de forma estandar.

## Idea clave

Un prompt dentro de MCP es un prompt convertido en componente de sistema: mas reusable, mas controlado y mejor conectado con herramientas y contexto externo.