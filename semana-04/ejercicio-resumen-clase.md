# Ejercicios — Semana 4: Aplicando el estilo a mi sitio
**Diseño Web Básico · EXP2 - Semana 4**

> Estos ejercicios refuerzan los contenidos de la guía de la semana 4. Practícalos antes de realizar la actividad sumativa.

---

## Ejercicio 1 — Pseudoclases en enlaces

**Objetivo:** Practicar las pseudoclases `:link`, `:visited`, `:hover` y `:active`.

Dado este HTML:
```html
<p>Visita <a href="https://www.duoc.cl">DUOC UC</a> para más información.</p>
```

Escribe reglas CSS para que:
1. Los enlaces no visitados (`link`) sean de color `#0066cc`.
2. Los enlaces visitados (`visited`) sean de color `#9900cc`.
3. Al pasar el mouse (`hover`) el color cambie a `#ff6600` y el texto se vea subrayado.
4. Al hacer clic (`active`) el color sea `#cc0000`.

```css
/* Tu solución: */
a:link    { }
a:visited { }
a:hover   { }
a:active  { }
```

**✅ Resultado esperado:** Cada estado del enlace tiene un color distinto.

---

## Ejercicio 2 — Crear un menú de navegación horizontal

**Objetivo:** Construir y estilar un menú de navegación aplicando pseudoclases y display.

**HTML de partida:**
```html
<nav>
  <ul>
    <li><a href="index.html">Inicio</a></li>
    <li><a href="recetas.html">Recetas</a></li>
    <li><a href="viajes.html">Viajes</a></li>
    <li><a href="contacto.html">Contacto</a></li>
  </ul>
</nav>
```

Escribe el CSS para lograr:
- [ ] Sin bullets en la lista.
- [ ] Menú en una sola línea (horizontal).
- [ ] Sin subrayado en los enlaces.
- [ ] Color de texto blanco sobre fondo oscuro.
- [ ] Al pasar el mouse, el fondo del enlace cambia de color.

```css
nav {
  background-color: #222;
}

nav ul { }

nav li { }

nav a { }

nav a:hover { }
```

**✅ Pistas:** `list-style: none`, `display: inline`, `text-decoration: none`, `padding`.

**Variante con flex:** borra el `display: inline` de los `li` y prueba `display: flex` y `gap: 16px` en `nav ul`. ¿Qué diferencia notas? ¿Qué pasa al agregar `justify-content: center`?

---

## Ejercicio 3 — Reset de CSS

**Objetivo:** Entender para qué sirve el reset y aplicarlo correctamente.

1. Crea un archivo HTML con este contenido:
```html
<h1>Título</h1>
<p>Párrafo de texto.</p>
<ul>
  <li>Elemento 1</li>
  <li>Elemento 2</li>
</ul>
```
2. Abre en el navegador **sin CSS**. Observa los márgenes, negritas y espaciados que tiene por defecto.
3. Ahora agrega este reset básico al inicio de tu CSS (la guía recomienda además el [reset de Eric Meyer](https://meyerweb.com/eric/tools/css/reset/reset.css), que es más completo):
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```
4. Recarga. ¿Qué cambió?

**Responde:**
- ¿Por qué el reset debe ir al **inicio** del archivo CSS?
- ¿Qué problema resuelve usar `box-sizing: border-box`?

---

## Ejercicio 4 — Entender el modelo de cajas

**Objetivo:** Visualizar las partes del box model (content, padding, border, margin).

Crea un `<div>` con el siguiente CSS y analiza cómo se comporta:

```css
* {
  box-sizing: border-box;
}

.caja {
  width: 300px;
  height: 150px;
  background-color: #e0f0ff;
  padding: 20px;
  border: 5px solid #0066cc;
  margin: 30px auto;
}
```

**Preguntas:**
1. ¿Cuánto espacio total ocupa la caja en el flujo de la página?
2. Ahora quita `box-sizing: border-box`. ¿Cambia el tamaño visible?
3. ¿Qué hace `margin: 30px auto`? ¿Dónde se centra el elemento?

---

## Ejercicio 5 — Padding y Border en práctica

**Objetivo:** Diferenciar padding de margin y usar propiedades de borde.

Dado este HTML:
```html
<section class="tarjeta">
  <h2>Título de la tarjeta</h2>
  <p>Contenido de la tarjeta con algo de texto descriptivo.</p>
</section>
```

Aplica CSS para que:
1. La `.tarjeta` tenga `padding: 20px` (relleno interno).
2. Tenga un `border: 2px solid #ccc`.
3. Tenga `margin: 20px auto` y un `width: 400px`.
4. El `h2` tenga solo `border-bottom: 2px dashed #0066cc` y `padding-bottom: 8px`.

```css
.tarjeta { }
.tarjeta h2 { }
```

---

## Ejercicio 6 — Display: block e inline

**Objetivo:** Cambiar el comportamiento de visualización de elementos.

```html
<ul class="menu-horizontal">
  <li><a href="#">Casa</a></li>
  <li><a href="#">Decoración</a></li>
  <li><a href="#">Jardín</a></li>
</ul>
```

1. Primero observa cómo se ve sin CSS (lista vertical con bullets).
2. Aplica `display: inline` a los `<li>`. ¿Qué pasa?
3. Cambia a `display: inline-block` y agrega `padding: 8px 16px`. ¿Cuál se ve mejor?
4. Ahora prueba dándole `display: block` a los `<a>`. ¿Qué efecto tiene?
5. Por último, quita el `display` de los `<li>` y aplica `display: flex` y `gap: 16px` a la `.menu-horizontal`. ¿Qué cambia? Recuerda: `flex` se aplica al **contenedor** y ordena a sus hijos directos.

---

## Ejercicio 7 — Flexbox: el contenedor y los dos ejes

**Objetivo:** Entender que `flex` va en el padre y qué alinea cada propiedad.

> 🧪 Antes de empezar, juega 5 minutos con el laboratorio de [`material-semana/flexbox-guia-visual.html`](./material-semana/flexbox-guia-visual.html).

```html
<div class="platos">
  <div class="plato">Charquicán</div>
  <div class="plato">Bife a lo pobre</div>
  <div class="plato">Tiramisú</div>
</div>
```

```css
.platos {
  height: 250px;
  border: 2px dashed #a8512e;
}

.plato {
  background-color: #f3e9d8;
  border: 2px solid #6b4a2f;
  padding: 10px;
}
```

1. Agrega `display: flex` a `.platos`. ¿Qué cambió?
2. Agrega `justify-content: center`. ¿En qué dirección se movieron los platos?
3. Agrega `align-items: center`. ¿Y ahora?
4. Agrega `flex-direction: column`. ¿Qué pasó con lo que hacían `justify-content` y `align-items`?
5. Mueve `display: flex` a `.plato` (y quítalo de `.platos`). ¿Funciona? ¿Por qué?

**✅ Resultado esperado:** puedes explicar con tus palabras qué es el **eje principal** y qué es el **eje cruzado**.

---

## Ejercicio 8 — Diagramar una página con flex

**Objetivo:** Armar el layout de una página: cabecera, menú, contenido con columna lateral, tarjetas y pie.

**HTML de partida:**
```html
<header class="cabecera"><h1>Mi blog</h1></header>

<nav class="menu">
  <ul>
    <li><a href="#">Inicio</a></li>
    <li><a href="#">Recetas</a></li>
    <li><a href="#">Contacto</a></li>
  </ul>
</nav>

<div class="contenedor disposicion">
  <main class="contenido">
    <h2>Últimas recetas</h2>
    <div class="tarjetas">
      <section class="tarjeta">Charquicán</section>
      <section class="tarjeta">Pastel de choclo</section>
      <section class="tarjeta">Sopaipillas</section>
    </div>
  </main>
  <aside class="lateral">Sobre mí</aside>
</div>

<footer class="pie">
  <p>© 2026</p>
  <p>Hecho en Duoc UC</p>
</footer>
```

Escribe el CSS para lograr:
- [ ] El menú en una fila centrada, con `gap` entre los enlaces.
- [ ] `.contenedor` centrado, con un ancho máximo de `1000px`.
- [ ] `main` y `aside` lado a lado: el contenido 3 veces más ancho que la lateral.
- [ ] Las tres tarjetas en fila, que bajen de línea si no caben.
- [ ] El pie con un párrafo a cada extremo.

```css
.menu ul { }

.contenedor { }

.disposicion { }
.contenido { }
.lateral { }

.tarjetas { }
.tarjeta { }

.pie { }
```

**✅ Pistas:** `display: flex`, `flex-wrap: wrap`, `gap`, `margin: 0 auto`, `flex: 3 1 400px`, `justify-content: space-between`.

**Prueba:** achica la ventana hasta el ancho de un celular. ¿Qué pasa con la columna lateral y con las tarjetas?

---

## 🐸 Reto — Flexbox Froggy

Juega [Flexbox Froggy](https://flexboxfroggy.com/#es) (en español) y llega lo más lejos que puedas. Los primeros 12 niveles cubren todo lo que usarás en la sumativa.

---

## Ejercicio 9 — Float: imagen rodeada de texto

**Objetivo:** Usar `float` para lo que fue creado: que el texto rodee a una imagen. Para ordenar bloques de la página usa `display: flex` (ejercicios 7 y 8).

```html
<article>
  <img src="assets/img/mi-foto.jpg" alt="Descripción de la foto" class="imagen-flotante" width="150">
  <p>Este es un párrafo largo de texto que debería rodear la imagen. Agrega aquí suficiente texto para que el efecto sea visible en el navegador.</p>
</article>
```

```css
.imagen-flotante {
  float: left;
  margin: 0 16px 8px 0;
}
```

**Prueba:**
1. Cambia `float: left` a `float: right`. ¿Qué pasa?
2. ¿Qué efecto tiene quitar el `margin`?
3. Agrega un `<h3>` después del párrafo y dale `clear: both`. ¿Dónde empieza ahora?
4. Acorta el párrafo a una línea. ¿La imagen se sale del `<article>`? Agrégale `display: flow-root` al `article` y compara.

---

## Ejercicio 10 — Múltiples columnas

**Objetivo:** Practicar la propiedad `columns` para diagramar texto en columnas.

```html
<div class="contenido-columnas">
  <h2>Mi blog en columnas</h2>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris.</p>
  <p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
</div>
```

```css
.contenido-columnas {
  column-count: 2;
  column-gap: 30px;
  column-rule: 1px solid #ccc;
}

.contenido-columnas h2 {
  column-span: all;
}
```

**Prueba:** Cambia `column-count` a 3. ¿Cómo se adapta el texto?

---

## Ejercicio Final — Estilado completo del blog

**Objetivo:** Integrar todos los conceptos de la semana 4 en tu blog.

Crea o mejora el CSS de tu blog verificando que tenga:

- [ ] Reset de CSS al inicio (el de Eric Meyer, o como mínimo `* { margin: 0; padding: 0; }`) y `* { box-sizing: border-box; }`
- [ ] Menú de navegación horizontal (con `display: flex` en el `<ul>`) y con `:hover`
- [ ] Al menos 1 elemento con `display: block` y 1 con `display: inline`
- [ ] Los enlaces del menú se ven **distintos** a los enlaces del contenido
- [ ] Al menos 1 elemento con `padding` y `border` bien definidos
- [ ] `margin: 0 auto` para centrar el contenedor principal
- [ ] Layout con `display: flex`: contenido y columna lateral, o un grupo de tarjetas, que se acomoden en el celular
- [ ] Al menos 1 imagen con `float` rodeada de texto
- [ ] El sitio publicado en el servidor con URL funcionando

> 📌 Este ejercicio te prepara directamente para la **Actividad Sumativa de la semana 4**: Estilando mi sitio. Compara tu resultado con el [ejemplo de la clase](./material-clase/LEEME.md).

---

*Diseño Web Básico · EXP2 Semana 4 · Campus Virtual DUOC UC*
