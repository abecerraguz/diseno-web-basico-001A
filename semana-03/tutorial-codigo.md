# Tutorial · Semana 3 — Mi primera hoja de estilos
**Diseño Web Básico · EXP2 - Semana 3**

> 🎯 **Qué vas a lograr:** crear una hoja de estilos externa, vincularla a todas las páginas de un sitio y dar estilo a títulos, párrafos y fondos con selectores de **elemento**, **clase** y **combinadores**.
>
> 🍲 **Proyecto de práctica:** trabajaremos con el **Blog de Cocina Chilena**, el proyecto demo de la clase. **No es tu entrega**: sigue los pasos en el demo y después aplica lo aprendido a **tu propio blog**, con tus colores, tus clases y tus decisiones.

**Herramientas:** VS Code (o tu editor) y un navegador (Chrome o Firefox).
**Tiempo estimado:** 60 a 90 minutos.

---

## La estructura de la que partimos

El demo tiene 5 páginas HTML, igual que el blog de la semana 2:

```
blog-cocina/
├── index.html
├── platos-de-fondo/
│   ├── charquican.html
│   └── bife-a-lo-pobre.html
├── postres/
│   ├── tiramisu.html
│   └── papayas-a-la-crema.html
└── assets/
    ├── css/
    └── img/
```

---

## Paso 1 · Crear la hoja de estilos

**Meta:** tener un archivo CSS en la ubicación que recomienda la guía.

**Haz esto:**
1. Dentro de `assets/css/`, crea un archivo llamado `style.css`.
2. Escribe un comentario de encabezado. Te ayuda a ti y a quien revise tu trabajo:
   ```css
   /* ==========================================
      Blog de Cocina Chilena — Hoja de estilos
      Ubicación: assets/css/style.css
      ========================================== */
   ```
3. Guarda el archivo.

**Comprueba:** en el explorador de VS Code ves `assets/css/style.css`, con la extensión `.css` (no `.css.txt`).

**Errores frecuentes:**
- Crear el archivo en la raíz y no dentro de `assets/css/`.
- Usar mayúsculas o espacios en el nombre (`Style.css`, `mi estilo.css`). En el servidor, `Style.css` y `style.css` son archivos **distintos**.

---

## Paso 2 · Vincular la hoja en las 5 páginas

**Meta:** que todas las páginas usen la misma hoja de estilos.

**Haz esto:**
1. Abre `index.html` y, en el `<head>`, **debajo del `<title>`**, agrega:
   ```html
   <link rel="stylesheet" href="assets/css/style.css">
   ```
2. En las páginas que están **dentro de una subcarpeta** (`platos-de-fondo/` y `postres/`), la ruta sube un nivel con `../`:
   ```html
   <link rel="stylesheet" href="../assets/css/style.css">
   ```
3. Para probar el vínculo, escribe en `style.css` una regla temporal:
   ```css
   body {
     background-color: yellow;
   }
   ```

**Comprueba:** abre cada una de las 5 páginas en el navegador. **Todas** deben verse con fondo amarillo. Cuando lo confirmes, borra la regla temporal.

**Errores frecuentes:**
- Usar `href="assets/css/style.css"` en las subpáginas: la ruta no existe desde ahí y la página queda sin estilos.
- Poner el `<link>` dentro del `<body>`.
- Olvidar `rel="stylesheet"`.

---

## Paso 3 · Estilos generales en `body` (herencia)

**Meta:** definir la tipografía y los colores base una sola vez, para que los herede todo el sitio.

**Haz esto:**
1. Escribe la regla de `body` con una **lista de fuentes** de respaldo:
   ```css
   body {
     font-family: Arial, Helvetica, sans-serif;
     font-size: 16px;
     color: #3d2f23;
     background-color: #faf6ef;
     margin: 0;
   }
   ```
2. Guarda y recarga el navegador.

**Comprueba:** los títulos, párrafos y listas cambiaron de fuente y de color **aunque no les escribiste ninguna regla**. Eso es la herencia.

**Errores frecuentes:**
- Escribir nombres de fuente de varias palabras sin comillas: `Trebuchet MS` va como `"Trebuchet MS"`.
- Olvidar el `;` al final de una declaración. La línea siguiente deja de funcionar.

---

## Paso 4 · Selector de elemento: títulos y párrafos

**Meta:** dar estilo a **todas** las etiquetas de un mismo tipo.

**Haz esto:**
1. Dale al `h1` del demo una fuente distinta a la del `body`:
   ```css
   h1 {
     font-family: Georgia, "Times New Roman", serif;
     font-size: 40px;
     font-weight: bold;
     text-align: center;
   }
   ```
2. Repite la idea con `h2` y `p`. En el demo, el `h2` va en color terracota (`#a8512e`) y el `p` queda alineado a la izquierda.

**Comprueba:** abre una receta y el inicio. El `h1` se ve igual en las 5 páginas, porque la regla vive en un solo archivo.

**Errores frecuentes:**
- Escribir el selector con signos de HTML: `<h1> { }` no funciona; es `h1 { }`.
- Usar `text-align: justify` en textos largos: dificulta la lectura en pantalla.

---

## Paso 5 · Selector de clase: las zonas del sitio

**Meta:** dar estilo a partes específicas de la página con nombres propios.

**Haz esto:**
1. En el HTML, ponle una clase a cada zona. En el demo:
   ```html
   <header class="cabecera"> … </header>
   <nav class="navegacion"> … </nav>
   <main class="contenido"> … </main>
   <footer class="pie-pagina"> … </footer>
   ```
2. En el CSS, las clases se escriben con **punto**:
   ```css
   .cabecera {
     background-color: #4a3221;
     color: #faf6ef;
     text-align: center;
   }
   ```
3. Repite lo mismo para `.navegacion` y `.pie-pagina`. En el demo, la navegación usa `#6b4a2f` y el pie usa el mismo café oscuro de la cabecera.

**Comprueba:** la cabecera y el pie tienen fondo café **en las 5 páginas**. Si una página no cambia, revisa que tenga la clase en su HTML.

**Errores frecuentes:**
- Olvidar el punto: `cabecera { }` busca una etiqueta `<cabecera>`, que no existe.
- Nombres con mayúsculas, tildes o espacios (`class="Cabecera Principal"`). Usa minúsculas y guiones: `cabecera-principal`.
- Poner la clase solo en `index.html` y no en las demás páginas.

> 💡 En tu blog, elige nombres que describan **tus** zonas. No tienen por qué ser los mismos del demo.

---

## Paso 6 · Combinadores: estilos según dónde está el elemento

**Meta:** dar estilo a un elemento **solo cuando está dentro** de otro.

**Haz esto:**
1. El `p` de la cabecera debe verse distinto a los párrafos del contenido. Usa un **combinador descendiente** (un espacio entre los dos selectores):
   ```css
   .cabecera p {
     color: #e8dac5;
   }
   ```
2. Haz lo mismo con los enlaces del menú: `.navegacion a { … }`, con color claro y en negrita.

**Comprueba:** los párrafos del contenido **no** cambiaron; solo cambió el de la cabecera.

**Errores frecuentes:**
- Escribir `.cabecera, p` (con coma): eso aplica la regla a la cabecera **y a todos los párrafos**. El combinador es un **espacio**.
- Escribir `.cabecerap`, sin el espacio.

---

## Paso 7 · Imagen de fondo

**Meta:** usar `background-image` con una ruta correcta.

**Haz esto:**
1. Guarda una imagen decorativa en `assets/img/`. En la clase usamos `pizza.png`.
2. En `style.css`, la ruta se escribe **desde el archivo CSS**. Como `style.css` está en `assets/css/`, hay que subir un nivel:
   ```css
   body {
     background-image: url("../img/pizza.png");
     background-repeat: no-repeat;
   }
   ```
3. Prueba los valores `repeat`, `repeat-x` y `repeat-y` para ver qué hace cada uno.

**Comprueba:** la imagen aparece en las 5 páginas, incluidas las de las subcarpetas.

**Errores frecuentes:**
- Escribir la ruta pensando en el HTML (`url("assets/img/pizza.png")`): desde `assets/css/` esa ruta no existe.
- Usar una imagen de fondo que tapa el texto. Revisa que el texto se siga leyendo bien.

---

## Paso 8 · Revisar el contraste

**Meta:** que tus textos se lean bien. Es un criterio de accesibilidad.

**Haz esto:**
1. Abre un verificador de contraste, por ejemplo el [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).
2. Ingresa el color del texto y el color del fondo de cada combinación de tu sitio.
3. Para texto normal, busca al menos **4,5:1** (nivel **AA**). El nivel **AAA** pide **7:1**.

**Comprueba con un caso real del demo:**
| Texto | Fondo | Contraste | Resultado |
|---|---|---|---|
| `#3d2f23` (texto) | `#faf6ef` (fondo) | 11,96:1 | ✅ AA y AAA |
| `#a8512e` (enlace) | `#f3e9d8` (tarjeta) | 4,49:1 | ❌ Se queda corto para AA por milésimas |
| `#8f4426` (enlace más oscuro) | `#f3e9d8` (tarjeta) | 5,78:1 | ✅ AA (no alcanza AAA) |

**Errores frecuentes:**
- Fiarse del ojo: un color que «se ve bien» en tu pantalla puede no cumplir.
- Redondear: 4,49 **no** es 4,5.

---

## Paso 9 · Ordenar y validar el código

**Meta:** entregar código limpio. La escala también evalúa la indentación, los comentarios y el estándar W3C.

**Haz esto:**
1. Agrupa tus reglas con comentarios: generales, elementos, clases y combinadores.
2. Revisa la indentación (en VS Code: clic derecho → *Dar formato al documento*).
3. Valida cada página HTML en <https://validator.w3.org/#validate_by_input> (pegando el código) y tu CSS en <https://jigsaw.w3.org/css-validator/#validate_by_input>.

**Comprueba:** el validador muestra **0 errores** en las 5 páginas y en el CSS.

**Errores frecuentes:**
- Dejar estilos dentro del HTML (`style=""` o `<style>`). Esta semana todo va en la hoja externa.
- Etiquetas sin cerrar, que el validador marca como error.

---

## Paso 10 · Publicar en el hosting de Duoc

**Meta:** que el sitio se vea desde internet con su URL.

**Haz esto:**
1. Entra al hosting de Duoc con los datos que entrega el AVA.
2. Sube la carpeta **completa**, respetando la estructura: `index.html` en la raíz, junto a las subcarpetas y `assets/`.
3. Abre la URL de tu sitio en el navegador.

**Comprueba:** desde la URL, navega por las 5 páginas. Todas deben tener estilos y mostrar sus imágenes.

**Errores frecuentes:**
- Subir solo los HTML y olvidar la carpeta `assets/`: el sitio se ve sin estilos.
- Diferencias de mayúsculas entre el nombre del archivo y la ruta. En tu computador puede funcionar y en el servidor no.
- Revisar solo en tu computador y no en la URL.

---

## ✅ Checklist final

- [ ] Existe `assets/css/style.css` y está vinculado en las **5** páginas, con la ruta correcta en cada una.
- [ ] No hay estilos dentro del HTML: ni `style=""` ni `<style>`.
- [ ] Usé selectores de **elemento**, de **clase** y **combinadores**.
- [ ] Los párrafos y encabezados tienen `font-family`, `font-size`, `font-weight` y `text-align`.
- [ ] Usé `background-color` y/o `background-image`.
- [ ] Revisé el contraste de mis colores (mínimo 4,5:1 para texto normal).
- [ ] El HTML y el CSS pasan el validador del W3C sin errores.
- [ ] El sitio está publicado y probé las 5 páginas desde la URL.

## ❓ Preguntas de repaso

1. ¿Cuáles son las partes de una regla CSS y qué signo separa una declaración de otra?
2. ¿Por qué la hoja externa es mejor que el estilo en línea?
3. ¿Qué diferencia hay entre `.cabecera p` y `.cabecera, p`?
4. Si declaras `font-family` en `body`, ¿por qué no necesitas repetirla en cada párrafo?
5. ¿Por qué una página dentro de una subcarpeta necesita `../` en la ruta del `<link>`?
6. ¿Qué contraste mínimo pide el nivel AA para texto normal? ¿Y el AAA?

## 📤 Entrega

Aplica estos pasos a **tu propio blog** (no entregues el demo). Según la actividad formativa *Aplicando CSS en una estructura HTML*, debes entregar por **AVA**:

- la carpeta de tu sitio comprimida en **.zip**;
- tu sitio **subido al hosting de Duoc**, con la **URL** copiada en el documento de la actividad.

📅 Plazo: **lunes 9 de noviembre de 2026, 23:59 hrs.**

---

*Diseño Web Básico · EXP2 Semana 3 · Campus Virtual DUOC UC*
