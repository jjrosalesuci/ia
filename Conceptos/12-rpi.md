# RPI (Research, Plan, Implement)

## Introduccion

Uno de los errores mas comunes al trabajar con agentes de IA es pedirles que resuelvan todo de una sola vez. El agente recibe la tarea, improvisa un plan mental, empieza a actuar y termina produciendo cambios que no estan bien justificados, que no fueron validados antes de ejecutarse, o que ignoran informacion importante que estaba disponible pero que nadie fue a buscar.

RPI es el patron que evita ese error. Separa el trabajo en tres fases claras —investigar, planificar, implementar— de manera que cada una tiene un objetivo definido y su propio criterio de exito antes de avanzar a la siguiente.

---

## Definicion simple

RPI es una forma de trabajar con IA en tres fases: primero investigar, despues planificar y por ultimo implementar.

En simple: en lugar de pedirle al modelo que resuelva todo de una sola vez, se separa el trabajo en pasos claros para reducir errores y mejorar la calidad del resultado.

---

## Explicacion tecnica

RPI es un patron de orquestacion que estructura una tarea compleja en tres etapas bien diferenciadas:

- **Research (investigar):** el sistema recopila la informacion necesaria antes de actuar. Lee archivos, consulta documentacion, explora el codigo o busca contexto relevante. El objetivo es entender el problema antes de proponer una solucion.
- **Plan (planificar):** con la informacion ya recogida, el sistema redacta un plan explicito de los pasos a seguir. Ese plan suele ser una lista corta y verificable, que puede revisarse antes de ejecutarse.
- **Implement (implementar):** recien entonces se realizan los cambios reales: editar archivos, ejecutar comandos, generar contenido o aplicar correcciones. La implementacion sigue el plan en lugar de improvisar.

Este patron es habitual en agentes de codigo y asistentes que trabajan sobre proyectos reales, porque separa el razonamiento del cambio efectivo y permite validar cada fase por separado.

### Por que cada fase importa

**Research antes de planificar:** la mayoria de los errores en sistemas de IA no vienen de malas decisiones, sino de actuar con informacion insuficiente. Sin research, el agente improvisa sobre suposiciones. Con research, el agente tiene evidencia.

**Plan antes de implementar:** el plan explicito tiene un valor doble. Primero, obliga al agente a articular su razonamiento antes de actuar, lo que a menudo revela problemas o inconsistencias. Segundo, da la oportunidad a un humano (o a otro componente del sistema) de revisar y aprobar antes de que se ejecute ningun cambio real.

**Implementacion siguiendo el plan:** si el agente improvisa durante la implementacion, el plan se convierte en decoracion. El valor del plan esta en que la implementacion lo siga fielmente.

### Aplicar RPI a distintos dominios

**RPI en desarrollo de software:**
- Research: leer el codigo relevante, entender el bug, revisar los tests existentes
- Plan: definir que cambio minimo resuelve el problema y como se validara
- Implement: editar el archivo, agregar el test, verificar que el build pasa

**RPI en generacion de contenido:**
- Research: leer la audiencia, el contexto, el tono esperado, articulos relacionados
- Plan: definir la estructura del articulo, los puntos clave y el enfoque
- Implement: escribir el contenido siguiendo la estructura planificada

**RPI en analisis de datos:**
- Research: entender que datos hay disponibles, su formato, sus columnas, sus vacios
- Plan: definir que calculos o visualizaciones son necesarios y en que orden
- Implement: ejecutar los calculos, generar las visualizaciones, interpretar los resultados

### RPI como disciplina de equipo

RPI no es solo un patron para agentes individuales. Tambien es una forma de trabajar en equipo donde las responsabilidades estan claras:

- El **researcher** es quien recopila informacion y contexto
- El **planner** es quien define los pasos antes de que alguien toque codigo o datos
- El **implementer** es quien ejecuta el plan

En equipos con agentes de IA, estas tres fases pueden ser ejecutadas por el mismo agente secuencialmente, o por agentes distintos en un sistema multi-agente.

---

## Ejemplo practico

Supongamos que un usuario pide:

```
Corregi el bug que hace fallar el login cuando el email tiene mayusculas.
```

Aplicando RPI, un agente puede actuar asi:

1. **Research:** abre los archivos de autenticacion, busca donde se compara el email, revisa los tests existentes y entiende como se normalizan los datos.
2. **Plan:** propone un plan minimo, por ejemplo: "convertir el email a minusculas antes de comparar en `login.service`, agregar un test que cubra el caso con mayusculas".
3. **Implement:** edita el archivo afectado, agrega el test, corre la suite y confirma que el bug esta resuelto.

El resultado es un cambio enfocado, justificado y verificable, en lugar de una modificacion amplia hecha sin contexto previo.

### Ejemplo sin RPI (problema tipico)

Sin RPI, el agente podria:

1. Recibir el pedido y asumir que el problema es en el frontend
2. Modificar el formulario de login para convertir el email a lowercase en el cliente
3. El cambio "funciona" en el caso del usuario, pero el bug real (la comparacion sin normalizar) sigue en el backend

Con research adecuado, el agente habria descubierto donde estaba el problema real antes de proponer cualquier solucion.

---

## Analogia facil

RPI se parece a como trabaja un buen carpintero antes de cortar madera.

Primero mira el espacio y toma medidas (research), despues dibuja un plano de lo que va a construir (plan) y recien entonces enciende la sierra (implement). Si se saltea las dos primeras etapas, es muy probable que tenga que rehacer el trabajo.

El costo de "tomar medidas" es siempre menor que el costo de cortar madera a la medida equivocada.

---

## Herramientas que soportan RPI

En el contexto de agentes de codigo, varias herramientas estan diseñadas con RPI en mente:

- **GitHub Copilot Coding Agent:** sigue explicitamente un ciclo de research (lee el repositorio), plan (propone cambios) e implement (hace los commits)
- **Cursor:** su modo agentico puede descomponerse en las tres fases
- **Claude Code:** diseñado para investigar el codebase antes de proponer cambios

Los frameworks de agentes tambien suelen soportar RPI: LangChain, AutoGen y CrewAI permiten definir agentes con fases de razonamiento separadas.

---

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
- Se extiende en [QRSPI](13-qrspi.md), que añade una fase de clarificacion (Q) antes del research y una fase de sintesis (S) entre el research y el plan.
- Los resultados de cada fase deben verificarse con [Evaluaciones](12-evaluaciones.md): ¿el research fue suficiente? ¿el plan era viable? ¿la implementacion siguio el plan?

---

## Idea clave

RPI no es una tecnologia nueva, sino una disciplina de trabajo: investigar antes de planificar y planificar antes de implementar. Aplicado a un agente de IA, reduce errores, hace los cambios mas explicables y permite validar el avance paso a paso.

---

## Resumen del capitulo

RPI es un patron de trabajo en tres fases (Research, Plan, Implement) que estructura como un agente aborda tareas complejas. Al separar la fase de recopilacion de informacion, la de planificacion y la de ejecucion, RPI produce resultados mas precisos, mas explicables y mas faciles de validar. Es aplicable tanto a agentes individuales como a equipos de trabajo y puede extenderse a QRSPI cuando la tarea es suficientemente ambigua o compleja.
