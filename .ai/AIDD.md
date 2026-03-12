# AI-Driven Development 

## Architect

### Input:

- `.ai/architect/prd.instructions.md`: Instrucciones para generar el PRD.
- `.ai/architect/prd.template.md`: Plantilla con la estructura esperada del PRD.
- `.ai/architect/feature.instructions.md`: Instrucciones para generar la descripción detallada de **una** feature
- `.ai/architect/feature.template.md`: Plantilla con la estructura detallada de **una** feature.
- `.ai/architect/domain.instructions.md`: Instrucciones para generar el Domain document.
- `.ai/architect/domain.template.md`: Plantilla con la estructura esperada del Domain document.

### Output: 

- `/docs/PRD.md`: Documento de Requerimientos del Producto (PRD) que describe la funcionalidad y características del sistema.
- `/docs/DOMAIN.md`: Documento de Dominio que define los conceptos clave y relaciones del sistema. E/R con reglas de negocio.
> Dominio no se refiere a Domain Drive Design (DDD), sino conceptos claves y relaciones del sistema eg. model ER, con algunas reglas y restricciones
- `github.com/issues`: Issues de GitHub que describen tareas y funcionalidades específicas a implementar, y sus estados (open, closed, in progress).
>El detalle de las funcionalidades podriamos decir que nos la grave como un fichero (la carpeta `/docs`), pero cuando tengas muchas funcionalidades (75,100...) la carpeta va ser un caos.
> El detalle de las funcionalidades la podemos namejar en otro sistema aparte, no el indice (el indice esta en el `PRD.md`). Eg. gira, issues de github.

## Builder

### Input:

- `.ai/builder/feature-plan.instructions.md`: Instrucciones para planificar la implementación de una feature.
- `.ai/builder/feature-plan.template.md`: Plantilla con la estructura de un plan de implementación de feature.
- `.ai/builder/implementation.instructions.md`: Instrucciones para implementar un plan de una feature (es un prompt).
- `.ai/builder/rules`: Reglas técnicas de escritura y estilo de código.
> puede que segun tu editor/IDE esten fisicamente en otro sitio.

### Output:

- `docs/feature.plan.md`: Documento de Planificación de implementación de **una** funcionalidad.
> Los planes los puedes borrar si quieres, o sino lo guardas como referencia
- `src/test`:  Código fuente del sistema, organizado por capas y funcionalidades.

## Craftsman

### Input:

- `.ai/craftsman/test.instructions.md`: Instrucciones para implementar tests de una feature.
- `.ai/craftsman/document.instructions.md`: Instrucciones documentar el código fuente de **una** feature.
- `.ai/craftsman/rules`: Reglas técnicas de escritura y estilo de pruebas[Opcional]

### Output:

- `src/test`:  Tests unitarios y de integración para el sistema, organizados por funcionalidades.
- `/docs/STRUCTURE.md`: Documento de Estructura que describe la arquitectura del sistema, incluyendo patrones de diseño y organización de carpetas.

---
### Aplicacion Full Stack

- Hay una parte que habría que repetir para cada capa por que las reglas del frontend y del backend son diferentes.
> - No pediria un plan de implementacion para todo
> - No pediria que programe el front y el back a la vez
- Dividimos el Desarrollo en trozos(Funciones pequeñas) pequeños y en Faces(Front, Back, DB,...).
