# Contexto

## Definicion simple

El contexto es la informacion adicional que ayuda a la IA a entender mejor una tarea antes de responder.

Es todo lo que acompaña a la pregunta para que la respuesta tenga sentido.

## Explicacion tecnica

En sistemas de IA, el contexto es el conjunto de datos que el modelo recibe junto con la instruccion principal. Puede incluir conversaciones previas, documentos, reglas, ejemplos, perfil del usuario, estado de una aplicacion o resultados traidos por herramientas.

Tecnicamente, el contexto forma parte de la entrada total que el modelo procesa. El modelo no tiene memoria humana persistente por defecto; necesita que la informacion relevante este presente en su ventana de contexto o le sea reinyectada por el sistema.

Por eso, en sistemas modernos, gran parte de la calidad depende no solo del modelo, sino de que contexto se selecciona, cuanto contexto se añade y como se organiza.

## Ejemplo practico

Pregunta sin contexto:

"Resume este documento"

Pregunta con contexto:

"Resume este documento para un director de operaciones. Enfocate en costos, plazos y riesgos. Ignora el detalle legal."

En el segundo caso, la IA sabe para quien resume, que priorizar y que dejar fuera.

## Analogia facil

El contexto se parece a los antecedentes que das a un medico.

Decir "me siento mal" sirve poco.

Decir "me siento mal, tengo fiebre desde ayer, alergia a penicilina y me duele el pecho" cambia por completo la calidad de la evaluacion.

## Relacion con los demas conceptos

- Complementa al [Prompt](01-prompt.md) porque una buena instruccion suele necesitar informacion de apoyo.
- Es una materia prima central del [Prompt engineering](02-prompt-engineering.md), que decide que contexto incluir.
- Se convierte en [Tokens](04-tokens.md) junto con el resto de la entrada, por lo que ocupa parte del espacio disponible.
- Alimenta al [LLM](05-llm.md), que solo puede razonar sobre lo que recibe.
- Puede venir de sistemas basados en [Embeddings](06-embeddings.md), por ejemplo al recuperar documentos semanticamente parecidos.
- Puede combinarse con [Skill](08-skill.md) y [MCP](09-mcp.md) cuando herramientas externas aportan datos adicionales.
- Influye directamente en el [Prompt dentro de MCP](10-prompt-en-mcp.md), porque las herramientas y el modelo suelen intercambiar contexto para resolver tareas.

## Idea clave

Un buen modelo con mal contexto suele fallar. Un buen contexto puede mejorar mucho el resultado sin cambiar el modelo.