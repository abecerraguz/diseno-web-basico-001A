# Semana 4 — Aplicando el estilo a mi sitio
**Diseño Web Básico · EXP2 - Semana 4**
**Asignatura:** Diseño web básico · **Carrera:** Desarrollo y Diseño Web · DUOC UC

---

## Introducción a la semana

La semana anterior conocimos qué es CSS, las reglas, su aplicación en HTML y las propiedades básicas para textos y fondos. Esta semana aprenderemos a **diagramar**: veremos nuevas propiedades para entender el **modelo de cajas**, cómo estilar enlaces con **pseudoclases**, cómo resetear el CSS para partir de cero y técnicas de layout con `display`, `float` y columnas.

---

## Resultado de Aprendizaje e Indicadores de Logro

**El estudiante será capaz de:**
- Ejecutar código CSS considerando códigos gráficos, con el propósito de asignar apariencia visual al contenido web adaptable a múltiples dispositivos.

**Indicadores de logro trabajados esta semana:**
- **IL 8.** Crea archivo CSS, utilizando nomenclatura y vinculación, siguiendo buenas prácticas.
- **IL 9.** Efectúa la codificación del documento, utilizando la sintaxis de código y considerando herencias y tipos de selectores.
- **IL 10.** Aplica las reglas de CSS para la diagramación de estructura de archivo según requerimiento visual.

**Preguntas activadoras:**
- ¿Cómo puedo hacer que los enlaces no se vean en azul y subrayados?
- ¿Cómo puedo hacer que al pasar el mouse sobre un enlace este cambie de color?
- ¿Cómo puedo disponer elementos lado a lado?

---

## Contenidos desarrollados

### 1. Pseudoclases

Las pseudoclases se añaden a los selectores y determinan un **comportamiento específico** en respuesta a la interacción del usuario.

**Sintaxis:**
```css
selector:pseudoclase {
  propiedad: valor;
}
```

**Pseudoclases de enlaces:**

| Pseudoclase | Cuándo se activa |
|-------------|-----------------|
| `:link` | Enlace no visitado |
| `:visited` | Enlace ya visitado |
| `:hover` | Al pasar el mouse por encima |
| `:active` | Mientras se hace clic |

**Ejemplo:**
```css
a:link    { color: #0066cc; }
a:visited { color: #9900cc; }
a:hover   { color: #ff6600; }
a:active  { color: #cc0000; }
```

---

### 2. Estilando enlaces

Por defecto los navegadores muestran los enlaces en **azul y subrayados**. Para cambiar eso:

```css
/* Quitar subrayado y color predeterminado */
a {
  text-decoration: none;
  color: #333;
}

/* Agregar efecto hover */
a:hover {
  color: #ff6600;
}
```

**Para un menú de navegación:**
```css
/* Quitar el bullet de la lista */
ul {
  list-style: none;
}

/* Hacer el menú horizontal */
li {
  display: inline;
}

/* Estilar solo los enlaces del nav (combinador descendiente) */
nav a {
  text-decoration: none;
  color: white;
  padding: 8px 16px;
}

nav a:hover {
  background-color: #444;
}
```

> ⚠️ Los enlaces del menú de navegación **deben verse distintos** a los enlaces del contenido. Úsa clases o combinadores para diferenciarlos.

---

### 3. Modelo de cajas (Box Model)

Para CSS, **todos los elementos HTML tienen una caja rectangular** a su alrededor. Cada vez que se inserta una etiqueta HTML, CSS crea una caja que encierra ese elemento.

#### Tipos de elementos

- **Bloque (block):** Ocupa el 100% del ancho disponible. Los elementos se apilan verticalmente. Ej: `<h1>`, `<p>`, `<div>`, `<header>`, `<section>`.
- **Línea (inline):** Permite que otros elementos estén al lado. Ej: `<a>`, `<strong>`, `<em>`, `<span>`.

#### Partes de una caja

```
┌─────────────────────────────────┐
│           MARGIN                │
│  ┌───────────────────────────┐  │
│  │         BORDER            │  │
│  │  ┌─────────────────────┐  │  │
│  │  │       PADDING       │  │  │
│  │  │  ┌───────────────┐  │  │  │
│  │  │  │    CONTENT    │  │  │  │
│  │  │  └───────────────┘  │  │  │
│  │  └─────────────────────┘  │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘
```

- **Content:** Área donde se muestra el contenido (texto, imágenes).
- **Padding:** Espacio entre el contenido y el borde.
- **Border:** Línea que envuelve el contenido y el padding.
- **Margin:** Espacio exterior entre la caja y otros elementos.

#### `box-sizing: border-box`

Por defecto, `width` y `height` solo aplican al **content**. Al agregar padding y border, la caja crece. Para evitarlo:

```css
/* Buena práctica: aplicar a TODOS los elementos */
* {
  box-sizing: border-box;
}
```

Con esto, el `width` incluye padding y border, y la caja **no crece más allá del ancho definido**.

---

### 4. Reset de CSS

Los elementos HTML traen estilos predeterminados del navegador (márgenes, negritas, colores). Para trabajar desde cero:

```css
/* Reset básico — va PRIMERO en tu CSS */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

También puedes usar el [Reset de Meyer Web](https://meyerweb.com/eric/tools/css/reset/reset.css) para un reset más completo.

> ✅ El reset siempre debe ir **al inicio** del archivo CSS, antes de tus propios estilos.

---

### 5. Padding — Relleno

Espacio interno entre el contenido y el borde.

```css
/* Los 4 lados iguales */
div { padding: 20px; }

/* Top y bottom | Right y left */
div { padding: 10px 20px; }

/* Top | Right | Bottom | Left (sentido horario) */
div { padding: 10px 20px 15px 20px; }

/* Lados independientes */
div {
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 15px;
  padding-left: 20px;
}
```

---

### 6. Border — Borde

```css
/* Sintaxis: width style color */
div { border: 2px solid #333; }

/* Bordes por lado */
h2 { border-bottom: 2px dashed #c00; }

/* Estilos de borde disponibles */
/* solid | dashed | dotted | double | groove | ridge | inset | outset */
```

---

### 7. Margin — Márgenes

Espacio externo entre la caja y otros elementos. Misma sintaxis que padding.

```css
/* Los 4 lados iguales */
p { margin: 16px; }

/* Centrar un elemento con ancho definido */
.contenedor {
  width: 960px;
  margin: 0 auto;
}
```

---

### 8. Técnicas de diagramación

#### `display` — Cambiar el tipo de elemento

```css
/* Hacer una lista horizontal */
li { display: inline; }

/* Dar comportamiento de bloque a un enlace */
a { display: block; }

/* inline-block: combina ambos */
.tarjeta { display: inline-block; width: 200px; }
```

#### `float` — Flotar elementos

Desplaza el elemento a la izquierda o derecha, permitiendo que el contenido fluya a su alrededor.

```css
img { float: left; }   /* imagen a la izquierda, texto rodea */
img { float: right; }  /* imagen a la derecha */
img { float: none; }   /* anula el float heredado */
```

#### `columns` — Múltiples columnas

```css
.articulo {
  column-count: 3;         /* número de columnas */
  column-gap: 20px;        /* separación entre columnas */
  column-rule: 1px solid #ccc; /* línea divisoria */
}

/* Elemento que ocupa todas las columnas */
h2 { column-span: all; }
```

---

## Checklist para el menú de navegación ✅

Al crear un menú de navegación en CSS, recuerda:

- [ ] Quitar el bullet a la lista: `ul { list-style: none; }`
- [ ] Quitar el subrayado a los enlaces: `a { text-decoration: none; }`
- [ ] Hacer el menú horizontal: `li { display: inline; }`
- [ ] Diferenciar los enlaces del nav de los del contenido: usar clases o combinador `nav a { }`
- [ ] Siempre agregar `:hover` para que el usuario sepa que puede hacer clic

---

## Actividad de la semana

**Actividad Sumativa: Estilando mi sitio**

Continuarás trabajando con tu blog. Crearás una **hoja de estilo única para todo el sitio** y la aplicarás en todas las páginas. Deberás:

1. Aplicar estilos a los textos.
2. Estilar los vínculos incluyendo la pseudoclase `:hover`.
3. Definir colores de fondo.
4. Mostrar elementos usando `display: block`, `inline` y `float`.
5. Utilizar bordes.
6. Usar selector de clase y combinados.
7. **Publicar el blog en el servidor**, con URL verificada.

📅 **Fecha de entrega:** Lunes 16 de noviembre de 2026 a las 23:59 hrs.

**Entrega:**
- Carpeta del sitio comprimida en `.zip`
- URL del sitio publicado en el servidor

---

## Recursos de referencia

- [MDN Box Model](https://developer.mozilla.org/es/docs/Learn/CSS/Building_blocks/The_box_model)
- [W3Schools CSS Border](https://www.w3schools.com/css/css_border.asp)
- [W3Schools CSS Float](https://www.w3schools.com/css/css_float.asp)
- [W3Schools CSS Multiple Columns](https://www.w3schools.com/css/css3_multiple_columns.asp)
- [Meyer Web CSS Reset](https://meyerweb.com/eric/tools/css/reset/reset.css)

---

*Diseño Web Básico · EXP2 Semana 4 · Campus Virtual DUOC UC*
*Facilitador disciplinar: Jimena Jamett · Asesor par: Max Villalobos*
