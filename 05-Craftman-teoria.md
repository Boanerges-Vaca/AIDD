
## Builder
 - Pensar (Plan).
 - Actuar

**Chat**
```
Genera un plan de Implementacion del cambio.
Usa `#file:2_operaciones_trading.plan.md` como  ejemplo de lo que debes generar.
No generes Codigo solo el plan.
```
> Primero pensamos (plan), luego ejecutamos. se puede usar modelos diferentes. eg. planificar(codex), ejecucion (gemini)

genera 2b.plan.md

**Chat**
```
 Implementa el plan 2b.plan.md
```

**En el builder**
- fichero de instrucciones
- plantilla de plan

---

## Craftman.
Craftman es alguien que mantiene lo que ya crearon.
>por ampliacion, mejora, arreglo.

Por un **software mantenible**
- Testing 
- Documentacion

### Test
Testing suele ser una programacion mucho mas acotada por tanto no se suelo pidir que haga un plan.
en caso de que nesecites puede hacerlo como hicimos en builder (plan y plantilla)

**Testear la logica de Crear Porfolio**

**Chat**.
>Genera pruebas para `porfolio.logic.ts` en la carpeta  `src/test` siguiendo las instrucciones `c-1.test.instructions.md` 

### Documentacion

5 Fases de una funcionalidad (Parte del Flujo de una Ejecucion):
1. Definicion.
2. Planificacion.
3. Implmentacion.
4. Testeo 
5. Documentacion.

- En un mundo Ideal la capeta `.ai` deberia valer para cualquier proyecto en cualquier tecnologia, pero ...

- Dicho lo anterior, la capeta `/architect` si vale para cualquier proyecto en cualquier tecnologia.

- La Carpeta `/Builder` y `/craftman` deberia ajustarse al tipo de proyecto.
> la capeta `/rules`  es la que mas cambia

**Ejemplo Angular**
- [Construccion Con IA](https://angular.dev/ai).
- [LLM prompts and AI IDE setup](https://angular.dev/ai/develop-with-ai).
