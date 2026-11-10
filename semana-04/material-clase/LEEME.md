# 📎 Ejemplo de la clase · Semana 4
**Blog de Cocina Chilena: diagramado con flex y listo para publicar**

Es el estado final del [tutorial de la semana 4](../tutorial-codigo.md). Parte del blog de la semana 3 y le agrega reset, menú, modelo de cajas y diagramación.

> ⚠️ **No es tu entrega.** Úsalo para ver cómo queda cada paso y luego toma tus propias decisiones de diseño para **tu blog**.

## Cómo abrirlo

🌐 **Publicado en la web:** <https://abecerraguz.github.io/diseno-web-basico-001A/semana-04/material-clase/>

También puedes abrir `index.html` en el navegador (doble clic o *Open with Live Server* en VS Code). Navega usando **solo el menú**.

## Estructura

```
material-clase/
├── index.html
├── platos-de-fondo/
│   ├── charquican.html
│   └── bife-a-lo-pobre.html
├── postres/
│   ├── tiramisu.html
│   └── papayas-a-la-crema.html
└── assets/
    ├── css/style.css      ← una sola hoja para todo el sitio
    └── img/               ← fotos de los platos (imágenes de ejemplo)
```

> Las fotos de `assets/img/` son **ilustraciones de ejemplo**: una por receta y dos horizontales para las tarjetas del inicio (`platos-de-fondo.jpg` y `postres.jpg`). En tu blog usa tus propias fotos o imágenes con licencia libre.

## El layout con flex

```
┌──────────────────── .cabecera ─────────────────────┐
├──────────── .navegacion ul  (flex, fila) ──────────┤
│                                                    │
│  ┌──── .contenedor.disposicion (flex, fila) ────┐  │
│  │ ┌──── main.contenido ────┐ ┌─ aside.lateral ┐│  │
│  │ │ ┌─ .tarjetas (flex) ─┐ │ │                ││  │
│  │ │ │ .tarjeta │ .tarjeta│ │ │                ││  │
│  │ │ └────────────────────┘ │ │                ││  │
│  │ └────────────────────────┘ └────────────────┘│  │
│  └──────────────────────────────────────────────┘  │
├──── .pie-pagina .contenedor (flex, space-between) ─┤
└────────────────────────────────────────────────────┘
```

Hay **seis contenedores flex**. Todos siguen la misma regla: `display: flex` va en el **padre** y ordena a sus **hijos directos**.

| Contenedor | Hijos que ordena | Propiedades clave |
|---|---|---|
| `.navegacion ul` | los `<li>` del menú | `justify-content: center`, `gap`, `flex-wrap` |
| `.disposicion` | `main` y `aside` (dos columnas) | `flex: 3 1 560px` y `flex: 1 1 240px`, `align-items: flex-start` |
| `.tarjetas` | las dos `.tarjeta` | `flex: 1 1 240px`, `gap`, `flex-wrap` |
| `.tarjeta` | la imagen y `.tarjeta-cuerpo` | `flex-direction: column`, `overflow: hidden` |
| `.receta-pie` | los enlaces «Anterior» y «Siguiente» | `justify-content: space-between`, `margin-left: auto` |
| `.pie-pagina .contenedor` | los dos párrafos del pie | `justify-content: space-between` |

Achica la ventana: gracias a `flex-wrap: wrap`, la columna lateral baja debajo del contenido y las tarjetas quedan una sobre otra.

## Dónde está cada requisito de la sumativa

| La pauta pide… | En el ejemplo | Selector en `style.css` |
|---|---|---|
| Una hoja de estilo única | `assets/css/style.css`, con el reset al inicio | sección 0 |
| Estilos a los textos | tipografías, tamaños, interlineado | `body`, `h2`, `h3`, `.cabecera h1` |
| Vínculos con `:hover` | menú y enlaces del contenido | `.navegacion a:hover`, `.contenido a:hover` |
| Enlaces del menú distintos al resto | menú claro sin subrayado; contenido terracota subrayado | `.navegacion a` y `.contenido a` |
| Menú en todas las páginas | el mismo `<nav>` en las 5 páginas, con rutas ajustadas | — |
| Colores de fondo | cabecera, menú, contenido, tarjetas y pie | `.cabecera`, `.tarjeta`, `.lateral`… |
| `display: block` | enlaces de las tarjetas y del menú | `.tarjeta a`, `.navegacion a` |
| `display: inline` | datos de la receta en una sola línea | `.datos-receta li` |
| `float` | foto del plato rodeada de texto | `.foto-receta` (+ `clear` y `flow-root`) |
| Bordes | tarjetas, lateral, foto, separadores | `.tarjeta`, `.lateral`, `.receta-pie` |
| Selectores de clase y combinados | `.navegacion a`, `.navegacion .actual`, `.tarjeta h3`… | todo el archivo |

**Además (complemento de clase):** `display: flex` para el layout, `column-count` en los ingredientes y un ajuste con `@media` para celulares.

## Accesibilidad y contraste

- Cada imagen tiene un `alt` que describe el plato, también las de las tarjetas.
- El menú usa `<nav aria-label="Menú principal">` y marca la página actual con `aria-current="page"`.
- Contrastes medidos (WCAG AA exige 4,5:1): ver la tabla en el [tutorial](../tutorial-codigo.md), paso 12. Todas las combinaciones de texto superan 5,7:1.
