# Skill

## Definicion simple

En sistemas de IA, un skill es una capacidad empaquetada para hacer una tarea concreta.

No es una "habilidad humana" abstracta, sino un componente reutilizable que le enseña al sistema como resolver cierto tipo de trabajo.

## Explicacion tecnica

Un skill suele combinar instrucciones, reglas, contexto esperado y, a veces, acceso a herramientas o pasos de ejecucion. Su objetivo es encapsular una funcion concreta para que un asistente o agente no tenga que improvisarla desde cero cada vez.

Dependiendo de la plataforma, un skill puede incluir:

- prompts especializados
- formato de entrada y salida
- criterios de decision
- llamadas a herramientas
- pasos secuenciales de trabajo
- restricciones de seguridad o validacion

En otras palabras, un skill convierte una capacidad en una pieza reutilizable del sistema.

## Ejemplo practico

Un asistente empresarial puede tener un skill llamado "resumir reunion".

Ese skill podria:

- recibir una transcripcion
- extraer acuerdos
- listar tareas pendientes
- devolver un resumen en formato fijo

El usuario no necesita diseñar todo desde cero cada vez; el sistema reutiliza esa capacidad ya preparada.

## Analogia facil

Piensa en una caja de herramientas.

Un skill es como un destornillador especializado: no resuelve cualquier problema del mundo, pero es muy bueno para una tarea concreta y repetible.

## Relacion con los demas conceptos

- Puede usar un [Prompt](01-prompt.md) interno para orientar la tarea que resuelve.
- Suele apoyarse en [Prompt engineering](02-prompt-engineering.md), porque un skill bien diseñado contiene instrucciones bien afinadas.
- Puede agregar [Contexto](03-contexto.md) especifico antes de pedir una respuesta al modelo.
- Normalmente delega el razonamiento linguistico a un [LLM](05-llm.md).
- Puede usar [Embeddings](06-embeddings.md) para buscar informacion relacionada.
- Puede ejecutarse sobre un modelo ajustado con [Fine-tuning](07-fine-tuning.md), aunque eso no es obligatorio.
- Suele ser invocado por un [Agente](11-agente.md), que decide cuando usar esa capacidad dentro de un flujo mayor.
- Puede conectarse con herramientas externas mediante [MCP](09-mcp.md).
- En muchos casos incluye o consume un [Prompt dentro de MCP](10-prompt-en-mcp.md) cuando trabaja sobre una infraestructura compartida de prompts y herramientas.

## Idea clave

Un skill convierte una tarea recurrente en una capacidad reusable, en lugar de depender siempre de instrucciones improvisadas.