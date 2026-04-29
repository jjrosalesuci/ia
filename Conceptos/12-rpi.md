# RPI (Research, Plan, Implement)

## Definicion simple

RPI es una forma de trabajar con IA en tres fases: primero investigar, despues planificar y por ultimo implementar.

En simple: en lugar de pedirle al modelo que resuelva todo de una sola vez, se separa el trabajo en pasos claros para reducir errores y mejorar la calidad del resultado.

## Explicacion tecnica

RPI es un patron de orquestacion que estructura una tarea compleja en tres etapas bien diferenciadas:

- **Research (investigar):** el sistema recopila la informacion necesaria antes de actuar. Lee archivos, consulta documentacion, explora el codigo o busca contexto relevante. El objetivo es entender el problema antes de proponer una solucion.
- **Plan (planificar):** con la informacion ya recogida, el sistema redacta un plan explicito de los pasos a seguir. Ese plan suele ser una lista corta y verificable, que puede revisarse antes de ejecutarse.
- **Implement (implementar):** recien entonces se realizan los cambios reales: editar archivos, ejecutar comandos, generar contenido o aplicar correcciones. La implementacion sigue el plan en lugar de improvisar.

Este patron es habitual en agentes de codigo y asistentes que trabajan sobre proyectos reales, porque separa el razonamiento del cambio efectivo y permite validar cada fase por separado.

## Ejemplo practico

Supongamos que un usuario pide:

"Corregi el bug que hace fallar el login cuando el email tiene mayusculas."

Aplicando RPI, un agente puede actuar asi:

1. **Research:** abre los archivos de autenticacion, busca donde se compara el email, revisa los tests existentes y entiende como se normalizan los datos.
2. **Plan:** propone un plan minimo, por ejemplo: "convertir el email a minusculas antes de comparar en `login.service`, agregar un test que cubra el caso con mayusculas".
3. **Implement:** edita el archivo afectado, agrega el test, corre la suite y confirma que el bug esta resuelto.

El resultado es un cambio enfocado, justificado y verificable, en lugar de una modificacion amplia hecha sin contexto previo.

## Analogia facil

RPI se parece a como trabaja un buen carpintero antes de cortar madera.

Primero mira el espacio y toma medidas (research), despues dibuja un plano de lo que va a construir (plan) y recien entonces enciende la sierra (implement). Si se saltea las dos primeras etapas, es muy probable que tenga que rehacer el trabajo.

## Relacion con los demas conceptos

- Recibe el objetivo inicial como un [Prompt](01-prompt.md), normalmente formulado como una tarea a resolver.
- Se apoya fuertemente en [Prompt engineering](02-prompt-engineering.md), porque cada fase se beneficia de instrucciones claras y separadas.
- La fase de research es, en esencia, una forma de armar buen [Contexto](03-contexto.md) antes de pedirle al modelo que decida.
- Usa un [LLM](05-llm.md) como motor para razonar, planificar y redactar los cambios.
- Todo lo que se investiga, planifica e implementa termina representado en [Tokens](04-tokens.md) al pasar por el modelo.
- Puede usar [Embeddings](06-embeddings.md) durante la fase de research para encontrar archivos o fragmentos relevantes por similitud semantica.
- Puede ejecutarse sobre un modelo ajustado mediante [Fine-tuning](07-fine-tuning.md), aunque no es un requisito.
- Suele empaquetarse como un [Skill](08-skill.md) reutilizable, para aplicar el mismo patron a distintos tipos de tareas.
- Es un patron de trabajo natural para un [Agente](11-agente.md), que coordina las tres fases y decide cuando avanzar de una a la siguiente.
- Puede apoyarse en herramientas externas conectadas via [MCP](09-mcp.md) para leer archivos, ejecutar comandos o consultar servicios durante research e implement.
- Puede consumir un [Prompt dentro de MCP](10-prompt-en-mcp.md) como plantilla estructurada para cada una de las fases.

## Idea clave

RPI no es una tecnologia nueva, sino una disciplina de trabajo: investigar antes de planificar y planificar antes de implementar. Aplicado a un agente de IA, reduce errores, hace los cambios mas explicables y permite validar el avance paso a paso.
