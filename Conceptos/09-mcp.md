# MCP

## Definicion simple

MCP significa Model Context Protocol.

Es una forma estandar de conectar modelos de IA con herramientas, datos y funciones externas sin tener que crear integraciones distintas para cada caso.

## Explicacion tecnica

MCP es un protocolo que define como un cliente de IA y un servidor pueden intercambiar contexto, herramientas y otros recursos de manera estructurada.

La idea principal es separar el modelo de las fuentes externas de informacion y accion. En lugar de programar una conexion distinta para cada base de datos, API o sistema, MCP ofrece una interfaz comun para exponer capacidades como:

- herramientas que el modelo puede invocar
- recursos que el sistema puede leer
- prompts reutilizables
- datos estructurados necesarios para la tarea

Esto hace que los sistemas sean mas modulares. Un cliente compatible con MCP puede conectarse a distintos servidores MCP y descubrir que capacidades tiene disponibles.

## Ejemplo practico

Imagina un asistente que necesita consultar tickets de soporte y tambien revisar documentacion interna.

En vez de construir integraciones separadas y cerradas dentro del asistente, se puede conectar a:

- un servidor MCP que expone una herramienta para buscar tickets
- otro servidor MCP que expone recursos de documentacion

El modelo sigue siendo el mismo, pero ahora puede apoyarse en informacion externa mediante una interfaz comun.

## Analogia facil

MCP se parece a un enchufe estandar.

Si todos los aparatos usan conectores distintos, integrarlos es costoso. Si comparten un estandar, conectarlos es mucho mas simple.

## Relacion con los demas conceptos

- Extiende lo que puede hacer un [LLM](05-llm.md), porque le da acceso estructurado a herramientas y datos externos.
- Mejora el [Contexto](03-contexto.md) al permitir traer informacion desde otros sistemas.
- Suele ser usado por un [Agente](11-agente.md), que necesita consultar recursos o ejecutar herramientas sin integraciones ad hoc.
- Puede alojar o exponer [Prompt dentro de MCP](10-prompt-en-mcp.md) para tareas reutilizables.
- Se relaciona con [Skill](08-skill.md) porque un skill puede usar MCP para ejecutar parte de su trabajo.
- Se combina con [Prompt engineering](02-prompt-engineering.md), ya que no basta con tener herramientas: tambien hay que guiar bien su uso.
- Puede complementar sistemas con [Embeddings](06-embeddings.md) cuando el acceso a busqueda vectorial se publica como capacidad externa.

## Idea clave

MCP no reemplaza al modelo. Le da una forma ordenada de conectarse con el resto del mundo.