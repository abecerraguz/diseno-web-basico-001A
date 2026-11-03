# Ejercicios — Semana 3: Creando mis primeras reglas de CSS
**Diseño Web Básico · EXP2 - Semana 3**

> Estos ejercicios refuerzan los contenidos de la guía de la semana 3. Practícalos en tu editor de código (VS Code) antes de realizar la actividad formativa.

---

## Ejercicio 1 — Crear y vincular una hoja de estilos externa

**Objetivo:** Practicar la creación de un archivo CSS externo y su vinculación a HTML.

1. Crea un archivo llamado `estilos.css` dentro de una carpeta `assets/css/`.
2. En el `<head>` de tu HTML, agrega la siguiente línea:
   ```html
   <link rel="stylesheet" href="assets/css/estilos.css">
   ```
3. En tu archivo CSS escribe esta regla y guarda:
   ```css
   body {
     background-color: #f0f0f0;
   }
   ```
4. Abre el HTML en el navegador. ¿Cambió el fondo de la página?

**✅ Resultado esperado:** El fondo de la página se ve gris claro.

---

## Ejercicio 2 — Practicar tipos de selectores

**Objetivo:** Entender la diferencia entre selector de elemento, clase e ID.

Dado este HTML:
```html
<h1 id="titulo-principal">Mi Blog</h1>
<p class="texto-destacado">Este párrafo es especial.</p>
<p>Este párrafo es normal.</p>
<p class="texto-destacado">Este también es especial.</p>
```

Escribe reglas CSS para:

1. **Selector de elemento:** Que todos los `<p>` tengan `color: #444` y `font-size: 16px`.
2. **Selector de clase:** Que los elementos con clase `texto-destacado` tengan `font-weight: bold` y `color: #c00`.
3. **Selector de ID:** Que el elemento con ID `titulo-principal` tenga `font-family: Georgia` y `text-align: center`.

```css
/* Escribe tu solución aquí */
p { }

.texto-destacado { }

#titulo-principal { }
```

**✅ Resultado esperado:** El h1 centrado en Georgia, los párrafos especiales en rojo negrita, el párrafo normal en gris.

---

## Ejercicio 3 — Combinadores

**Objetivo:** Practicar el selector combinador descendiente.

Dado este HTML:
```html
<nav>
  <a href="#">Inicio</a>
  <a href="#">Blog</a>
  <a href="#">Contacto</a>
</nav>

<footer>
  <a href="#">Aviso legal</a>
</footer>
```

Escribe un selector combinador para que **solo los `<a>` dentro de `<nav>`** tengan `color: white` y `text-decoration: none`, sin afectar el enlace del footer.

```css
/* Tu solución: */
```

**✅ Pista:** Usa `nav a { }`.

---

## Ejercicio 4 — Propiedades de texto

**Objetivo:** Practicar las propiedades de estilado de texto sobre tu blog.

Aplicar a los elementos de tu blog (archivo HTML del ejercicio anterior o tu blog de semana 2):

| Elemento | Propiedad | Valor sugerido |
|----------|-----------|----------------|
| `body` | `font-family` | `Arial, Helvetica, sans-serif` |
| `h1` | `font-size` | `2rem` |
| `h1` | `text-transform` | `uppercase` |
| `h2` | `font-size` | `1.5rem` |
| `p` | `font-size` | `1rem` |
| `p` | `text-align` | `left` |
| `a` | `text-decoration` | `none` |

Escribe las reglas CSS en tu hoja de estilos y verifica el resultado en el navegador.

---

## Ejercicio 5 — Formatos de color

**Objetivo:** Reconocer y utilizar los distintos formatos de color en CSS.

Dado el siguiente resultado visual esperado, escribe el mismo color en los **4 formatos** indicados:

**Color:** Rojo puro `#ff0000`

```css
/* Hexadecimal */
h1 { color: #ff0000; }

/* RGB */
h1 { color: rgb(_____, _____, _____); }

/* RGBA con 50% de opacidad */
h1 { color: rgba(_____, _____, _____, _____); }

/* Por nombre */
h1 { color: _____; }
```

**Desafío adicional:** Usa [Adobe Color](https://color.adobe.com) para crear una paleta de 3 colores para tu blog y aplícalos como `background-color` en el `header`, `main` y `footer`.

---

## Ejercicio 6 — Herencia en CSS

**Objetivo:** Comprender cómo funciona la herencia entre padres e hijos.

Dado este HTML:
```html
<body>
  <h1>Título principal</h1>
  <p>Párrafo de texto.</p>
  <ul>
    <li>Elemento de lista</li>
  </ul>
</body>
```

1. Agrega al CSS: `body { font-family: 'Georgia', serif; color: #222; }`.
2. Abre en el navegador. ¿Qué elementos heredaron la fuente y el color?
3. Ahora agrega: `h1 { font-family: 'Arial', sans-serif; }`.
4. ¿Qué cambió? ¿Qué elementos siguen usando Georgia?

**Responde:**
- ¿Qué significa que CSS sea "en cascada"?
- ¿Qué ventaja tiene declarar `font-family` en `body` en lugar de en cada elemento?

---

## Ejercicio 7 — Fondo de pantalla

**Objetivo:** Aplicar background-color y background-image.

1. Agrega un color de fondo al `header`:
   ```css
   header {
     background-color: #1a1a2e;
   }
   ```
2. Agrega una imagen de fondo al `body` (usa cualquier imagen de tu proyecto o una de internet):
   ```css
   body {
     background-image: url("assets/img/fondo.jpg");
     background-repeat: no-repeat;
   }
   ```
3. Prueba los valores `repeat`, `repeat-x` y `repeat-y`. ¿Qué hace cada uno?

---

## Ejercicio Final — Aplicar todo a tu blog

**Objetivo:** Integrar todos los conceptos de la semana en tu blog de semana 2.

Crea o mejora el archivo `estilos.css` para tu blog aplicando:

- [ ] Hoja CSS externa vinculada a los 5 archivos HTML
- [ ] `font-family` definida en `body` (herencia para todo el sitio)
- [ ] `color` y `font-size` para h1, h2 y párrafos
- [ ] `text-align` para los títulos
- [ ] `background-color` en al menos 2 secciones (header, footer, etc.)
- [ ] Al menos 1 clase CSS aplicada a un elemento
- [ ] Al menos 1 combinador CSS para estilar elementos dentro de una sección

> 📌 Este ejercicio te prepara directamente para la **Actividad Formativa de la semana 3**.

---

*Diseño Web Básico · EXP2 Semana 3 · Campus Virtual DUOC UC*
