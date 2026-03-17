---
description: Esta regla proporciona mejores prácticas integrales y estándares de codificación para el desarrollo de Angular, enfocándose en TypeScript moderno, componentes standalone, signals y optimizaciones de rendimiento.
globs: ["**/*.{ts,html,scss,css}"]
---

# Mejores Prácticas de Angular

Este proyecto adheres to modern Angular best practices, emphasizing maintainability, performance, accessibility, and scalability.

Este proyecto sigue las mejores prácticas modernas de Angular, enfatizando mantenibilidad, rendimiento, accesibilidad y escalabilidad.

## Mejores Prácticas de TypeScript

* **Verificación de Tipos Estricta:** Siempre habilita y adhere a la verificación de tipos estricta. Esto ayuda a detectar errores tempranamente y mejora la calidad del código.
* **Prefiere Inferencia de Tipos:** Permite que TypeScript infiera los tipos cuando son obvios del contexto. Esto reduce la verbosidad mientras mantiene la seguridad de tipos.
    * **Incorrecto:**
        ```typescript
        let name: string = 'Angular';
        ```
    * **Correcto:**
        ```typescript
        let name = 'Angular';
        ```
* **Evita `any`:** No uses el tipo `any` a menos que sea absolutamente necesario, ya que evade la verificación de tipos. Prefiere `unknown` cuando un tipo es incierto y necesitas manejarlo de forma segura.

## Mejores Prácticas de Angular

* **Componentes Standalone:** Siempre usa componentes standalone, directivas y pipes. Evita usar `NgModules` para nuevas funcionalidades o refactorizar los existentes.
* **Standalone Implícito:** Al crear componentes standalone, no necesitas establecer explícitamente `standalone: true` dentro de los decoradores `@Component`, `@Directive` y `@Pipe`, ya que está implícito por defecto.
    * **Incorrecto:**
        ```typescript
        @Component({
          standalone: true,
          // ...
        })
        export class MyComponent {}
        ```
    * **Correcto:**
        ```typescript
        @Component({
          // `standalone: true` está implícito
          // ...
        })
        export class MyComponent {}
        ```
* **Signals para Gestión de Estado:** Utiliza Angular Signals para la gestión de estado reactivo dentro de componentes y servicios.
* **Carga Diferida:** Implementa carga diferida para rutas de características para mejorar los tiempos de carga inicial de tu aplicación.
* **NgOptimizedImage:** Usa `NgOptimizedImage` para todas las imágenes estáticas para optimizar automáticamente la carga de imágenes y el rendimiento.
* **Host bindings:** NO uses los decoradores `@HostBinding` y `@HostListener`. En su lugar, coloca los enlaces del host dentro del objeto `host` del decorador `@Component` o `@Directive`.

## Componentes

* **Responsabilidad Única:** Mantén los componentes pequeños, enfocados y responsables de una única funcionalidad.
* **Funciones `input()` y `output()`:** Prefiere las funciones `input()` y `output()` sobre los decoradores `@Input()` y `@Output()` para definir las entradas y salidas de los componentes.
    * **Sintaxis Antigua con Decoradores:**
        ```typescript
        @Input() userId!: string;
        @Output() userSelected = new EventEmitter<string>();
        ```
    * **Nueva Sintaxis con Funciones:**
        ```typescript
        import { input, output } from '@angular/core';

        // ...
        userId = input<string>('');
        userSelected = output<string>();
        ```
* **`computed()` para Estado Derivado:** Usa la función `computed()` de `@angular/core` para el estado derivado basado en signals.
* **`ChangeDetectionStrategy.OnPush`:** Siempre establece `changeDetection: ChangeDetectionStrategy.OnPush` en el decorador `@Component` para beneficios de rendimiento al reducir los ciclos innecesarios de detección de cambios.
* **Plantillas en Línea:** Prefiere plantillas en línea (template: `...`) para componentes pequeños para mantener el código relacionado junto. Para plantillas más grandes, usa archivos HTML externos.
* **Formularios Reactivos:** Prefiere formularios reactivos sobre los formularios basados en plantillas para formularios complejos, validación y controles dinámicos debido a su naturaleza explícita, inmutable y síncrona.
* **No `ngClass` / `NgClass`:** No uses la directiva `ngClass`. En su lugar, usa enlaces nativos de `class` para estilos condicionales.
    * **Incorrecto:**
        ```html
        <section [ngClass]="{'active': isActive}"></section>
        ```
    * **Correcto:**
        ```html
        <section [class.active]="isActive"></section>
        <section [class]="{'active': isActive}"></section>
        <section [class]="myClasses"></section>
        ```
* **No `ngStyle` / `NgStyle`:** No uses la directiva `ngStyle`. En su lugar, usa enlaces nativos de `style` para estilos en línea condicionales.
    * **Incorrecto:**
        ```html
        <section [ngStyle]="{'font-size': fontSize + 'px'}"></section>
        ```
    * **Correcto:**
        ```html
        <section [style.font-size.px]="fontSize"></section>
        <section [style]="myStyles"></section>
        ```

## Gestión del Estado

* **Signals para Estado Local:** Usa signals para gestionar el estado local del componente.
* **`computed()` para Estado Derivado:** Utiliza `computed()` para cualquier estado que pueda derivarse de otros signals.
* **Transformaciones Puras y Predecibles:** Asegúrate de que las transformaciones de estado sean funciones puras (sin efectos secundarios) y predecibles.
* **Actualizaciones de Valor de Signals:** NO uses `mutate` en signals, usa `update` o `set` en su lugar.

## Plantillas

* **Plantillas Simples:** Mantén las plantillas lo más simples posible, evitando lógica compleja directamente en la plantilla. Delega la lógica compleja al código TypeScript del componente.
* **Flujo de Control Nativo:** Usa la nueva sintaxis de flujo de control incorporada (`@if`, `@for`, `@switch`) en lugar de las directivas estructurales antiguas (`*ngIf`, `*ngFor`, `*ngSwitch`).
    * **Sintaxis Antigua:**
        ```html
        <section *ngIf="isVisible">Content</section>
        <section *ngFor="let item of items">{{ item }}</section>
        ```
    * **Nueva Sintaxis:**
        ```html
        @if (isVisible) {
          <section>Content</section>
        }
        @for (item of items; track item.id) {
          <section>{{ item }}</section>
        }
        ```
* **Pipe Async:** Usa el pipe `async` para manejar observables en las plantillas. Esto se subscribe y desubscribe automáticamente, previniendo fugas de memoria.

## Servicios

* **Responsabilidad Única:** Diseña servicios alrededor de una única responsabilidad bien definida.
* **`providedIn: 'root'`:** Usa la opción `providedIn: 'root'` al declarar servicios inyectables para asegurarte de que sean singletons y tree-shakeables.
* **Función `inject()`:** Prefiere la función `inject()` sobre la inyección en el constructor al inyectar dependencias, especialmente dentro de funciones `provide`, propiedades `computed`, o fuera del contexto del constructor.
    * **Inyección Antigua en Constructor:**
        ```typescript
        constructor(private myService: MyService) {}
        ```
    * **Nueva Función `inject()`:**
        ```typescript
        import { inject } from '@angular/core';

        export class MyComponent {
          private myService = inject(MyService);
          // ...
        }
        ```
