# Semana 4 — Aplicando el estilo a mi sitio
**Diseño Web Básico · EXP2 - Semana 4**
**Asignatura:** Diseño web básico · **Carrera:** Desarrollo y Diseño Web · DUOC UC

---

## En esta semana

| | |
|---|---|
| **Tema** | Aplicando el estilo a mi sitio |
| **Actividad** | **Sumativa individual:** *Estilando mi sitio* |
| **Clase sincrónica** | Martes 10 de noviembre, 21:00 hrs. (la grabación queda en el foro semanal) |
| **Entrega** | Lunes 16 de noviembre de 2026, 23:59 hrs., por AVA |

---

## Introducción a la semana

La semana pasada creaste tu hoja de estilos y le diste formato a los textos y fondos. Esta semana aprenderemos a **diagramar**: a ubicar los elementos en la página. Para eso veremos:

- cómo estilar los **enlaces** con **pseudoclases**, para que no se vean azules y subrayados;
- el **modelo de cajas**, base de toda la diagramación;
- el **reset** de CSS, para partir de un lienzo en blanco;
- técnicas para **disponer elementos**: sobre todo `display: flex`, y además `display` block e inline, `float` y columnas.

**Preguntas activadoras:**
- ¿Cómo hago que los enlaces no se vean azules y subrayados?
- ¿Cómo hago que un enlace cambie de color al pasar el mouse?
- ¿Cómo puedo disponer los elementos en la página?

**Conceptos clave:** pseudoclases · modelo de cajas · `box-sizing` · reset · `padding` · `margin`.

---

## 1. Pseudoclases

Se agregan al selector con dos puntos (`:`), todo junto y sin espacios. Le dan estilo a un elemento **según su estado**.

| Pseudoclase | Se aplica cuando… |
|-------------|-------------------|
| `:link` | el enlace aún no se visita |
| `:visited` | el enlace ya se visitó |
| `:hover` | pasas el mouse por encima (sin hacer clic) |
| `:active` | haces clic (dura muy poco) |

```css
a:hover {
  color: #6b4a2f;
}
```

> 💡 En `:hover` declara **solo lo que cambia**. El resto lo hereda de la regla del enlace.

---

## 2. Estilando enlaces y menús

1. **Modifica la etiqueta `<a>`**: es la que trae el azul y el subrayado.
2. **Quita el subrayado** con `text-decoration: none;` y define el color de tu diseño.
3. **Declara siempre `:hover`**, para que se entienda que se puede hacer clic.
4. **Si es un menú de navegación**, quítale las viñetas a la lista con `list-style: none;` (idealmente en el `<ul>`).

> ⚠️ Los enlaces del menú deben verse **distintos** a los enlaces del contenido. Diferéncialos con **clases** y **combinadores descendientes**, por ejemplo `.menu a { }` y `.contenido a { }`.

---

## 3. Modelo de cajas

Para CSS, **cada elemento es una caja rectangular**. Hay dos tipos de comportamiento:

- **Bloque (`block`):** ocupa todo el ancho y lo que sigue queda debajo. Ej.: `h1`, `p`, listas, `header`, `main`, `section`, `div`.
- **Línea (`inline`):** deja que otros elementos queden a su lado. Ej.: `a`, `strong`, `em`, `span`.

Cada caja tiene, de adentro hacia afuera:

```
┌──────────── margin (espacio exterior) ────────────┐
│ ┌────────── border (borde) ─────────────────────┐ │
│ │ ┌──────── padding (relleno) ────────────────┐ │ │
│ │ │          content (contenido)              │ │ │
│ │ └───────────────────────────────────────────┘ │ │
│ └───────────────────────────────────────────────┘ │
└───────────────────────────────────────────────────┘
```

**Ojo con las medidas:** `width` y `height` miden solo el contenido. El padding y el borde **se suman**. Una caja de `350px` con `25px` de padding y `5px` de borde por lado termina midiendo `410px` de ancho.

### `box-sizing: border-box`

Hace que la caja respete el ancho que declaraste, sin sumar padding ni borde. Se recomienda para todos los elementos:

```css
* {
  box-sizing: border-box;
}
```

---

## 4. Reset de CSS

Los navegadores traen estilos propios: márgenes, interlineados, títulos en negrita, enlaces azules. El **reset** los elimina para que partas de un lienzo en blanco.

- La guía recomienda el reset de Eric Meyer: <https://meyerweb.com/eric/tools/css/reset/reset.css>
- Puedes vincularlo en el `<head>` **antes** de tu hoja, o pegar su contenido **al inicio** de tu `style.css`.

> ⚠️ El reset siempre va **primero**. El navegador se queda con lo último que lee: si va después, borra tus estilos.

---

## 5. Lados, `padding`, `border` y `margin`

Toda caja tiene 4 lados: `top`, `right`, `bottom` y `left`. Con un solo valor se aplica a todos; con varios, se leen **en el sentido del reloj**, partiendo por arriba.

```css
.tarjeta {
  padding: 20px;               /* los 4 lados iguales */
  padding: 10px 20px;          /* arriba/abajo | derecha/izquierda */
  padding: 10px 20px 15px 5px; /* arriba | derecha | abajo | izquierda */
}
```

| Propiedad | Qué hace | Ejemplo |
|-----------|----------|---------|
| `padding` | Espacio **interior**, entre el contenido y el borde | `padding: 20px;` |
| `border` | Borde: grosor, estilo y color | `border: 5px solid #ffffff;` |
| `border-bottom` | Borde de un solo lado | `border-bottom: 2px dotted #a8512e;` |
| `margin` | Espacio **exterior**, entre la caja y lo que la rodea | `margin: 20px 0;` |

Estilos de borde: `solid`, `dashed`, `dotted`, `double`, `groove`, `ridge`, `inset`, `outset`.

---

## 6. Diagramar con `display: flex` ⭐

Diagramar es decidir **dónde va cada elemento**. Hoy la herramienta principal para eso es **flexbox**. Acordamos usarla en el curso porque es como se diagrama en la industria. La guía oficial no la incluye: es un complemento de clase.

> 🧪 **Guía visual interactiva:** abre [`material-semana/flexbox-guia-visual.html`](./material-semana/flexbox-guia-visual.html) en el navegador y mueve los controles.
> 📎 **Ejemplo de la clase:** [`material-clase/`](./material-clase/LEEME.md) tiene el Blog de Cocina diagramado completo con flex.

### Flex en 3 ideas

1. **Va en el padre.** `display: flex` se escribe en el **contenedor**.
2. **Ordena a los hijos directos.** Solo se mueven los hijos inmediatos; los nietos se comportan como siempre.
3. **Trabaja sobre dos ejes.** `justify-content` alinea en el **eje principal** y `align-items`, en el **eje cruzado**.

```
flex-direction: row  (por defecto)

  eje cruzado ↓  ┌──────────── contenedor ────────────┐
  align-items    │ ┌──────┐ ┌──────┐ ┌──────┐         │
                 │ │hijo 1│ │hijo 2│ │hijo 3│         │
                 │ └──────┘ └──────┘ └──────┘         │
                 └────────────────────────────────────┘
                   eje principal → justify-content
```

Con `flex-direction: column` los ejes se **intercambian**: `justify-content` pasa a alinear en vertical.

### Propiedades del contenedor

| Propiedad | Para qué sirve | Valores frecuentes |
|-----------|----------------|--------------------|
| `display` | Activa flex | `flex` |
| `flex-direction` | Dirección del eje principal | `row` (por defecto), `column` |
| `justify-content` | Alinear en el eje principal | `flex-start`, `center`, `flex-end`, `space-between` |
| `align-items` | Alinear en el eje cruzado | `stretch` (por defecto), `flex-start`, `center` |
| `flex-wrap` | Permitir que los hijos bajen de línea | `nowrap` (por defecto), `wrap` |
| `gap` | Espacio **entre** hijos | `16px`, `1rem` |

### Propiedad de los hijos: `flex`

```css
.tarjeta {
  flex: 1 1 240px;   /* crece | se encoge | ancho base */
}
```

Cada hijo parte con un ancho base de `240px`, crece para llenar la fila y, si no cabe, baja a la siguiente línea (con `flex-wrap: wrap` en el padre). Si un hijo tiene `flex: 3 …` y otro `flex: 1 …`, el primero crece tres veces más.

### Los patrones del Blog de Cocina

| Patrón | Contenedor | Código clave |
|--------|-----------|--------------|
| Menú en una fila | `.navegacion ul` | `display: flex; justify-content: center; gap: 8px;` |
| Contenido + columna lateral | `.disposicion` | hijos con `flex: 3 1 560px` y `flex: 1 1 240px` |
| Tarjetas que se acomodan | `.tarjetas` | `flex-wrap: wrap;` y `.tarjeta { flex: 1 1 240px; }` |
| Un elemento en cada extremo | `.pie-pagina .contenedor` | `justify-content: space-between;` |
| Empujar un elemento a la derecha | `.receta-pie` | `.siguiente { margin-left: auto; }` |

```css
/* Centrar el sitio y diagramar en dos columnas */
.contenedor {
  max-width: 1100px;
  margin: 0 auto;            /* auto a los lados = centrado */
  padding: 0 16px;
}

.disposicion {
  display: flex;
  flex-wrap: wrap;           /* en el celular, el aside baja */
  align-items: flex-start;
  gap: 24px;
}

.contenido { flex: 3 1 560px; }
.lateral   { flex: 1 1 240px; }
```

> ⚠️ **Errores típicos:** poner `display: flex` en los hijos en vez del padre; olvidar `flex-wrap: wrap` (los elementos se aprietan en el celular); separar con `margin` **y** `gap` a la vez (el espacio se duplica).

---

## 7. `display` block e inline, `float` y columnas

La pauta de la sumativa pide **mostrar elementos con `display` block, inline y `float`**. Úsalos para lo que sirven y deja el layout a flex.

### `display`: cambiar cómo se muestra un elemento

```css
.tarjeta a       { display: block; }   /* línea → bloque: cada enlace en su propia línea */
.datos-receta li { display: inline; }  /* bloque → línea: los datos quedan en una fila */
```

> 💡 Los elementos `inline` ignoran `width` y `height`. Si necesitas medidas, usa `block` o un contenedor flex.

### `float`: una imagen rodeada de texto

`float` se creó para que el texto **rodee** a un elemento, como en una revista. Ese es su uso correcto hoy.

```css
.foto-receta {
  float: left;               /* left | right | none */
  margin: 4px 20px 12px 0;
}

.receta h3 {
  clear: both;               /* el subtítulo empieza debajo de la imagen */
}

.receta {
  display: flow-root;        /* la caja contiene a la imagen flotada */
}
```

> 📌 Un `float` bien aplicado a la foto de una receta cumple el requisito de la pauta. No uses `float` para armar columnas o menús: para eso está flex.

### Múltiples columnas

```css
.ingredientes {
  column-count: 2;              /* número de columnas */
  column-gap: 32px;             /* separación */
  column-rule: 1px solid #ccc;  /* línea divisoria (opcional) */
}
.articulo h2 { column-span: all; }  /* un título que cruza todas las columnas */
```

### ¿flex o float?

| Quiero… | Uso |
|---------|-----|
| Menú, columnas, tarjetas, pie de página | `display: flex` |
| Que el texto rodee una imagen | `float` (+ `clear` y `flow-root`) |
| Datos cortos en una sola línea | `display: inline` |
| Que un enlace ocupe su propia línea | `display: block` |
| Repartir una lista o un texto largo en columnas | `column-count` |

---

## 8. Antes de diseñar


- **Prueba en más de un navegador** (Chrome, Firefox, Edge o Safari).
- **Guarda** antes de recargar: el navegador muestra la última versión guardada.
- Si no ves tus cambios, **borra la caché** o recarga forzando (`Ctrl + F5`, o `Cmd + Shift + R` en Mac).

---

## Actividad sumativa individual: *Estilando mi sitio*

Le darás estilo a tu blog y lo publicarás en el servidor, para que se pueda ver desde cualquier lugar con su URL.

**1. Crea una hoja de estilo única para tu sitio** y aplica en ella:
- estilos a los textos;
- estilos a los vínculos, incluyendo la pseudoclase `:hover`;
- colores de fondo;
- elementos mostrados con `display` block, inline y `float`;
- bordes;
- selectores de clase y combinados.

**2. Considera además que:**
- debe haber una sola hoja de estilos para todo el sitio;
- el menú de navegación debe estar en **todas** las páginas;
- los enlaces del menú deben verse **distintos** a los enlaces de otras áreas del sitio.

**3. Publica tu sitio:** configura el hosting de Duoc con los datos que entrega el AVA y sube el sitio.

### 📤 Formato de entrega

Entrega por AVA:
- el **link (URL)** de tu sitio publicado;
- la carpeta del sitio comprimida en **.zip**.

Plazo: **lunes 16 de noviembre de 2026, 23:59 hrs.**

### 📋 ¿Cómo se evalúa? Rúbrica de 9 criterios (100 puntos)

| # | Criterio | Puntaje máximo |
|---|----------|:--------------:|
| 1 | Carpeta raíz con la nomenclatura y estructura de archivos del estándar | 11 |
| 2 | Archivos HTML con nomenclatura y estructura según el estándar W3C | 11 |
| 3 | Código HTML con sintaxis estándar, buenas prácticas, indentación y comentarios | 11 |
| 4 | Etiquetas de seccionamiento, texto, medios y formulario, con criterios de accesibilidad | 10 |
| 5 | Archivos estructurados y vinculados para que el sitio se pueda navegar | 13 |
| 6 | Sitio publicado en el servidor remoto y funcionando | 11 |
| 7 | Archivo CSS con buena nomenclatura y vinculación | 11 |
| 8 | Código CSS con buena sintaxis, considerando herencias y tipos de selectores | 11 |
| 9 | Reglas CSS para diagramar el layout según el requerimiento visual | 11 |

Cada criterio tiene cinco niveles: Completamente logrado, Logrado (errores hasta un 20%), Medianamente logrado (hasta un 40%), Logro insuficiente y No logrado.

> 💡 Dos de cada tres puntos (67 de 100) están en la estructura, el HTML, la navegación y la publicación. Revisa que **todos los enlaces funcionen** y que el sitio se vea **en la URL publicada**, no solo en tu computador.

---

## Recursos de referencia

- [MDN — El modelo de caja](https://developer.mozilla.org/es/docs/Learn/CSS/Building_blocks/The_box_model)
- [MDN — Flexbox](https://developer.mozilla.org/es/docs/Learn/CSS/CSS_layout/Flexbox)
- [Flexbox Froggy](https://flexboxfroggy.com/#es) — juego en español para practicar flex
- [MDN — Floats](https://developer.mozilla.org/es/docs/Learn/CSS/CSS_layout/Floats)
- [W3Schools — CSS Box Sizing](https://www.w3schools.com/css/css3_box-sizing.asp)
- [W3Schools — CSS Border](https://www.w3schools.com/css/css_border.asp)
- [W3Schools — CSS Multiple Columns](https://www.w3schools.com/css/css3_multiple_columns.asp)
- [Reset de Eric Meyer](https://meyerweb.com/eric/tools/css/reset/reset.css)

---

*Diseño Web Básico · EXP2 Semana 4 · Campus Virtual DUOC UC*
*Facilitador disciplinar: Jimena Jamett · Asesor par: Max Villalobos*
