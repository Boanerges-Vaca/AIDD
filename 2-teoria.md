
Rama s2...
Antes de Codificar, hay que generar un monton de documentacion.

## Arquitectura 

- Que es lo que voy a hacer (Arquitectura y analisis)
- dos o tres documentos mas n funcionalidades

Documentos:
- PR o PRD (Proyect Requeriments - Documento de Requerimientos del proyecto) -- en el ejercicio anterio estaba incrustado dentro del arquitecto
- Dominio - Documento de dominio que va mas alla de las entidades
  -- Entidades, relaciones, reglas de dominio, 
- Documento de los sistemas que vamos a incorporar
  eg. solo API, API + Web... si es con multiples proyectos
- N... los n son uno por cada funcionalidad Core.

---
para generar estos documentos no tienes que escribirlos a mano.
por tanto vamos a crear plantillas con sintaxis que te permitan crear PRD´s y cualquier otra cosa.

podriamos crear un documento que explique la plantilla.
`syntax.template.md`

Las plantillas PRD, Domain, features., sistema[Opcional] van a estar asociadas al `Agent Architect`

En el **builder** vamos a tener muchas plantillas
 - planificacion, contenedor, db

En el **Craftsman**
- especificar las pruebas.
- planificar la documentacion.

#### Capetas para guardar los mds
>cada editor tiene su forma.

Nosotros usaremos:
- independiente del editor y mas generico.
- carpeta .ai (al empezar con punto quiere decir que no es codigo)
- valido para cualquier proyecto en cualquier tecnologia
 
Dentro de:
- .ai-> architect.
- *.template.md -> 

Los Containers de la plantilla no son Containers de dockers o kubernetes,
es nomenclatura estandar de arquietectura de software donde los elementos despleglabes se les llama containers.
si no te gusta la cambias.
que es un contenedor?. es un despleglabe. (CLI, API, Angular, etc  )

---

### chat

```
**Chat**
usa esta plantilla para generar un fichero en esta carpeta.
```
>Pero cuando el Prompt es muy largo, combiene tenerlo en un archivo aparte
estos son los **.instructions.md (podrian ser **.prompts.md).
>`instructions = promts`

// a-1 -> viene de arquitect. (a-1, a-2... a-n)

```
**chat**
- sigue las instrucciones de @a-1.prd.instru.md para mi proyecto AssestsBoard
ejecucion 1
```

---
falta un documento de sistemas. podriamos hacerlo en architect o en builder.
dependiendo que vas ha hacer (multiples proyectos).

