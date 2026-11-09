# Semana 3 — Creando mis primeras reglas de CSS
**Diseño Web Básico · EXP2 - Semana 3**
**Asignatura:** Diseño web básico · **Carrera:** Desarrollo y Diseño Web · DUOC UC

---

## En esta semana

| | |
|---|---|
| **Tema** | Creando mis primeras reglas de CSS |
| **Actividad** | Formativa: *Aplicando CSS en una estructura HTML* |
| **Clase sincrónica** | Martes 3 de noviembre, 21:00 hrs. (la grabación queda en el foro semanal) |
| **Entrega** | Lunes 9 de noviembre de 2026, 23:59 hrs., por AVA |

---

## Introducción a la semana

En la experiencia anterior estructuraste los contenidos de tu blog con HTML. Ahora le daremos su **apariencia visual**.

Dar estilo significa aplicar propiedades a los textos: color y grosor de la tipografía, alineación, colores de fondo e interlineados. Para eso usamos **CSS (Cascading Style Sheets u Hojas de Estilo en Cascada)**, el lenguaje que controla cómo se ve una página.

> 💡 El contenido (HTML) va separado de su apariencia (CSS). Así puedes cambiar el look de todo el sitio sin tocar el HTML.

**Preguntas activadoras:**
- ¿Cómo cambio la tipografía de mi sitio?
- ¿De qué forma alineo los textos?
- ¿Cómo cambio el color de la tipografía?

**Conceptos clave:** hojas de estilo · regla CSS · selectores · propiedades · valores · herencia.

---

## 1. ¿Qué es CSS?

CSS es un lenguaje de hojas de estilo. Se llama **«en cascada»** porque puedes tener varias hojas y las propiedades se van heredando entre ellas.

> Si el HTML es el esqueleto de la página, el CSS es la piel, el pelo y la ropa.

HTML y CSS son lenguajes distintos: HTML usa `< >` y CSS usa `{ }`.

---

## 2. Sintaxis de una regla CSS

Una regla tiene un **selector** y una **declaración** entre llaves. La declaración está formada por **propiedad** y **valor**.

```css
selector {
  propiedad: valor;
}
```

- **Selector:** el elemento HTML al que le aplicas el estilo.
- **Propiedad:** lo que quieres definir (color, tipografía, tamaño…).
- **Valor:** cómo quieres que quede (naranjo, Helvetica, 24px…).

Un selector puede tener varias declaraciones, cada una terminada en punto y coma `;`:

```css
h1 {
  color: #f90;          /* naranjo (equivale a #ff9900) */
  font-family: Helvetica, Arial, sans-serif;
}
```

---

## 3. Tipos de selectores

| Selector | Sintaxis | Qué selecciona |
|----------|----------|----------------|
| Elemento | `h2 { }` | Todas las etiquetas de ese tipo |
| Clase | `.color-marca { }` | Todos los elementos con `class="color-marca"` (se puede repetir) |
| ID | `#home { }` | El único elemento con `id="home"` |
| Universal | `* { }` | Todos los elementos |
| Combinador descendiente | `.cabecera h1 { }` | Los `h1` que están **dentro** de `.cabecera` |
| Atributo | `a[href] { }` | Elementos que tienen ese atributo |

**Reglas para nombrar clases e ID:** sin caracteres especiales, sin espacios, en minúsculas, sin empezar con números y con nombres que describan su función.

> 📌 La actividad de esta semana pide usar selectores de **clase**, de **elemento** y **combinadores**.

---

## 4. Ubicación de los estilos

| Ubicación | ¿Cómo? | ¿Recomendada? |
|-----------|--------|---------------|
| **Hoja externa** | Archivo `style.css` en `assets/css/`, vinculado con `<link>` | ✅ Sí: un cambio actualiza todo el sitio |
| Etiqueta `<style>` | Reglas dentro del `<head>` de una página | ❌ Solo afecta a esa página |
| Estilo en línea | Atributo `style=""` en una etiqueta | ❌ Solo afecta a esa etiqueta |

La hoja externa se vincula en el `<head>`, **debajo del `<title>`**:

```html
<title>Mi blog</title>
<link rel="stylesheet" href="assets/css/style.css">
```

> ⚠️ Si la página está dentro de una subcarpeta, la ruta cambia: `href="../assets/css/style.css"`. El `../` sube un nivel.

---

## 5. Propiedades de texto

| Propiedad | Para qué sirve | Valores de ejemplo |
|-----------|----------------|--------------------|
| `font-family` | Familia tipográfica | `"Trebuchet MS", Verdana, sans-serif` |
| `font-size` | Tamaño de la letra | `16px`, `1.5em`, `1rem`, `120%` |
| `color` | Color del texto | `#ff0000`, `rgb(255, 0, 0)`, `tomato` |
| `font-weight` | Grosor | `normal`, `bold`, `100`–`900` |
| `font-style` | Cursiva | `normal`, `italic`, `oblique` |
| `text-transform` | Mayúsculas y minúsculas | `uppercase`, `lowercase`, `capitalize` |
| `text-align` | Alineación | `left`, `center`, `right`, `justify` |
| `text-decoration` | Subrayado y otras líneas | `none`, `underline`, `line-through` |

**Sobre `font-family`:** el navegador solo muestra fuentes instaladas en el equipo de quien visita el sitio. Por eso se escribe una **lista**: si la primera no está, usa la siguiente. Los nombres de más de una palabra van entre comillas. Servicios como Google Fonts entregan la fuente desde internet.

**Sobre las unidades de `font-size`:** `px` es fija; `em` y `%` dependen del elemento padre; `rem` depende del tamaño base del `<html>`.

> ⚠️ `justify` no se recomienda en pantalla porque dificulta la lectura.

---

## 6. Formas de escribir un color

| Formato | Ejemplo (rojo) | Nota |
|---------|----------------|------|
| Hexadecimal | `#ff0000` | `#RRGGBB`, de `00` a `ff` |
| RGB | `rgb(255, 0, 0)` | Cada canal de 0 a 255 |
| RGBA | `rgba(255, 0, 0, 0.5)` | El cuarto valor es la opacidad (0 a 1) |
| HSL | `hsl(0, 100%, 50%)` | Tono (0–360), saturación y luminosidad |
| Nombre | `red`, `tomato` | Lista de nombres predefinidos |

Para armar una paleta puedes usar [Adobe Color](https://color.adobe.com).

---

## 7. Fondos

```css
.cabecera {
  background-color: #4a3221;
}

body {
  background-image: url("../img/fondo.jpg");
  background-repeat: no-repeat;   /* repeat | repeat-x | repeat-y | no-repeat */
}
```

> ⚠️ La ruta de `url()` se escribe **desde la ubicación del archivo CSS**. Si tu hoja está en `assets/css/` y la imagen en `assets/img/`, la ruta es `../img/fondo.jpg`.

---

## 8. Herencia

Los elementos hijos heredan muchas propiedades de su elemento padre. Si declaras la tipografía en `body`, todo el sitio la usa, salvo donde declares otra:

```css
body {
  font-family: Arial, Helvetica, sans-serif;
}

h1 {
  font-family: "Trebuchet MS", sans-serif;  /* solo el h1 cambia */
}
```

---

## Actividad formativa: *Aplicando CSS en una estructura HTML*

Crea **una hoja de estilos** para los **5 archivos HTML** del blog que armaste en la semana 2.

1. Crea tus primeras reglas CSS usando selectores de:
   - clase
   - elemento
   - combinadores
2. Da estilo a los textos (párrafos y encabezados) con:
   - `font-family`
   - `font-size`
   - `font-weight`
   - `text-align`
   - `background-color` y/o `background-image`

### 📤 Formato de entrega

- La carpeta de tu sitio comprimida en **.zip**.
- El sitio **subido al hosting de Duoc** (con los datos que entrega el AVA) y la **URL** copiada en el documento de la actividad.
- Todo se entrega por AVA hasta el **lunes 9 de noviembre de 2026, 23:59 hrs.**

### 📋 ¿Cómo se revisa?

Se usa una **escala de valoración** con cinco niveles: Completamente logrado (100%), Logrado (80%), Medianamente logrado (60%), Logro insuficiente (30%) y No logrado (0%).

Revisa **10 aspectos**. No solo mira el CSS: también revisa tu HTML.
- **Estructura y HTML (1 a 4):** carpeta raíz y nombres de archivos, documentos HTML según el estándar W3C, código ordenado con indentación y comentarios, y etiquetas semánticas y accesibles.
- **Navegación y publicación (5 a 7):** proceso de publicación, archivos bien vinculados para navegar el sitio y sitio funcionando en el servidor.
- **CSS (8 a 10):** archivo CSS bien nombrado y vinculado, sintaxis con herencia y tipos de selectores, y reglas aplicadas según el diseño.

---

## Recursos de referencia

- [MDN — Selectores de clase](https://developer.mozilla.org/es/docs/Web/CSS/Class_selectors)
- [MDN — Combinador descendiente](https://developer.mozilla.org/es/docs/Web/CSS/Descendant_combinator)
- [MDN — Fundamentos de texto y fuentes](https://developer.mozilla.org/es/docs/Learn/CSS/Styling_text/Fundamentals)
- [W3Schools — CSS Fonts](https://www.w3schools.com/css/css_font.asp)
- [W3Schools — CSS Colors](https://www.w3schools.com/css/css_colors.asp)
- [Adobe Color](https://color.adobe.com)

---

*Diseño Web Básico · EXP2 Semana 3 · Campus Virtual DUOC UC*
*Facilitador disciplinar: Jimena Jamett · Asesor par: Max Villalobos*
