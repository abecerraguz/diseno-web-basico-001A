# Tutorial · Semana 4 — Diagramar con flex y publicar mi sitio
**Diseño Web Básico · EXP2 - Semana 4**

> 🎯 **Qué vas a lograr:** resetear los estilos del navegador, estilar un menú con `:hover`, entender el modelo de cajas y **diagramar la página con `display: flex`**: menú en fila, contenido y columna lateral, tarjetas y pie de página. Además, usarás `display` block e inline, `float` y columnas, como pide la pauta. Al final, publicarás el sitio.
>
> 🍲 **Proyecto de práctica:** seguimos con el **Blog de Cocina Chilena**, tal como quedó al terminar la semana 3. **No es tu entrega**: practica aquí y luego toma tus propias decisiones de diseño para **tu blog**.
>
> 📎 **Ejemplo de la clase:** el resultado final de este tutorial está en [`material-clase/`](./material-clase/LEEME.md). Úsalo para comparar cuando algo no te resulte.
> 🧪 **Guía visual de flexbox:** abre [`material-semana/flexbox-guia-visual.html`](./material-semana/flexbox-guia-visual.html) y juega con las propiedades antes de los pasos 4, 6 y 7.

**Herramientas:** VS Code y un navegador con herramientas de desarrollo (`F12`, o `Cmd + Opción + I` en Mac).
**Tiempo estimado:** 2 a 2,5 horas.

**El layout que vamos a construir:**

```
┌──────────────────── .cabecera ─────────────────────┐
├──────────── .navegacion ul  (flex, fila) ──────────┤  ← pasos 2, 3 y 4
│  ┌──── .contenedor.disposicion (flex, fila) ────┐  │  ← paso 6
│  │ ┌──── main.contenido ────┐ ┌─ aside.lateral ┐│  │
│  │ │ ┌─ .tarjetas (flex) ─┐ │ │                ││  │  ← paso 7
│  │ │ │ .tarjeta │ .tarjeta│ │ │                ││  │
│  │ │ └────────────────────┘ │ │                ││  │
│  │ └────────────────────────┘ └────────────────┘│  │
│  └──────────────────────────────────────────────┘  │
├──── .pie-pagina .contenedor (flex, space-between) ─┤  ← paso 8
└────────────────────────────────────────────────────┘
```

---

## Paso 1 · Reset y `box-sizing` al inicio de la hoja

**Meta:** partir de un lienzo en blanco y controlar el tamaño de las cajas.

**Haz esto:**
1. Abre el reset de Eric Meyer: <https://meyerweb.com/eric/tools/css/reset/reset.css>.
2. Copia su contenido y pégalo **al comienzo** de `assets/css/style.css`, antes de todas tus reglas. Así sigues teniendo **una sola hoja de estilos**.
3. Justo después del reset, agrega:
   ```css
   * {
     box-sizing: border-box;
   }
   ```
4. El reset deja el interlineado en `1` y quita la negrita. Devuélvelos en tu `body` y en `strong`:
   ```css
   body {
     line-height: 1.6;
   }

   strong {
     font-weight: bold;
   }
   ```
5. Guarda y recarga.

**Comprueba:** se perdieron los márgenes, las viñetas y los números de las listas. Tus colores y tipografías siguen funcionando.

**Errores frecuentes:**
- Pegar el reset **al final** de la hoja: borra tus propios estilos, porque el navegador se queda con lo último que lee.
- Crear un segundo archivo CSS para el reset y olvidar vincularlo **antes** de `style.css`. Además, la pauta pide una sola hoja.
- Asustarse porque las listas quedaron sin viñetas y los títulos sin tamaño: es justamente lo que hace el reset. Ahora tú decides cómo se ven (las viñetas vuelven en el paso 10).

---

## Paso 2 · El menú como lista, igual en las 5 páginas

**Meta:** tener un menú de navegación bien estructurado, presente en **todas** las páginas.

**Haz esto:**
1. En el demo, el menú era un párrafo con barras `|`. Reemplázalo por una lista dentro de `<nav>`:
   ```html
   <nav class="navegacion" aria-label="Menú principal">
     <ul>
       <li><a class="actual" href="index.html" aria-current="page">Inicio</a></li>
       <li><a href="platos-de-fondo/charquican.html">Charquicán</a></li>
       <li><a href="platos-de-fondo/bife-a-lo-pobre.html">Bife a lo pobre</a></li>
       <li><a href="postres/tiramisu.html">Tiramisú</a></li>
       <li><a href="postres/papayas-a-la-crema.html">Papayas a la crema</a></li>
     </ul>
   </nav>
   ```
2. Copia el mismo menú en las otras 4 páginas y **ajusta las rutas** según dónde esté cada una. Desde `platos-de-fondo/charquican.html`, por ejemplo, Inicio es `../index.html` y Tiramisú es `../postres/tiramisu.html`.
3. En cada página, mueve `class="actual"` y `aria-current="page"` al enlace de **esa** página. Así quien navega sabe dónde está, también con lector de pantalla.

**Comprueba:** desde **cada** página, haz clic en **cada** enlace del menú. Son 25 clics y ninguno debe llevar a un error 404.

**Errores frecuentes:**
- Copiar el menú de `index.html` tal cual en las subpáginas: las rutas quedan rotas.
- Dejar `class="actual"` siempre en «Inicio».

---

## Paso 3 · Enlaces del menú y del contenido con `:hover`

**Meta:** que los enlaces del menú se vean como menú, y **distintos** a los enlaces del contenido.

**Haz esto:**
1. Estila los enlaces **solo dentro del menú**, con un combinador:
   ```css
   .navegacion a {
     display: block;            /* toda el área es clickeable */
     color: #faf6ef;
     font-weight: bold;
     text-decoration: none;
     padding: 8px 14px;
     border-radius: 4px;
   }

   .navegacion a:hover {
     background-color: #4a3221;
     color: #ffffff;
   }

   .navegacion .actual {
     background-color: #faf6ef;
     color: #4a3221;
   }
   ```
2. Los enlaces del contenido llevan **otro** estilo, con su propio `:hover`:
   ```css
   .contenido a {
     color: #8f4426;
     text-decoration: underline;
   }

   .contenido a:hover {
     color: #4a3221;
     text-decoration: none;
   }
   ```

> 🎨 El terracota del contenido pasó de `#a8512e` a `#8f4426`: sobre el fondo crema de las tarjetas, el anterior no alcanzaba el contraste mínimo (paso 12).

**Comprueba:** al pasar el mouse por el menú cambia el fondo del enlace. Los enlaces dentro de las recetas se ven **distintos** a los del menú.

**Errores frecuentes:**
- Estilar `a { }` a secas: todos los enlaces del sitio terminan iguales.
- Escribir `.navegacion a :hover` con espacio antes de los dos puntos: así no funciona. Va todo junto, `a:hover`.
- En `:hover`, repetir todas las propiedades. Basta con declarar lo que cambia.

---

## Paso 4 · El menú en fila con `display: flex`

**Meta:** poner los enlaces del menú uno al lado del otro, y entender los dos ejes de flex.

**Haz esto:**
1. Aplica `flex` al **contenedor** de los enlaces, que es el `<ul>`:
   ```css
   .navegacion {
     background-color: #6b4a2f;
     padding: 10px 20px;
   }

   .navegacion ul {
     display: flex;             /* los <li> quedan en fila */
     flex-wrap: wrap;           /* si no caben, bajan a otra línea */
     justify-content: center;   /* eje principal (horizontal) */
     align-items: center;       /* eje cruzado (vertical) */
     gap: 8px;                  /* espacio entre los <li> */
   }
   ```
2. Prueba cambiar `justify-content` por `flex-start`, `flex-end` y `space-between`, y observa la diferencia.
3. Agrega `flex-direction: column;` y mira cómo cambian los ejes: ahora `justify-content` mueve en vertical. Bórralo al terminar.

**Comprueba:** los enlaces quedan en una fila centrada. Si achicas la ventana, los que no caben bajan a una segunda línea.

**Errores frecuentes:**
- Poner `display: flex` en los `<li>` o en los `<a>`: no pasa nada visible. `flex` se aplica al **padre** y ordena a sus hijos directos.
- Separar los enlaces con espacios o con `&nbsp;` en el HTML. Para eso está `gap`.

> 💡 La guía muestra el menú horizontal con `display: inline` en los `<li>`. Funciona, pero no permite alinear ni repartir el espacio. Con flex es más simple y predecible.

---

## Paso 5 · Modelo de cajas: `padding`, `border` y `margin`

**Meta:** entender y controlar el espacio dentro y fuera de una caja.

**Haz esto:**
1. Dale a las tarjetas del inicio relleno y bordes:
   ```css
   .tarjeta {
     background-color: #f3e9d8;
     padding: 20px;
     border: 1px solid #d9c6a5;
     border-top: 4px solid #a8512e;   /* borde de un solo lado */
     border-radius: 6px;
   }
   ```
2. Abre las herramientas de desarrollo (`F12`), selecciona una `.tarjeta` y mira el diagrama de cajas: content, padding, border y margin.

**Comprueba:** en el diagrama ves los valores que escribiste. Con `box-sizing: border-box` (paso 1), el ancho total de la caja **no crece** al sumar padding y borde.

**Errores frecuentes:**
- Confundir `padding` (adentro, toma el color de fondo de la caja) con `margin` (afuera, transparente).
- Olvidar el orden de los 4 valores: arriba, derecha, abajo, izquierda (en el sentido del reloj).
- Escribir el borde incompleto: `border: 1px #ccc` no se ve porque falta el **estilo** (`solid`, `dashed`…).

---

## Paso 6 · Diagramar la página: contenedor centrado y dos columnas

**Meta:** centrar el sitio y poner el contenido y una columna lateral **lado a lado** con flex.

**Haz esto:**
1. En `index.html`, envuelve el `<main>` en un `<div>` y agrega un `<aside>` después de él:
   ```html
   <div class="contenedor disposicion">

       <main class="contenido">
           … todo lo que ya tenías …
       </main>

       <aside class="lateral">
           <h2>Sobre este blog</h2>
           <p>Recetas caseras de la cocina chilena, probadas en familia y explicadas paso a paso.</p>
       </aside>

   </div>
   ```
2. Centra el sitio con un ancho máximo:
   ```css
   .contenedor {
     max-width: 1100px;
     margin: 0 auto;            /* auto a los lados = centrado */
     padding: 0 16px;
   }
   ```
3. Convierte `.disposicion` en un contenedor flex con dos hijos:
   ```css
   .disposicion {
     display: flex;
     flex-wrap: wrap;           /* en pantallas angostas, el aside baja */
     align-items: flex-start;   /* cada columna toma solo el alto que necesita */
     gap: 24px;
     margin-top: 24px;
     margin-bottom: 24px;
   }

   .contenido { flex: 3 1 560px; }   /* crece | se encoge | ancho base */
   .lateral   { flex: 1 1 240px; }
   ```
4. Dale a `.contenido` fondo blanco, `padding` y un borde, y a `.lateral` fondo crema y un `border-left` de color.
5. Repite el `<div>` y el `<aside>` en las otras 4 páginas.

**Comprueba:** en pantalla ancha ves dos columnas: la del contenido es unas tres veces más ancha que la lateral. Si achicas la ventana, la lateral baja debajo del contenido.

**Errores frecuentes:**
- Dejar el `<aside>` **fuera** del `<div class="disposicion">`: ya no es hijo directo y flex no lo ordena.
- Olvidar `flex-wrap: wrap`: en el celular las dos columnas quedan apretadísimas.
- Quitar `align-items: flex-start`: la lateral se estira hasta el alto del contenido (es el valor `stretch`, que viene por defecto).

---

## Paso 7 · Tarjetas lado a lado con flex

**Meta:** usar flex para un grupo de bloques que se acomodan solos.

**Haz esto:**
1. En `index.html`, envuelve las dos tarjetas en un contenedor. Aprovecha de cambiar los `<div class="tarjeta">` por `<section>` y de quitar las barras `|` entre los enlaces:
   ```html
   <div class="tarjetas">
       <section class="tarjeta">
           <h3>🍖 Platos de fondo</h3>
           <p>Recetas contundentes y llenas de sabor para compartir en familia.</p>
           <a href="platos-de-fondo/charquican.html">Ver charquicán →</a>
           <a href="platos-de-fondo/bife-a-lo-pobre.html">Ver bife a lo pobre →</a>
       </section>
       <section class="tarjeta"> … </section>
   </div>
   ```
2. Aplica `flex` al contenedor, y a cada tarjeta un ancho base:
   ```css
   .tarjetas {
     display: flex;
     flex-wrap: wrap;
     gap: 20px;
   }

   .tarjeta {
     flex: 1 1 240px;   /* crece, se encoge, ancho base 240px */
   }
   ```

**Comprueba:** en pantalla ancha las tarjetas quedan lado a lado y con el mismo ancho; en pantalla angosta, una debajo de otra.

**Errores frecuentes:**
- Aplicar `display: flex` a `.tarjeta` en vez de a `.tarjetas`.
- Dejar el `margin` lateral de las tarjetas y además el `gap`: se duplica el espacio.

---

## Paso 8 · Pie de página y navegación entre recetas

**Meta:** dejar un elemento en cada extremo con `space-between`, y empujar uno solo con `margin-left: auto`.

**Haz esto:**
1. En el pie de página, separa el texto en dos párrafos dentro de un `.contenedor`:
   ```html
   <footer class="pie-pagina">
       <div class="contenedor">
           <p>Blog de Cocina Chilena &copy; 2026</p>
           <p>Diseño Web Básico · DUOC UC</p>
       </div>
   </footer>
   ```
   ```css
   .pie-pagina .contenedor {
     display: flex;
     flex-wrap: wrap;
     justify-content: space-between;   /* uno a cada extremo */
     gap: 8px;
   }
   ```
2. Al final de cada receta, cambia el párrafo con los enlaces anterior y siguiente por un `<nav>`:
   ```html
   <nav class="receta-pie" aria-label="Más recetas">
       <a href="charquican.html">← Anterior: Charquicán</a>
       <a class="siguiente" href="../postres/tiramisu.html">Siguiente: Tiramisú →</a>
   </nav>
   ```
   ```css
   .receta-pie {
     display: flex;
     flex-wrap: wrap;
     justify-content: space-between;
     gap: 12px;
     border-top: 2px dotted #d9c6a5;
     padding-top: 16px;
   }

   .receta-pie .siguiente {
     margin-left: auto;   /* lo empuja a la derecha aunque esté solo */
   }
   ```

**Comprueba:** en el charquicán, que solo tiene «Siguiente», el enlace igual queda a la derecha.

**Errores frecuentes:**
- Usar `float: right` para el enlace «Siguiente»: funciona a medias y descuadra la caja. Con flex basta `margin-left: auto`.

---

## Paso 9 · `display: block` y `display: inline`

**Meta:** cambiar cómo se muestra un elemento. La pauta pide usar ambos valores.

**Haz esto:**
1. **De línea a bloque:** haz que cada enlace «Ver …» de las tarjetas ocupe su propia línea:
   ```css
   .tarjeta a {
     display: block;
     font-weight: bold;
     margin-top: 8px;
   }
   ```
2. **De bloque a línea:** en cada receta, agrega bajo el título una lista corta con los datos del plato y muéstrala en una sola línea:
   ```html
   <ul class="datos-receta">
       <li>4 porciones</li>
       <li>45 minutos</li>
       <li>Dificultad: fácil</li>
   </ul>
   ```
   ```css
   .datos-receta li {
     display: inline;
     margin-right: 12px;
   }

   .datos-receta li + li {
     padding-left: 12px;
     border-left: 2px solid #d9c6a5;   /* separador entre datos */
   }
   ```

**Comprueba:** los enlaces de las tarjetas quedan uno debajo del otro y los datos de la receta, en una sola fila.

**Errores frecuentes:**
- Pensar que `display: inline` acepta `width` y `height`: los elementos en línea los ignoran.
- Olvidar que los `<li>` son bloque por defecto: sin `display: inline` (o `flex` en el `<ul>`), se apilan.

---

## Paso 10 · Una imagen rodeada de texto con `float`

**Meta:** usar `float` para lo que fue creado: que el texto rodee a una imagen.

**Haz esto:**
1. Agrega una foto del plato dentro de la receta, **antes del primer párrafo**, con su texto alternativo:
   ```html
   <img class="foto-receta" src="../assets/img/charquican.jpg" alt="Plato de charquicán servido con un huevo frito encima" width="240" height="180">
   ```
2. Hazla flotar a la izquierda y sepárala del texto:
   ```css
   .foto-receta {
     float: left;
     margin: 4px 20px 12px 0;
     border: 4px solid #f3e9d8;
   }
   ```
3. Haz que los subtítulos empiecen **debajo** de la imagen y que la caja de la receta la contenga:
   ```css
   .receta h3 {
     clear: both;
   }

   .receta {
     display: flow-root;
   }
   ```
4. Devuelve las viñetas y los números que quitó el reset: agrega `class="ingredientes"` al `<ul>` y `class="pasos"` al `<ol>`:
   ```css
   .ingredientes { list-style: disc;    padding-left: 20px; }
   .pasos        { list-style: decimal; padding-left: 24px; }
   ```

**Comprueba:** el párrafo fluye al lado de la imagen, «Ingredientes» empieza debajo de ella y la imagen no se sale de la caja de la receta.

**Errores frecuentes:**
- Imagen sin `alt`, o con un `alt` como «imagen1». Describe lo que muestra (es un criterio de accesibilidad).
- Usar `float` para armar el layout de la página: para eso está `flex` (pasos 4, 6, 7 y 8).
- No separar la imagen del texto con `margin`.

---

## Paso 11 · Columnas (opcional)

**Meta:** repartir la lista de ingredientes en dos columnas.

**Haz esto:**
```css
.ingredientes {
  column-count: 2;
  column-gap: 32px;
}

.ingredientes li {
  break-inside: avoid;   /* un ingrediente no se corta entre columnas */
}
```

**Comprueba:** la lista se reparte en 2 columnas parejas.

**Errores frecuentes:**
- Aplicar `column-count` a cada `<li>` en vez de a la lista que los contiene.

---

## Paso 12 · Revisar contraste y validar

**Meta:** que el sitio se lea bien y cumpla el estándar.

**Haz esto:**
1. Revisa el contraste de cada combinación de texto y fondo en el [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/). Fíjate sobre todo en el menú, en el `:hover` y en las tarjetas. Estos son los del ejemplo:

   | Texto | Fondo | Dónde | Contraste |
   |-------|-------|-------|:---------:|
   | `#faf6ef` | `#6b4a2f` | Enlaces del menú | 7,37:1 ✅ |
   | `#ffffff` | `#4a3221` | Menú en `:hover` | 11,87:1 ✅ |
   | `#4a3221` | `#faf6ef` | Página actual del menú | 11,02:1 ✅ |
   | `#8f4426` | `#ffffff` | Enlaces del contenido | 6,95:1 ✅ |
   | `#8f4426` | `#f3e9d8` | Enlaces en tarjetas y lateral | 5,78:1 ✅ |
   | `#6b4a2f` | `#ffffff` | Subtítulos y datos de la receta | 7,94:1 ✅ |
   | `#e8dac5` | `#4a3221` | Pie de página | 8,63:1 ✅ |

2. Valida las 5 páginas en <https://validator.w3.org/#validate_by_input> y el CSS en <https://jigsaw.w3.org/css-validator/#validate_by_input>.
3. Abre la consola del navegador (`F12` → Consola) y revisa que no haya errores, como imágenes o archivos que no cargan.

**Comprueba:** el contraste es de al menos **4,5:1** (AA) en texto normal, el validador marca **0 errores** y la consola está limpia.

**Errores frecuentes:**
- Revisar solo el estado normal y olvidar el `:hover`.
- Que el validador marque un `<li>` fuera de un `<ul>` o una etiqueta sin cerrar.

---

## Paso 13 · Publicar y probar desde la URL

**Meta:** dejar el sitio funcionando en el hosting de Duoc.

**Haz esto:**
1. Entra al hosting de Duoc con los datos de acceso. Si no los recibiste, **levanta un ticket en la mesa de ayuda** lo antes posible.
2. Sube la carpeta **completa**: `index.html` en la raíz, las subcarpetas y `assets/` (con `css/` e `img/`).
3. Abre tu URL.

**Comprueba:** desde la URL, recorre las 5 páginas usando **solo el menú**. Todo debe tener estilos, las fotos deben cargar y ningún enlace debe estar roto. Abre la URL también en tu celular.

**Errores frecuentes:**
- Subir archivos sueltos y perder la estructura de carpetas.
- Diferencias de mayúsculas entre `Charquican.jpg` y `charquican.jpg`: en el servidor no funcionan igual.
- Ver una versión antigua por la caché: recarga forzando (`Ctrl + F5`, o `Cmd + Shift + R` en Mac).

---

## ✅ Checklist final

- [ ] Una **sola** hoja de estilos para todo el sitio, con el reset y `box-sizing` al inicio.
- [ ] Estilos aplicados a los textos.
- [ ] Menú de navegación en **todas** las páginas, con las rutas correctas y la página actual marcada.
- [ ] Enlaces con `:hover`, y los del menú se ven **distintos** a los del contenido.
- [ ] Colores de fondo y **bordes**.
- [ ] Layout con `display: flex`: menú en fila, contenido + lateral, tarjetas y pie de página.
- [ ] Al menos un elemento con `display: block` y otro con `display: inline`.
- [ ] Una imagen con `float`, rodeada de texto y con un `alt` descriptivo.
- [ ] Selectores de **clase** y **combinados**.
- [ ] Contraste revisado (AA como mínimo), HTML y CSS validados, consola sin errores.
- [ ] Sitio publicado y recorrido completo desde la URL, también en el celular.

## ❓ Preguntas de repaso

1. ¿Por qué el reset debe ir al comienzo de la hoja de estilos?
2. Una caja tiene `width: 300px`, `padding: 20px` y `border: 5px`. ¿Cuánto mide de ancho **sin** `box-sizing: border-box`? ¿Y con él?
3. ¿A qué elemento se le aplica `display: flex`: al contenedor o a los hijos?
4. Con `flex-direction: column`, ¿qué propiedad centra los hijos en horizontal: `justify-content` o `align-items`?
5. ¿Qué significan los tres valores de `flex: 3 1 560px`?
6. ¿Para qué sirve `flex-wrap: wrap` en el layout de dos columnas?
7. ¿Para qué se recomienda usar `float` hoy? ¿Qué hacen `clear: both` y `display: flow-root`?
8. ¿Cómo logras que los enlaces del menú se vean distintos a los del contenido?
9. Tu sitio se ve bien en tu computador pero sin estilos en la URL. ¿Qué revisarías primero?

## 📤 Entrega

Aplica lo aprendido a **tu propio blog** (no entregues el demo). Según la actividad sumativa individual *Estilando mi sitio*, entrega por **AVA**:

- el **link (URL)** de tu sitio publicado en el hosting de Duoc;
- la carpeta de tu sitio comprimida en **.zip**.

📅 Plazo: **lunes 16 de noviembre de 2026, 23:59 hrs.** Revisa la rúbrica de 9 criterios en el AVA antes de entregar.

---

*Diseño Web Básico · EXP2 Semana 4 · Campus Virtual DUOC UC*
