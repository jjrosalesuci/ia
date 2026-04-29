# QRSPI

## Definicion simple

QRSPI es un concepto que se incorpora a esta guia para describir un elemento mas dentro de los sistemas modernos de IA.

En simple: aqui se documentara que es QRSPI, para que sirve y como se relaciona con las demas piezas.

## Explicacion tecnica

Esta seccion describira los detalles tecnicos de QRSPI: en que parte del flujo aparece, que entradas y salidas maneja y que componentes lo soportan.

Los puntos a cubrir incluyen:

- proposito principal de QRSPI
- entradas que recibe
- salidas que produce
- componentes con los que interactua
- limitaciones o consideraciones a tener en cuenta

## Ejemplo practico

Aqui se incluira un ejemplo concreto que muestre como aparece QRSPI dentro de un caso de uso real, paso a paso, para ver su efecto sobre el resultado final.

## Analogia facil

Una analogia ayudara a visualizar QRSPI sin necesidad de conocer todos los detalles tecnicos, siguiendo el mismo estilo del resto de capitulos.

## Relacion con los demas conceptos

- Se apoya en un [Prompt](01-prompt.md) como punto de entrada del usuario.
- Puede beneficiarse de buenas practicas de [Prompt engineering](02-prompt-engineering.md).
- Necesita [Contexto](03-contexto.md) para operar con informacion suficiente.
- Todo lo que procesa termina representado como [Tokens](04-tokens.md).
- Usa un [LLM](05-llm.md) como motor de interpretacion y generacion.
- Puede combinarse con [Embeddings](06-embeddings.md) para recuperar informacion relevante.
- Puede operar sobre un modelo ajustado mediante [Fine-tuning](07-fine-tuning.md).
- Puede activarse como o junto a un [Skill](08-skill.md).
- Puede integrarse con herramientas externas mediante [MCP](09-mcp.md) y consumir un [Prompt dentro de MCP](10-prompt-en-mcp.md).
- Puede ser orquestado por un [Agente](11-agente.md) dentro de un flujo mayor.
- Puede combinarse con [RPI (Research, Plan, Implement)](12-rpi.md) como ciclo de trabajo previo a su ejecucion.

## Idea clave

QRSPI se suma al resto de conceptos para completar la vision del sistema: cada pieza cumple un rol y, en conjunto, permiten que la IA reciba una peticion, la procese y devuelva una respuesta util.
