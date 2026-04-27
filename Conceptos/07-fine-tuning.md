# Fine-tuning

## Definicion simple

Fine-tuning es volver a entrenar parcialmente un modelo ya existente para que se adapte mejor a una tarea o dominio concreto.

Es como tomar un modelo generalista y darle una especializacion.

## Explicacion tecnica

Un modelo base aprende patrones generales durante un entrenamiento muy grande. El fine-tuning añade una fase posterior de entrenamiento con datos mas especificos para ajustar sus parametros a una necesidad concreta.

Por ejemplo, puede usarse para:

- adoptar un estilo de respuesta determinado
- mejorar rendimiento en un sector, como legal o medico
- seguir formatos muy estrictos
- clasificar tipos de documentos
- responder mejor sobre una tarea repetitiva del negocio

La idea central es que el modelo no solo reciba mejores instrucciones, sino que cambie internamente parte de su comportamiento estadistico a partir de ejemplos adicionales.

## Ejemplo practico

Una empresa de soporte tecnico tiene miles de tickets etiquetados por categoria. En vez de depender solo de prompts, entrena un modelo con esos casos para que identifique con mas precision si un ticket corresponde a facturacion, acceso, infraestructura o integraciones.

Eso es un caso tipico de fine-tuning: adaptar el modelo a datos propios y a una tarea concreta.

## Analogia facil

Imagina un medico general que luego hace una residencia en cardiologia.

Sigue siendo medico, pero ahora esta mas afinado para un tipo particular de problema.

## Relacion con los demas conceptos

- Se diferencia de [Prompt engineering](02-prompt-engineering.md): uno mejora la instruccion; el otro modifica el modelo.
- Se aplica sobre un [LLM](05-llm.md) o un modelo base parecido para volverlo mas especializado.
- Puede reducir la dependencia de prompts muy detallados, aunque no elimina la necesidad de un buen [Prompt](01-prompt.md).
- Puede trabajar mejor si el sistema sigue usando buen [Contexto](03-contexto.md), porque un modelo especializado tampoco adivina informacion ausente.
- Puede combinarse con [Embeddings](06-embeddings.md), por ejemplo en sistemas que recuperan informacion y ademas usan un modelo adaptado al dominio.
- Puede formar parte de una arquitectura con [Skill](08-skill.md) y [MCP](09-mcp.md), pero no los sustituye: solo especializa el modelo central.

## Idea clave

Fine-tuning cambia al modelo. Prompt engineering cambia la forma de hablarle. Son cosas relacionadas, pero no equivalentes.