# Prompt engineering

## Definicion simple

Prompt engineering es el arte y la practica de escribir mejores instrucciones para que una IA responda mejor.

En pocas palabras: no solo importa hablarle a la IA, sino saber como pedirle las cosas.

## Explicacion tecnica

Prompt engineering es el proceso de diseñar, probar y refinar prompts para obtener salidas mas utiles, precisas, consistentes y seguras de un modelo.

No se trata solo de "redactar bonito". Tecnica y practicamente incluye decisiones como:

- definir claramente la tarea
- establecer formato de salida
- dar contexto relevante
- incluir ejemplos
- limitar ambiguedades
- dividir problemas complejos en pasos
- reducir respuestas inventadas o demasiado vagas

En sistemas reales, prompt engineering tambien puede involucrar prompts de sistema, plantillas, variables dinamicas, instrucciones por rol y estrategias de encadenamiento entre pasos.

## Ejemplo practico

### Version poco trabajada

"Analiza este reporte"

### Version con prompt engineering

"Analiza este reporte financiero como si fueras un analista junior. Resume los hallazgos en 5 puntos, identifica 2 riesgos principales y termina con una recomendacion ejecutiva de no mas de 80 palabras."

La segunda version reduce ambiguedad, fija formato y aclara la expectativa.

## Analogia facil

Es como pedirle a un arquitecto que te dibuje una casa.

Si dices "hazme una casa", la respuesta puede ser cualquier cosa.

Si dices "quiero una casa de una planta, con 3 habitaciones, patio pequeno y presupuesto limitado", el resultado se acerca mucho mas a lo que necesitas.

## Relacion con los demas conceptos

- Se apoya directamente en [Prompt](01-prompt.md), porque trabaja sobre la calidad de la instruccion inicial.
- Depende de [Contexto](03-contexto.md), ya que un buen prompt suele decidir que informacion adicional incluir o excluir.
- Se relaciona con [Tokens](04-tokens.md) porque prompts demasiado largos o mal estructurados consumen mas espacio y pueden degradar resultados.
- Se conecta con [LLM](05-llm.md) porque las tecnicas de prompt engineering existen para guiar mejor el comportamiento del modelo.
- Se relaciona con [Skill](08-skill.md) y [MCP](09-mcp.md) cuando el prompt debe coordinar herramientas, acciones o llamadas externas.
- Se vincula con [Prompt dentro de MCP](10-prompt-en-mcp.md) porque, en sistemas compuestos, tambien importa como se formula la instruccion dentro de un flujo conectado.
- Se mide con [Evaluacion (Evals)](13-evaluacion.md): cada cambio de prompt deberia validarse contra un golden set para detectar regresiones antes de publicarlo.

## Idea clave

Prompt engineering no cambia el cerebro del modelo; cambia la forma en que le damos instrucciones para usar mejor lo que ya sabe hacer.