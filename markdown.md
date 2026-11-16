# Semana 3
 ## Bitácora Día 1 
 ### 1.1.5 
 Con bootstrap el botón ya salió con forma, color, espaciado y efecto hover sin escribir nada de CSS. El inconveniente apareció cuando quise un hover distinto (fondo blanco y texto rojo), bootstrap no lo ofrece como clase, así que tuve que escribir CSS propio y sobrescribir los estilos.

 Hoy con tailwind construí digamos que el mismo boton pero agregando clases pequeñas como bg-white, text-blue-800, y cada una con una sola función. En este caso el hover personalizado lo resolví directamente en .html sin tocar css

 #### Diferencias
  Bootstrap me da piezas ya diseñadas (btn, card, modal): son rápidas de usar, pero todas se ven parecidas y personalizarlas implica sobrescribir estilos. Tailwind me da clases pequeñas de una sola propiedad (px-6, bg-black, rounded-full) y puedo armar el diseño combinándolas, y aunque requiere escribir más clases, yo tengo control total y no necesito CSS aparte.

  ### 1.2.3 

  clase usada (azul)

Abrí `src/output.css` y busqué con `Ctrl + F` la clase **`bg-blue-900`**, que
uso en el `<body>` de mi `prototipo.html`.

- Tailwind generó algo como:

```css
.bg-blue-900 {
  background-color: var(--color-blue-900);
}
```

 clase no usada (verde)

Busqué la clase **`bg-verde-500`**, que no escribí en ningún archivo.

- Resultado: no aparece en `output.css`.

### 1.4.4

#### Reglas del kit

Definí reglas fijas para que todos los componentes se vean como parte del mismo kit.

### Radios de borde
- `rounded-lg`: alertas y campos de formulario.
- `rounded-2xl`: carta y formulario.
- `rounded-full`: botones, etiquetas y datos destacados.

### Escala de espaciado
Solo uso los valores 1, 2, 4, 6 y 8 de la escala de Tailwind.

| Componente | Espaciado |
|---|---|
| Botón | `px-6 py-2` |
| Etiqueta y datos destacados | `px-3 py-1` |
| Campo de formulario | `px-3 py-2` |
| Carta, formulario y alertas | `p-4` |
| Separación entre componentes | `gap-4` |
| Separación entre secciones | `mt-8` |

### Colores
- Fondo de la página: `bg-blue-950`.
- Superficies (carta y formulario): `bg-slate-800` con `border-2 border-white`.
- Botón principal: `bg-green-500 text-white`, con hover `bg-white text-green-500`.
- Datos destacados: `bg-white text-blue-800`.
- Anillo de foco: `ring-4 ring-pink-300` en todo lo interactivo.
- Alertas: fondo `*-100`, borde `*-500` y texto `*-800`.

### Qué apliqué
- Cambié los datos destacados de `rounded` a `rounded-full`.
- Unifiqué los dos botones "Inscríbete" (el de arriba era blanco y sin foco).
- Le di a la carta `rounded-2xl` y una imagen de alto uniforme (`h-48`).
- Cambié el formulario de `bg-blue-600` a `bg-slate-800` con borde blanco,
  igual que la carta.
- Reemplacé márgenes como `mt-15`, `mb-5` y `gap-5` por valores de la escala.

### Por qué
Con reglas fijas, cada componente nuevo se arma eligiendo entre pocas
opciones, y el diseño se mantiene consistente en toda la página.


 ## Bitácora Día 2
 ### 2.5.4 
 #### cards con grid o flex, como funcionan?
 envolví las 3 cartas en un `grid` que convierte el contenedor en una cuadrícula, haciendo que sus hijos directos (las tarjetas) se acomoden automáticamente dentro de celdas. con su respectivo responsive de en sm `grid-cols-2` y en lg `grid-cols-3` con un espaciado(gap) de 
 6; a los hijos les apliqué `flex` y `flex-col` para su contenido.

 ### 2.6.5
 | Sección / Elemento | Comportamiento anterior (360 px) | Problema detectado | Solución aplicada (Mobile-First) | Estado |
| --- | --- | --- | --- | --- |
| **Encabezado (`<header>`)** | Logo + 3 botones en fila con `justify-between` y `flex-wrap`. | El ancho total superaba los `328 px` útiles, provocando un salto de línea desordenado hacia la izquierda y saturación visual. | Apilado vertical centrado en celular (`flex-col items-center`) y en fila desde `768 px` (`md:flex-row md:justify-between`). Se ocultaron enlaces secundarios en móvil (`hidden md:block`) dejando visible **Inscríbete**. | Corregido |
| **Logo (`<img>`)** | Uso de `translate-x` sin valor numérico y fondo oscuro en el contenedor. | El ícono quedaba descentrado horizontal y verticalmente dentro del círculo. | Ajuste con `translate-x-1 translate-y-3 scale-150`. | Corregido |
| **Hero / Inicio (`#inicio`)** | Título con `text-4xl` y subtítulo con `text-2xl` fijos. | Textos demasiado grandes para `360 px` con saltos de línea bruscos y sin escala progresiva en escritorio. | Escala tipográfica por breakpoint: `text-3xl sm:text-4xl lg:text-5xl` en `<h1>` y `text-lg sm:text-xl lg:text-2xl` en subtítulo. | Corregido |
| **Catálogo de Rutas (`#rutas`)** | Grilla con `sm:grid-cols-2 lg:grid-cols-3` sin definición explícita de 1 columna base y botones desalineados en altura. | Falta de control explícito en base y desnivel en la posición inferior de los botones según el largo del texto. | Definición explícita `grid-cols-1 sm:grid-cols-2 lg:grid-cols-3` y tarjetas con `flex flex-col` + `mt-auto` en el contenedor del botón. | Corregido |
| **Sección Pasos (`#pasos`)** | No existía en la estructura inicial. | Ausencia de flujo paso a paso adaptable a distintos tamaños de pantalla. | Implementación de grilla responsiva: `grid-cols-1` (celular), `sm:grid-cols-2` (tablet) y `lg:grid-cols-4` (escritorio). | Corregido |
| **Alertas (`#alertas` / `#avisos`)** | Contenedor `max-w-xl mx-auto` sin relleno horizontal (`px-4`). | A `360 px`, las cajas de alerta quedaban pegadas directamente a los bordes laterales de la pantalla. | Incorporación de `px-4` en el contenedor y ajuste de tamaños de texto (`text-sm sm:text-base`). | Corregido |
| **Formulario (`#formulario` / `#inscripcion`)** | `<form>` con `max-w-md mx-auto` sin margen lateral, sin botón de envío y con `id` distinto a los enlaces `#inscripcion`. | El borde blanco tocaba los extremos del viewport en móvil y los enlaces de navegación no llevaban al formulario. | Contenedor padre con `px-4`, vinculación con `id="inscripcion"`, ajuste de ancho (`w-full`) en inputs y adición de botón `submit`. | Corregido |

