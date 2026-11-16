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

