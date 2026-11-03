# Semana 3 — Creando mis primeras reglas de CSS
**Diseño Web Básico · EXP2 - Semana 3**
**Asignatura:** Diseño web básico · **Carrera:** Desarrollo y Diseño Web · DUOC UC

---

## Introducción a la semana

En la experiencia anterior aprendimos a estructurar contenidos mediante HTML. Ahora, a ese documento, le daremos su **apariencia visual**.

Dar estilo significa aplicar propiedades a los textos: color y grosor de tipografía, alineamiento, colores de fondo, interlineados. Para ello necesitamos aprender **CSS (Cascade Style Sheets u Hojas de Estilo en Cascada)**, el lenguaje que controla la apariencia.

> 💡 El contenido (HTML) va separado de su apariencia (CSS). Esto permite cambiar el look del sitio sin editar el HTML.

---

## Resultado de Aprendizaje e Indicadores de Logro

**El estudiante será capaz de:**
- Ejecutar código CSS considerando códigos gráficos, con el propósito de asignar apariencia visual al contenido web adaptable a múltiples dispositivos.

**Indicadores de logro trabajados esta semana:**
- **IL 8.** Crea archivo CSS, utilizando nomenclatura y vinculación, siguiendo buenas prácticas.
- **IL 9.** Efectúa la codificación del documento, utilizando la sintaxis de código y considerando herencias y tipos de selectores.
- **IL 10.** Aplica las reglas de CSS para la diagramación de estructura de archivo según requerimiento visual.

**Preguntas activadoras:**
- ¿Cómo cambio la tipografía de mi sitio?
- ¿De qué forma alineo los textos?
- ¿Cómo cambio el color de la tipografía?

---

## Contenidos desarrollados

### 1. ¿Qué es CSS?

CSS es un lenguaje de hojas de estilo. Se le conoce como **hojas de estilo en cascada** porque puede haber varias hojas y las propiedades se heredan entre ellas.

Funciona junto con HTML y controla el diseño y presentación del sitio web: fuentes, colores, tamaños, etc.

> Si HTML es el esqueleto de una página, CSS es la piel, el pelo y la ropa.

**Diferencia clave:** HTML usa `< >` y CSS usa `{ }`.

---

### 2. Sintaxis de una regla CSS

Una regla CSS tiene tres partes:

- **Selector:** el elemento HTML al que se aplica el estilo.
- **Propiedad:** qué aspecto se define (ej: color, font-size).
- **Valor:** el valor de esa propiedad (ej: red, 16px).

```css
selector {
  propiedad: valor;
}
```

**Ejemplo:**
```css
h1 {
  color: #f90000;
  font-family: Helvetica;
}
```

Un selector puede tener **múltiples declaraciones**, cada una separada por punto y coma `;`.

---

### 3. Tipos de selectores

| Selector | Sintaxis | Descripción |
|----------|----------|-------------|
| Elemento | `p { }` | Selecciona todas las etiquetas de ese tipo |
| Clase | `.nombre { }` | Selecciona elementos con esa clase |
| ID | `#nombre { }` | Selecciona el elemento con ese ID |
| Universal | `* { }` | Selecciona todos los elementos |
| Combinador descendiente | `nav a { }` | Selecciona `<a>` dentro de `<nav>` |
| Combinador hijo | `ul > li { }` | Solo hijos directos |
| Atributo | `input[type="text"] { }` | Elementos con ese atributo |

---

### 4. Ubicación de los estilos

Hay tres formas de incluir CSS en HTML:

**1. Hoja externa (recomendada) ✅**
```html
<link rel="stylesheet" href="assets/styles.css">
```
Separación total del HTML y CSS. Permite reutilizar estilos en múltiples páginas.

**2. Etiqueta `<style>` en el `<head>`**
```html
<head>
  <style>
    p { color: blue; }
  </style>
</head>
```

**3. Estilo en línea (no recomendado ❌)**
```html
<p style="color: blue;">Texto</p>
```
Dificulta el mantenimiento del código.

---

### 5. Propiedades de texto

#### `font-family` — Familia tipográfica
```css
p { font-family: Arial, Helvetica, sans-serif; }
```
Siempre incluir fuentes alternativas separadas por coma.

#### `font-size` — Tamaño de fuente
```css
h1 { font-size: 32px; }
p  { font-size: 1rem; }
```

#### `color` — Color del texto

Formatos disponibles:
- **Hexadecimal:** `color: #ff0000;`
- **RGB:** `color: rgb(255, 0, 0);`
- **RGBA (con opacidad):** `color: rgba(255, 0, 0, 0.5);`
- **HSL:** `color: hsl(0, 100%, 50%);`
- **Por nombre:** `color: red;`

#### `font-weight` — Grosor del texto
```css
p { font-weight: bold; }         /* normal | bold | lighter | bolder */
p { font-weight: 700; }          /* valores del 100 al 900 */
```

#### `font-style` — Estilo de fuente
```css
em { font-style: italic; }       /* normal | italic | oblique */
```

#### `text-transform` — Transformar texto
```css
h1 { text-transform: uppercase; } /* none | uppercase | lowercase | capitalize */
```

#### `text-align` — Alineación del texto
```css
p { text-align: justify; }       /* left | center | right | justify */
```
> ⚠️ `justify` no se recomienda en pantalla porque dificulta la lectura.

#### `text-decoration` — Decoración
```css
a { text-decoration: none; }     /* none | underline | overline | line-through */
```

---

### 6. Background — Fondo

#### `background-color` — Color de fondo
```css
header { background-color: #222222; }
section { background-color: rgba(0, 0, 0, 0.5); }
```

#### `background-image` — Imagen de fondo
```css
body {
  background-image: url("assets/img/fondo.jpg");
  background-repeat: no-repeat; /* no-repeat | repeat | repeat-x | repeat-y */
}
```

---

### 7. Herencia en CSS

CSS hereda propiedades del elemento padre a sus hijos.

```css
/* Si defino esto en body, TODOS los elementos lo heredan */
body {
  font-family: Arial;
  color: #333;
}

/* Puedo sobreescribir solo donde necesito */
h1 {
  font-family: 'Trebuchet MS';
}
```

> El elemento padre de todo lo visible es `<body>`. Lo que declaras ahí se aplica a todo el sitio a menos que lo sobreescribas.

---

## Actividad de la semana

**Actividad Formativa: Aplicando CSS en una estructura HTML**

Deberás crear una hoja de estilos para los 5 archivos HTML del blog armado en la semana 2, creando tus primeras reglas CSS con los siguientes **selectores**:
- `class`
- Elemento
- Combinadores

Y estilando los textos (párrafos y encabezados) con las propiedades:
- `font-family`
- `font-size`
- `font-weight`
- `text-align`
- `background-color` y/o `background-image`

📅 **Fecha de entrega:** Lunes 9 de noviembre de 2026 a las 23:59 hrs.

---

## Recursos de referencia

- [MDN CSS Selectores](https://developer.mozilla.org/es/docs/Web/CSS/Class_selectors)
- [MDN Fundamentos de texto y fuentes](https://developer.mozilla.org/es/docs/Learn/CSS/Styling_text/Fundamentals)
- [W3Schools CSS Fonts](https://www.w3schools.com/css/css_font.asp)
- [W3Schools CSS Colors](https://www.w3schools.com/css/css_colors.asp)
- [Adobe Color CC](https://color.adobe.com)

---

*Diseño Web Básico · EXP2 Semana 3 · Campus Virtual DUOC UC*
*Facilitador disciplinar: Jimena Jamett · Asesor par: Max Villalobos*
