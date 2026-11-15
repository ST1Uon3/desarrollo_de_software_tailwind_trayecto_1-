# Semana 3
 ## Día 1 
 ### 1.1.5 
 Con bootstrap el botón ya salió con forma, color, espaciado y efecto hover sin escribir nada de CSS. El inconveniente apareció cuando quise un hover distinto (fondo blanco y texto rojo), bootstrap no lo ofrece como clase, así que tuve que escribir CSS propio y sobrescribir los estilos.

 Hoy con tailwind construí digamos que el mismo boton pero agregando clases pequeñas como bg-white, text-blue-800, y cada una con una sola función. En este caso el hover personalizado lo resolví directamente en .html sin tocar css

 #### Diferencias
  Bootstrap me da piezas ya diseñadas (btn, card, modal): son rápidas de usar, pero todas se ven parecidas y personalizarlas implica sobrescribir estilos. Tailwind me da clases pequeñas de una sola propiedad (px-6, bg-black, rounded-full) y puedo armar el diseño combinándolas, y aunque requiere escribir más clases, yo tengo control total y no necesito CSS aparte.