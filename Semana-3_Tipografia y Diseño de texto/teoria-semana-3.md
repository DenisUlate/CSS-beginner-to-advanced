# 📝 Tipografía & Diseño de Texto - Semana 3

## 📖 Introducción

La tipografía es **uno de los pilares fundamentales del diseño web**. Controlar cómo se ve el texto no solo afecta la estética, sino también la **legibilidad, accesibilidad y experiencia del usuario**. En esta semana aprenderás a dominar todas las propiedades tipográficas de CSS moderno.

---

## 1️⃣ Font-Family y Font Stacks

### 📖 Teoría

`font-family` define la familia de fuentes que se usará para el texto. Como no todos los navegadores tienen las mismas fuentes instaladas, se usa un **font stack**: una lista de fuentes alternativas en orden de prioridad.

### 💡 Concepto Clave

Siempre proporciona fuentes alternativas y termina con una fuente genérica (`serif`, `sans-serif`, `monospace`, `cursive`, `fantasy`).

### 🛠️ Ejemplo Básico

```css
/* Font stack seguro */
body {
	font-family: Arial, Helvetica, sans-serif;
}

h1 {
	font-family: Georgia, "Times New Roman", serif;
}

code {
	font-family: "Courier New", Courier, monospace;
}
```

### 🚀 Ejemplo Moderno (2025)

```css
/* Fuente del sistema (más rápida) */
body {
	font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
}

/* Google Fonts */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@300..900&display=swap");

body {
	font-family: "Inter", system-ui, sans-serif;
}
```

### 🔄 Alternativas

1. **System Fonts**: Más rápidas, ya están instaladas

   - Pros: Performance excelente, look nativo
   - Contras: Menos control creativo

2. **Google Fonts**: Biblioteca gratuita enorme

   - Pros: Miles de fuentes, fácil implementación
   - Contras: Requiere conexión externa

3. **@font-face**: Hospedas tus propias fuentes
   - Pros: Control total, privacidad
   - Contras: Debes gestionar archivos

### ✅ Recomendación 2025

Usa **Google Fonts con `display=swap`** para proyectos profesionales, o **system fonts** para máxima performance.

---

## 2️⃣ Font-Size y Escalas Tipográficas

### 📖 Teoría

`font-size` controla el tamaño del texto. Una **escala tipográfica** es un sistema proporcional de tamaños que crea jerarquía visual consistente.

### 💡 Concepto Clave

Usa unidades relativas (`rem`, `em`) y funciones modernas (`clamp()`) para tipografía responsive.

### 🛠️ Ejemplo Básico

```css
/* Tamaños fijos */
h1 {
	font-size: 32px;
}
h2 {
	font-size: 24px;
}
p {
	font-size: 16px;
}
```

### 🚀 Ejemplo Moderno (2025)

```css
/* Base: 1rem = 16px (por defecto) */
:root {
	font-size: 16px; /* Base */
}

/* Escala tipográfica con clamp() - RESPONSIVE */
h1 {
	font-size: clamp(2rem, 5vw + 1rem, 3.5rem);
	/* Mínimo 32px, fluido, máximo 56px */
}

h2 {
	font-size: clamp(1.5rem, 3vw + 0.5rem, 2.5rem);
}

h3 {
	font-size: clamp(1.25rem, 2vw + 0.5rem, 2rem);
}

p {
	font-size: clamp(1rem, 1vw + 0.5rem, 1.125rem);
}
```

### 🔄 Escalas Tipográficas Populares

1. **Escala Mayor (1.25)**: 16px → 20px → 25px → 31px → 39px
2. **Escala Perfecta 4ta (1.333)**: 16px → 21px → 28px → 37px → 50px
3. **Escala Áurea (1.618)**: 16px → 26px → 42px → 68px

### ✅ Recomendación 2025

Usa `clamp()` para tipografía fluida que se adapte automáticamente sin media queries.

### 📌 Caso de Uso Real

```css
/* Blog profesional */
article {
	font-size: clamp(1rem, 0.9rem + 0.5vw, 1.125rem);
	line-height: 1.7;
	max-inline-size: 65ch; /* Máximo 65 caracteres por línea */
}
```

---

## 3️⃣ Font-Weight y Font-Style

### 📖 Teoría

`font-weight` controla el grosor del texto (100-900), y `font-style` define variantes como cursiva.

### 🛠️ Ejemplo Básico

```css
/* Pesos nombrados */
.light {
	font-weight: 300;
}
.regular {
	font-weight: 400;
} /* normal */
.bold {
	font-weight: 700;
} /* bold */

/* Estilos */
.italic {
	font-style: italic;
}
.oblique {
	font-style: oblique;
}
```

### 🚀 Ejemplo Moderno con Variable Fonts (2025)

```css
/* Variable Fonts permiten cualquier valor entre min-max */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap");

h1 {
	font-family: "Inter", sans-serif;
	font-weight: 850; /* Valor intermedio preciso */
}

/* Animación suave de peso */
.hover-text {
	font-weight: 400;
	transition: font-weight 0.3s ease;
}

.hover-text:hover {
	font-weight: 700;
}
```

### ✅ Recomendación 2025

Usa **Variable Fonts** para tener control granular y mejor performance que cargar múltiples archivos de peso.

---

## 4️⃣ Line-Height - El Secreto de la Legibilidad

### 📖 Teoría

`line-height` controla el espacio vertical entre líneas de texto. Es **crítico** para la legibilidad.

### 💡 Concepto Clave

Un `line-height` entre 1.5 y 1.8 es óptimo para texto de lectura. Títulos pueden usar menos (1.1-1.3).

### 🛠️ Ejemplo Básico

```css
p {
	font-size: 16px;
	line-height: 1.6; /* 25.6px de altura */
}

h1 {
	font-size: 48px;
	line-height: 1.2; /* 57.6px */
}
```

### 🚀 Ejemplo Moderno (2025)

```css
/* Sin unidad = relativo al font-size (MEJOR) */
body {
	font-size: 1rem;
	line-height: 1.6;
}

/* Para diferentes contextos */
.heading {
	line-height: 1.2; /* Títulos más compactos */
}

.body-text {
	line-height: 1.7; /* Lectura confortable */
}

.code {
	line-height: 1.4; /* Código más denso */
}

/* Ajuste dinámico */
.article {
	line-height: calc(1.5 + 0.2 * (100vw - 320px) / 680);
}
```

### ✅ Recomendación 2025

**Nunca uses unidades** (como px o rem) para `line-height`, usa valores numéricos para que hereden proporcionalmente.

---

## 5️⃣ Letter-Spacing y Word-Spacing

### 📖 Teoría

`letter-spacing` ajusta el espacio entre caracteres. `word-spacing` ajusta el espacio entre palabras.

### 🛠️ Ejemplos Prácticos

```css
/* Letter-spacing */
.heading {
	letter-spacing: -0.02em; /* Títulos más compactos */
}

.all-caps {
	text-transform: uppercase;
	letter-spacing: 0.1em; /* MAYÚSCULAS necesitan más espacio */
}

.logo {
	letter-spacing: 0.2em; /* Efecto espaciado */
}

/* Word-spacing */
.spaced-text {
	word-spacing: 0.3em; /* Más aire entre palabras */
}
```

### 🚀 Ejemplo Moderno (2025)

```css
/* Ajuste responsivo */
h1 {
	letter-spacing: clamp(-0.05em, -0.02em + -0.01vw, -0.01em);
}

/* Para accesibilidad en dislexia */
.readable-text {
	letter-spacing: 0.12em;
	word-spacing: 0.16em;
	line-height: 1.8;
}
```

### ✅ Recomendación 2025

Usa `em` para que el espaciado escale proporcionalmente con el `font-size`.

---

## 6️⃣ Text-Align, Text-Decoration y Text-Transform

### 🛠️ Text-Align

```css
.left {
	text-align: left;
}
.center {
	text-align: center;
}
.right {
	text-align: right;
}
.justify {
	text-align: justify;
} /* Evitar en web */
```

### 🚀 Text-Align Moderno (2025)

```css
/* Logical Properties */
.start {
	text-align: start;
} /* Se adapta a RTL/LTR */
.end {
	text-align: end;
}
```

### 🛠️ Text-Decoration

```css
a {
	text-decoration: underline;
}

.no-underline {
	text-decoration: none;
}

/* Estilos avanzados */
.fancy-link {
	text-decoration: underline wavy red;
	text-decoration-thickness: 2px;
	text-underline-offset: 4px;
}
```

### 🛠️ Text-Transform

```css
.uppercase {
	text-transform: uppercase;
}
.lowercase {
	text-transform: lowercase;
}
.capitalize {
	text-transform: capitalize;
}
```

---

## 7️⃣ Text-Shadow - Efectos de Texto

### 📖 Teoría

`text-shadow` añade sombras al texto para crear profundidad y efectos visuales.

**Sintaxis:** `text-shadow: offset-x offset-y blur color;`

### 🛠️ Ejemplos Prácticos

```css
/* Sombra simple */
h1 {
	text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

/* Múltiples sombras */
.neon {
	color: white;
	text-shadow: 0 0 10px #00ff00, 0 0 20px #00ff00, 0 0 30px #00ff00;
}

/* Efecto 3D */
.three-d {
	text-shadow: 1px 1px 0 #ccc, 2px 2px 0 #bbb, 3px 3px 0 #aaa, 4px 4px 0 #999, 5px 5px 0 #888;
}
```

### ✅ Recomendación 2025

Usa sombras sutiles (2-4px blur) para mejorar legibilidad sobre imágenes.

---

## 8️⃣ Google Fonts y @font-face

### 📖 Teoría

Para usar fuentes personalizadas, puedes importar desde **Google Fonts** o usar **@font-face** para cargar archivos propios.

### 🚀 Google Fonts (2025)

```html
<!-- En HTML -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700&display=swap" rel="stylesheet" />
```

```css
/* En CSS */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap");

body {
	font-family: "Poppins", sans-serif;
}
```

### 🚀 @font-face (2025)

```css
/* Fuentes auto-hospedadas */
@font-face {
	font-family: "MyCustomFont";
	src: url("/fonts/mycustomfont.woff2") format("woff2"), url("/fonts/mycustomfont.woff") format("woff");
	font-weight: 400;
	font-style: normal;
	font-display: swap; /* IMPORTANTE para performance */
}

body {
	font-family: "MyCustomFont", system-ui, sans-serif;
}
```

### ✅ Recomendación 2025

1. Usa `font-display: swap` siempre
2. Solo carga los pesos que necesitas
3. Prefieres formatos **woff2** (mejor compresión)
4. Usa `preconnect` para Google Fonts

---

## 9️⃣ Variable Fonts - Tecnología 2025

### 📖 Teoría

Los **Variable Fonts** contienen múltiples variaciones (peso, ancho, inclinación) en un solo archivo, permitiendo valores intermedios precisos.

### 🚀 Ejemplo Variable Font

```css
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap");

h1 {
	font-family: "Inter", sans-serif;
	font-weight: 675; /* Cualquier valor entre 100-900 */
	font-variation-settings: "wght" 675, "slnt" -10;
}

/* Animación suave */
.animated-text {
	font-variation-settings: "wght" 400;
	transition: font-variation-settings 0.3s ease;
}

.animated-text:hover {
	font-variation-settings: "wght" 700;
}
```

### ✅ Recomendación 2025

Usa Variable Fonts para **mejor performance** (1 archivo vs múltiples) y animaciones tipográficas suaves.

---

## 🔟 Jerarquía Tipográfica

### 📖 Teoría

La jerarquía tipográfica guía al usuario a través del contenido usando tamaño, peso, color y espaciado.

### 🚀 Sistema Completo de Jerarquía (2025)

```css
:root {
	/* Escala tipográfica */
	--font-size-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
	--font-size-sm: clamp(0.875rem, 0.8rem + 0.3vw, 1rem);
	--font-size-base: clamp(1rem, 0.9rem + 0.5vw, 1.125rem);
	--font-size-lg: clamp(1.25rem, 1.1rem + 0.7vw, 1.5rem);
	--font-size-xl: clamp(1.5rem, 1.3rem + 1vw, 2rem);
	--font-size-2xl: clamp(2rem, 1.5rem + 2vw, 3rem);
	--font-size-3xl: clamp(2.5rem, 2rem + 2.5vw, 4rem);
}

h1 {
	font-size: var(--font-size-3xl);
	font-weight: 700;
	line-height: 1.1;
	letter-spacing: -0.02em;
	margin-block-end: 0.5em;
}

h2 {
	font-size: var(--font-size-2xl);
	font-weight: 600;
	line-height: 1.2;
	margin-block-end: 0.6em;
}

h3 {
	font-size: var(--font-size-xl);
	font-weight: 600;
	line-height: 1.3;
}

p {
	font-size: var(--font-size-base);
	line-height: 1.7;
	margin-block-end: 1em;
}

small {
	font-size: var(--font-size-sm);
}
```

### 📌 Caso de Uso Real: Blog Article

```css
/* Blog profesional completo */
article {
	max-inline-size: 70ch; /* Máximo 70 caracteres por línea */
	margin-inline: auto;
}

article h1 {
	font-size: clamp(2rem, 5vw, 3.5rem);
	font-weight: 800;
	line-height: 1.1;
	letter-spacing: -0.03em;
	margin-block-end: 0.3em;
}

article .subtitle {
	font-size: clamp(1.25rem, 3vw, 1.75rem);
	font-weight: 400;
	color: #666;
	margin-block-end: 2em;
}

article p {
	font-size: clamp(1.063rem, 1.5vw, 1.125rem);
	line-height: 1.8;
	margin-block-end: 1.5em;
}

article blockquote {
	font-size: 1.25em;
	font-style: italic;
	border-inline-start: 4px solid #333;
	padding-inline-start: 1.5em;
	margin-block: 2em;
}
```

---

## 1️⃣1️⃣ Direction y Writing-Mode

### 📖 Teoría

Propiedades para controlar la dirección del texto, útil para idiomas RTL (right-to-left) o diseños verticales.

### 🛠️ Ejemplos

```css
/* Texto de derecha a izquierda (árabe, hebreo) */
.rtl {
	direction: rtl;
}

/* Texto vertical (japonés, chino tradicional) */
.vertical {
	writing-mode: vertical-rl;
}

.vertical-lr {
	writing-mode: vertical-lr;
}
```

---

## ✅ Mejores Prácticas Tipográficas 2025

### 📋 Checklist de Tipografía Profesional

1. **Legibilidad:**

   - ✅ `font-size` mínimo 16px para texto principal
   - ✅ `line-height` entre 1.5-1.8 para lectura
   - ✅ Máximo 65-75 caracteres por línea (`max-inline-size: 70ch`)
   - ✅ Contraste mínimo 4.5:1 (WCAG AA)

2. **Performance:**

   - ✅ Usa `font-display: swap`
   - ✅ Carga solo pesos necesarios
   - ✅ Prefiere Variable Fonts
   - ✅ `preconnect` para fuentes externas

3. **Responsive:**

   - ✅ Usa `clamp()` para tipografía fluida
   - ✅ Unidades relativas (rem, em)
   - ✅ Escala proporcional en todos los tamaños

4. **Accesibilidad:**
   - ✅ No uses `justify` en web
   - ✅ Suficiente `letter-spacing` para dislexia
   - ✅ Contraste adecuado
   - ✅ Tamaños legibles en móvil

---

## 🎨 Ejemplo Completo: Sistema Tipográfico Profesional

```css
/* ========================================
   Sistema Tipográfico Completo 2025
   ======================================== */

/* 1. Import Variable Fonts */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@300..900&family=Merriweather:wght@300;400;700&display=swap");

/* 2. Variables CSS */
:root {
	/* Fuentes */
	--font-sans: "Inter", system-ui, sans-serif;
	--font-serif: "Merriweather", Georgia, serif;
	--font-mono: "Fira Code", "Courier New", monospace;

	/* Escala tipográfica (Perfect Fourth 1.333) */
	--font-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
	--font-sm: clamp(0.875rem, 0.8rem + 0.3vw, 1rem);
	--font-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
	--font-md: clamp(1.125rem, 1rem + 0.6vw, 1.333rem);
	--font-lg: clamp(1.333rem, 1.2rem + 0.7vw, 1.777rem);
	--font-xl: clamp(1.777rem, 1.5rem + 1.4vw, 2.369rem);
	--font-2xl: clamp(2.369rem, 2rem + 1.8vw, 3.157rem);
	--font-3xl: clamp(3.157rem, 2.5rem + 3.3vw, 4.209rem);

	/* Pesos */
	--font-light: 300;
	--font-regular: 400;
	--font-medium: 500;
	--font-semibold: 600;
	--font-bold: 700;
	--font-extrabold: 800;

	/* Line Heights */
	--leading-tight: 1.2;
	--leading-normal: 1.5;
	--leading-relaxed: 1.7;
	--leading-loose: 2;

	/* Letter Spacing */
	--tracking-tight: -0.05em;
	--tracking-normal: 0em;
	--tracking-wide: 0.05em;
}

/* 3. Base Typography */
body {
	font-family: var(--font-sans);
	font-size: var(--font-base);
	line-height: var(--leading-relaxed);
	color: #333;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}

/* 4. Headings */
h1,
h2,
h3,
h4,
h5,
h6 {
	font-family: var(--font-serif);
	font-weight: var(--font-bold);
	line-height: var(--leading-tight);
	letter-spacing: var(--tracking-tight);
	margin-block-start: 1.5em;
	margin-block-end: 0.5em;
}

h1 {
	font-size: var(--font-3xl);
	font-weight: var(--font-extrabold);
}

h2 {
	font-size: var(--font-2xl);
}

h3 {
	font-size: var(--font-xl);
}

h4 {
	font-size: var(--font-lg);
}

h5 {
	font-size: var(--font-md);
}

h6 {
	font-size: var(--font-base);
	font-weight: var(--font-semibold);
}

/* 5. Body Text */
p {
	margin-block-end: 1.5em;
	max-inline-size: 70ch;
}

/* 6. Text Utilities */
.lead {
	font-size: var(--font-lg);
	line-height: var(--leading-relaxed);
	color: #555;
}

.small {
	font-size: var(--font-sm);
}

strong,
b {
	font-weight: var(--font-bold);
}

em,
i {
	font-style: italic;
}

mark {
	background-color: #fff3cd;
	padding-inline: 0.2em;
}

/* 7. Special Elements */
blockquote {
	font-family: var(--font-serif);
	font-size: var(--font-md);
	font-style: italic;
	border-inline-start: 4px solid #333;
	padding-inline-start: 1.5em;
	margin-block: 2em;
	color: #555;
}

code {
	font-family: var(--font-mono);
	font-size: 0.9em;
	background-color: #f5f5f5;
	padding: 0.2em 0.4em;
	border-radius: 3px;
}

pre code {
	display: block;
	padding: 1.5em;
	overflow-x: auto;
	line-height: var(--leading-normal);
}

/* 8. Links */
a {
	color: #0066cc;
	text-decoration: underline;
	text-decoration-thickness: 1px;
	text-underline-offset: 2px;
	transition: color 0.2s ease;
}

a:hover {
	color: #004499;
	text-decoration-thickness: 2px;
}

/* 9. Utility Classes */
.text-center {
	text-align: center;
}
.text-end {
	text-align: end;
}
.text-start {
	text-align: start;
}

.uppercase {
	text-transform: uppercase;
}
.lowercase {
	text-transform: lowercase;
}
.capitalize {
	text-transform: capitalize;
}

.font-light {
	font-weight: var(--font-light);
}
.font-normal {
	font-weight: var(--font-regular);
}
.font-semibold {
	font-weight: var(--font-semibold);
}
.font-bold {
	font-weight: var(--font-bold);
}
```

---

## 🎯 Proyecto Práctico: Blog Article

Aplica todo lo aprendido creando un artículo de blog profesional:

**Requisitos:**

- ✅ Sistema tipográfico con variables CSS
- ✅ 2+ Google Fonts (sans-serif + serif)
- ✅ Jerarquía clara de títulos (h1-h4)
- ✅ `clamp()` para responsive
- ✅ Line-height óptimo (1.7-1.8)
- ✅ Máximo 70ch por línea
- ✅ Text effects (shadows, decorations)
- ✅ Blockquotes estilizadas
- ✅ Links con hover effects

---

## 📚 Recursos Adicionales

- **Google Fonts**: https://fonts.google.com
- **Variable Fonts**: https://v-fonts.com
- **Type Scale**: https://typescale.com
- **Font Pair**: https://fontpair.co

---

¡Domina la tipografía y tus diseños se verán instantáneamente más profesionales! 🎨✨
