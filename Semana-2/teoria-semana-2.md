# 📦 Semana 2: Box Model & Unidades CSS - Teoría Completa

## 📖 Introducción

En esta semana aprenderás uno de los conceptos más fundamentales de CSS: **el Box Model**. Todo elemento HTML es una "caja" rectangular, y entender cómo funcionan estas cajas es esencial para dominar CSS. También aprenderás las diferentes unidades de medida para crear diseños responsive y precisos.

---

## 1️⃣ BOX MODEL: La Base de CSS

### 📖 Teoría

El **Box Model** es el sistema que CSS usa para calcular el espacio que ocupa cada elemento. Cada caja tiene 4 capas desde el interior hacia el exterior: **content** (contenido), **padding** (relleno), **border** (borde) y **margin** (margen).

### 💡 Concepto Clave

Piensa en el Box Model como una caja de regalo: el contenido es el regalo, el padding es el papel de seda que lo protege, el border es la caja misma, y el margin es el espacio entre tu regalo y otros regalos.

### 🛠️ Ejemplo Básico

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Ejemplo: Box Model</title>
		<style>
			.caja {
				/* Content: El área del contenido */
				width: 200px;
				height: 100px;

				/* Padding: Espacio interno entre contenido y borde */
				padding: 20px;

				/* Border: El borde de la caja */
				border: 5px solid #3498db;

				/* Margin: Espacio externo entre esta caja y otros elementos */
				margin: 30px;

				background-color: #ecf0f1;
			}
		</style>
	</head>
	<body>
		<div class="caja">Este es el contenido (content)</div>
	</body>
</html>
```

**Tamaño total de la caja:**

- Ancho total = 200px (content) + 40px (padding) + 10px (border) + 60px (margin) = **310px**
- Alto total = 100px (content) + 40px (padding) + 10px (border) + 60px (margin) = **210px**

### 🚀 Visualización del Box Model

```css
/* Usa DevTools de Chrome/Firefox (F12) para ver el Box Model visualmente */
.ejemplo-visual {
	width: 300px;
	padding: 30px; /* Capa verde en DevTools */
	border: 10px solid; /* Capa amarilla en DevTools */
	margin: 20px; /* Capa naranja en DevTools */
}
```

---

## 2️⃣ BOX-SIZING: content-box vs border-box

### 📖 Teoría

`box-sizing` determina **cómo se calcula el width y height** de un elemento. Hay dos valores principales: `content-box` (predeterminado) y `border-box` (recomendado en 2025).

### 💡 Concepto Clave

**`content-box`**: width/height solo aplica al contenido. Padding y border se suman.
**`border-box`**: width/height incluye contenido, padding Y border. ¡Mucho más intuitivo!

### 🛠️ Ejemplo Comparativo

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<style>
			.content-box {
				box-sizing: content-box; /* Predeterminado */
				width: 200px;
				padding: 20px;
				border: 5px solid red;
				/* Ancho real = 200 + 40 + 10 = 250px */
			}

			.border-box {
				box-sizing: border-box; /* Recomendado */
				width: 200px;
				padding: 20px;
				border: 5px solid blue;
				/* Ancho real = 200px (ya incluye padding y border) */
			}
		</style>
	</head>
	<body>
		<div class="content-box">Content-box: 250px total</div>
		<div class="border-box">Border-box: 200px total</div>
	</body>
</html>
```

### 🚀 Método Moderno (2025)

```css
/* SIEMPRE usa esto al inicio de tus proyectos */
*,
*::before,
*::after {
	box-sizing: border-box;
}

/* Ahora todos los elementos usan border-box por defecto */
.caja {
	width: 300px; /* Esto será EXACTAMENTE 300px sin importar padding/border */
	padding: 50px;
	border: 10px solid;
}
```

### ✅ Recomendación

**SIEMPRE usa `border-box`** en proyectos modernos. Es más intuitivo y predecible. Aplica el reset universal al inicio de tu CSS.

---

## 3️⃣ UNIDADES ABSOLUTAS: px, pt, cm

### 📖 Teoría

Las **unidades absolutas** tienen un tamaño fijo independiente del contexto. Son útiles para dimensiones precisas, pero menos flexibles para diseños responsive.

### 💡 Concepto Clave

Las unidades absolutas son como una regla: siempre miden lo mismo sin importar dónde estés.

### 🛠️ Unidades Comunes

```css
.ejemplo-absolutas {
	/* PÍXELES (px) - La más común */
	width: 300px;
	border: 2px solid;

	/* PUNTOS (pt) - Usados principalmente para impresión */
	font-size: 12pt;

	/* CENTÍMETROS (cm) - Raramente usados */
	margin: 1cm;

	/* MILÍMETROS (mm) - Raramente usados */
	padding: 10mm;

	/* PULGADAS (in) - Raramente usados */
	width: 2in;
}
```

### 🔄 Cuándo Usar Cada Una

1. **px (píxeles)**:

   - ✅ Borders, shadows, detalles pequeños
   - ❌ Font sizes (usa rem en su lugar)
   - ❌ Widths/heights principales (usa %, rem, vw/vh)

2. **pt (puntos)**:

   - ✅ Hojas de estilo para impresión (@media print)
   - ❌ Diseño web general

3. **cm, mm, in**:
   - ✅ CSS para documentos imprimibles
   - ❌ Diseño web (son inconsistentes entre pantallas)

### ✅ Recomendación 2025

Usa **px solo para detalles pequeños** como borders y shadows. Para tamaños de texto y layouts, prefiere unidades relativas.

---

## 4️⃣ UNIDADES RELATIVAS: %, em, rem, vw, vh, vmin, vmax

### 📖 Teoría

Las **unidades relativas** se calculan en base a otro valor (elemento padre, viewport, raíz del documento). Son esenciales para diseños responsive y accesibles.

### 💡 Concepto Clave

Las unidades relativas son como decir "la mitad de mi contenedor" o "el doble del tamaño base" - se adaptan al contexto.

### 🛠️ % (Porcentaje)

```html
<!DOCTYPE html>
<html>
	<head>
		<style>
			.padre {
				width: 500px;
				height: 300px;
				background: #3498db;
				padding: 20px;
			}

			.hijo {
				width: 50%; /* 50% del padre = 250px */
				height: 80%; /* 80% del padre = 240px */
				background: #e74c3c;
				padding: 5%; /* 5% del ANCHO del padre = 25px */
			}
		</style>
	</head>
	<body>
		<div class="padre">
			<div class="hijo">Hijo con 50% width</div>
		</div>
	</body>
</html>
```

**⚠️ Importante**: El porcentaje siempre es relativo al **elemento padre**.

### 🛠️ em (Relativo al font-size del elemento)

```css
.ejemplo-em {
	font-size: 20px;

	/* 'em' se basa en el font-size del elemento actual */
	padding: 1em; /* = 20px (1 × 20px) */
	margin: 0.5em; /* = 10px (0.5 × 20px) */
	border-radius: 2em; /* = 40px (2 × 20px) */
}

/* ⚠️ CUIDADO: em se acumula en elementos anidados */
.padre-em {
	font-size: 16px; /* Base */
}

.hijo-em {
	font-size: 1.5em; /* = 24px (1.5 × 16px) */
}

.nieto-em {
	font-size: 1.5em; /* = 36px (1.5 × 24px) - ¡Se acumula! */
}
```

### 🚀 rem (Relativo al font-size del ROOT - `<html>`)

```css
/* Método Moderno 2025: rem es MUCHO mejor que em para tamaños */

html {
	font-size: 16px; /* Base global */
}

.ejemplo-rem {
	font-size: 1.5rem; /* = 24px (1.5 × 16px) */
	padding: 2rem; /* = 32px (2 × 16px) */
	margin: 0.5rem; /* = 8px (0.5 × 16px) */
}

/* rem NO se acumula - siempre relativo a <html> */
.padre-rem {
	font-size: 2rem; /* = 32px */
}

.hijo-rem {
	font-size: 1.5rem; /* = 24px (aún basado en 16px de html) */
}
```

**✅ Ventaja de rem**: Permite que los usuarios cambien el tamaño de fuente base y todo se escala automáticamente (accesibilidad).

### 🛠️ vw/vh (Viewport Width/Height)

```css
/* Unidades relativas al tamaño del viewport (ventana del navegador) */

.hero-section {
	width: 100vw; /* 100% del ancho del viewport */
	height: 100vh; /* 100% del alto del viewport */
	/* Perfecto para secciones a pantalla completa */
}

.responsive-text {
	font-size: 5vw; /* 5% del ancho del viewport */
	/* En viewport de 1000px = 50px */
	/* En viewport de 500px = 25px */
}

.sidebar {
	width: 25vw; /* Siempre el 25% del ancho del viewport */
}
```

**⚠️ Cuidado**: `vw` incluye la barra de scroll, puede causar scroll horizontal.

### 🛠️ vmin/vmax (Viewport Mínimo/Máximo)

```css
/* vmin: el MENOR entre vw o vh */
/* vmax: el MAYOR entre vw o vh */

.cuadrado-responsive {
	width: 50vmin; /* En landscape: 50vh, en portrait: 50vw */
	height: 50vmin; /* Siempre un cuadrado perfecto */
}

.texto-adaptable {
	font-size: 3vmin; /* Se adapta mejor a todas las orientaciones */
}

.cover-image {
	min-width: 100vmax; /* Siempre cubre toda la pantalla */
	min-height: 100vmax;
}
```

### 🔄 Comparación de Unidades Relativas

| Unidad | Relativo a             | Uso Principal                     | 2025                 |
| ------ | ---------------------- | --------------------------------- | -------------------- |
| `%`    | Elemento padre         | Layouts, widths                   | ✅ Común             |
| `em`   | Font-size del elemento | Spacing interno de componentes    | ⚠️ Usar con cuidado  |
| `rem`  | Font-size de `<html>`  | Font-sizes, spacing global        | ✅ **Recomendado**   |
| `vw`   | Ancho del viewport     | Layouts fluidos, text responsive  | ✅ Común             |
| `vh`   | Alto del viewport      | Secciones full-height             | ✅ Común             |
| `vmin` | Menor entre vw/vh      | Elementos que deben caber siempre | ✅ Útil              |
| `vmax` | Mayor entre vw/vh      | Backgrounds que cubren todo       | ⚠️ Casos específicos |

### ✅ Recomendación 2025

- **Layouts**: `%`, `vw`, `vh`
- **Font-sizes**: `rem` (SIEMPRE)
- **Spacing (padding/margin)**: `rem`
- **Borders/shadows**: `px`
- **Responsive components**: `vw`, `vh`, `vmin`

---

## 5️⃣ FUNCIONES: calc(), min(), max(), clamp()

### 📖 Teoría

Las **funciones CSS** permiten realizar cálculos dinámicos para crear diseños más flexibles y responsive. Son herramientas poderosas de CSS moderno.

### 🛠️ calc() - Cálculos Matemáticos

```css
/* calc() permite mezclar unidades y hacer operaciones */

.ejemplo-calc {
	/* Ancho del contenedor menos padding */
	width: calc(100% - 40px);

	/* Altura del viewport menos header y footer */
	height: calc(100vh - 120px);

	/* Centrar absolutamente con calc */
	position: absolute;
	left: calc(50% - 150px); /* Asumiendo width: 300px */

	/* Cálculos complejos */
	padding: calc(2rem + 10px);
	font-size: calc(1rem + 0.5vw);
}

/* Caso Real: Grid con gaps */
.grid-item {
	/* 3 columnas con 20px de gap entre ellas */
	width: calc((100% - 40px) / 3);
}
```

**✅ Ventaja**: Mezcla diferentes unidades en un solo cálculo.

### 🚀 min() - El Valor MENOR

```css
/* min() elige el valor MÁS PEQUEÑO */

.ejemplo-min {
	/* Nunca será mayor a 600px, pero puede ser más pequeño */
	width: min(100%, 600px);
	/* = 100% en pantallas pequeñas, 600px en grandes */

	/* Padding responsive con límite */
	padding: min(5vw, 3rem);
	/* = 5vw en pantallas pequeñas, máximo 3rem */

	/* Font-size con límite superior */
	font-size: min(4vw, 2rem);
}
```

**💡 Piénsalo como**: "Usa este valor, pero nunca más grande que..."

### 🚀 max() - El Valor MAYOR

```css
/* max() elige el valor MÁS GRANDE */

.ejemplo-max {
	/* Nunca será menor a 300px, pero puede ser más grande */
	width: max(50%, 300px);
	/* = 300px en pantallas pequeñas, 50% en grandes */

	/* Font-size con mínimo legible */
	font-size: max(16px, 1rem);

	/* Padding con valor mínimo */
	padding: max(20px, 2vw);
}
```

**💡 Piénsalo como**: "Usa este valor, pero nunca más pequeño que..."

### 🚀 clamp() - Valor con MÍNIMO y MÁXIMO

```css
/* clamp(MÍNIMO, PREFERIDO, MÁXIMO) - LA FUNCIÓN MÁS PODEROSA 2025 */

.ejemplo-clamp {
	/* Tipografía fluida responsive */
	font-size: clamp(1rem, 2vw + 0.5rem, 3rem);
	/* = 1rem (móvil), crece con viewport, máximo 3rem (desktop) */

	/* Width responsive con límites */
	width: clamp(300px, 50%, 800px);
	/* = 300px mínimo, 50% del contenedor, 800px máximo */

	/* Padding adaptable */
	padding: clamp(1rem, 5vw, 5rem);

	/* Margin lateral responsive */
	margin-inline: clamp(1rem, 5%, 10rem);
}

/* Caso Real: Tipografía Fluida Perfecta */
h1 {
	font-size: clamp(2rem, 5vw + 1rem, 5rem);
	/* Móvil: 2rem, Tablet: 3-4rem, Desktop: 5rem */
}

p {
	font-size: clamp(1rem, 2vw + 0.5rem, 1.25rem);
	/* Siempre legible, escala suavemente */
}
```

**✅ Ventaja**: No necesitas media queries para responsive typography!

### 🔄 Comparación de Funciones

```css
/* SIN funciones modernas (antiguo) */
.antiguo {
	width: 600px;
	font-size: 16px;
}

@media (max-width: 768px) {
	.antiguo {
		width: 100%;
		font-size: 14px;
	}
}

/* CON funciones modernas (2025) */
.moderno {
	width: min(100%, 600px); /* Responsive automático */
	font-size: clamp(0.875rem, 2vw, 1rem); /* Escala suave sin breakpoints */
}
```

### ✅ Recomendación 2025

- **calc()**: Para cálculos precisos y mezclar unidades
- **min()/max()**: Para límites simples
- **clamp()**: Para tipografía fluida y spacing responsive (¡ÚSALO MUCHO!)

---

## 6️⃣ WIDTH y HEIGHT

### 📖 Teoría

`width` y `height` controlan las dimensiones de un elemento. Hay múltiples variantes para diferentes casos de uso.

### 🛠️ Propiedades Básicas

```css
.ejemplo-dimensiones {
	/* Dimensiones fijas */
	width: 300px;
	height: 200px;

	/* Dimensiones relativas */
	width: 50%;
	height: 100vh;

	/* Dimensiones con límites */
	min-width: 200px; /* Ancho mínimo */
	max-width: 800px; /* Ancho máximo */
	min-height: 300px; /* Alto mínimo */
	max-height: 600px; /* Alto máximo */
}
```

### 🚀 Método Moderno: Logical Properties (2025)

```css
/* En lugar de width/height, usa inline-size/block-size */

.moderno {
	/* Modo horizontal (idiomas como español/inglés) */
	inline-size: 300px; /* = width en modo horizontal */
	block-size: 200px; /* = height en modo horizontal */

	/* Modo vertical (idiomas como japonés) */
	/* inline-size sería la altura visual */
	/* block-size sería el ancho visual */
}

/* Ventaja: Funciona automáticamente con writing-mode */
```

### 🛠️ Casos de Uso Comunes

```css
/* Container responsive con límites */
.container {
	width: 100%;
	max-width: 1200px; /* Nunca más ancho que esto */
	margin-inline: auto; /* Centrar horizontalmente */
}

/* Card con proporción fija */
.card {
	width: 100%;
	max-width: 400px;
	min-height: 250px; /* Altura mínima garantizada */
}

/* Full viewport section */
.hero {
	width: 100vw;
	height: 100vh;
}

/* Imagen responsive */
.imagen-responsive {
	width: 100%;
	height: auto; /* Mantiene proporción */
}
```

### ✅ Recomendación 2025

- Usa `max-width` en lugar de `width` fijo para responsiveness
- `height: auto` para imágenes
- Considera `inline-size`/`block-size` para soporte multiidioma

---

## 7️⃣ OUTLINE vs BORDER

### 📖 Teoría

Aunque parecen similares, **outline** y **border** tienen diferencias importantes. Outline NO afecta el box model (no ocupa espacio), mientras que border sí.

### 💡 Concepto Clave

**Border**: Es parte de la caja, ocupa espacio, puede tener border-radius.
**Outline**: Dibujado FUERA de la caja, no ocupa espacio, útil para accesibilidad.

### 🛠️ Comparación Visual

```html
<!DOCTYPE html>
<html>
	<head>
		<style>
			.con-border {
				width: 200px;
				height: 100px;
				border: 5px solid #3498db;
				/* Ancho total = 210px (200 + 5 + 5) */
				/* Mueve otros elementos */
			}

			.con-outline {
				width: 200px;
				height: 100px;
				outline: 5px solid #e74c3c;
				/* Ancho total = 200px */
				/* NO mueve otros elementos */
			}

			/* Caso Real: Focus state accesible */
			.boton {
				padding: 1rem 2rem;
				border: 2px solid #3498db;
				background: white;
			}

			.boton:focus {
				outline: 3px solid #f39c12;
				outline-offset: 2px; /* Separa el outline del borde */
			}
		</style>
	</head>
	<body>
		<div class="con-border">Con Border (ocupa espacio)</div>
		<div class="con-outline">Con Outline (NO ocupa espacio)</div>
		<button class="boton">Presiona Tab para ver outline</button>
	</body>
</html>
```

### 🔄 Diferencias Clave

| Característica                | Border        | Outline                              |
| ----------------------------- | ------------- | ------------------------------------ |
| Ocupa espacio                 | ✅ Sí         | ❌ No                                |
| Parte del box model           | ✅ Sí         | ❌ No                                |
| `border-radius`               | ✅ Sí         | ❌ No (excepto navegadores modernos) |
| Estilos individuales por lado | ✅ Sí         | ❌ No                                |
| `outline-offset`              | ❌ No         | ✅ Sí                                |
| Uso principal                 | Diseño visual | Accesibilidad (focus)                |

### 🚀 Outline Moderno

```css
/* Propiedades de outline */
.ejemplo-outline {
	outline-width: 3px;
	outline-style: solid; /* solid, dashed, dotted, double */
	outline-color: #e74c3c;
	outline-offset: 5px; /* Espacio entre outline y elemento */

	/* Shorthand */
	outline: 3px solid #e74c3c;
}

/* IMPORTANTE: NO REMUEVAS EL OUTLINE DE FOCUS */
/* ❌ MAL */
*:focus {
	outline: none; /* Terrible para accesibilidad */
}

/* ✅ BIEN */
*:focus {
	outline: 2px solid #3498db;
	outline-offset: 2px;
}

/* ✅ MEJOR (2025) */
*:focus-visible {
	outline: 3px solid #3498db;
	outline-offset: 3px;
}
```

### ✅ Recomendación 2025

- **Border**: Para diseño visual y estructura
- **Outline**: Para estados de focus (accesibilidad)
- **NUNCA** remuevas outline sin reemplazarlo con un estilo de focus visible

---

## 8️⃣ BOX SHADOW

### 📖 Teoría

`box-shadow` crea sombras alrededor de elementos, añadiendo profundidad y jerarquía visual. Es esencial para diseños modernos tipo material design.

### 💡 Concepto Clave

Las sombras simulan luz y profundidad, haciendo que elementos parezcan "flotar" sobre la página. Una buena sombra es sutil pero efectiva.

### 🛠️ Sintaxis de box-shadow

```css
/* box-shadow: offset-x offset-y blur-radius spread-radius color inset; */

.ejemplo-shadow {
	/* Sombra simple */
	box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
	/*          ↑   ↑   ↑    ↑
     *          X   Y  Blur Spread Color
     */
}
```

### 🛠️ Ejemplos Prácticos

```css
/* Sombra suave (card elevation) */
.card-suave {
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

/* Sombra media (hover state) */
.card-media {
	box-shadow: 0 4px 16px rgba(0, 0, 0, 0.15);
}

/* Sombra profunda (modal) */
.card-profunda {
	box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
}

/* Sombra con spread */
.con-spread {
	box-shadow: 0 0 0 5px rgba(52, 152, 219, 0.3);
	/* Efecto de "glow" o borde suave */
}

/* Sombra interna */
.sombra-interna {
	box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.2);
	/* Efecto de "hundido" */
}
```

### 🚀 Múltiples Sombras (2025)

```css
/* Puedes aplicar MÚLTIPLES sombras separadas por comas */

.sombra-multiple {
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1), /* Sombra cercana */ 0 8px 16px rgba(0, 0, 0, 0.1); /* Sombra lejana */
	/* Crea efecto de profundidad realista */
}

/* Glow effect con múltiples capas */
.glow-effect {
	box-shadow: 0 0 5px rgba(52, 152, 219, 0.5), 0 0 10px rgba(52, 152, 219, 0.3), 0 0 20px rgba(52, 152, 219, 0.1);
}

/* Neumorphism (tendencia 2024-2025) */
.neumorphism {
	background: #e0e5ec;
	box-shadow: 9px 9px 16px rgba(163, 177, 198, 0.6), /* Sombra oscura */ -9px -9px 16px rgba(255, 255, 255, 0.5); /* Luz */
}
```

### 🎨 Shadows para Interacciones

```css
/* Transiciones suaves de sombra */
.card-interactiva {
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
	transition: box-shadow 0.3s ease;
}

.card-interactiva:hover {
	box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
	transform: translateY(-2px); /* Levita al hacer hover */
}

.card-interactiva:active {
	box-shadow: 0 1px 4px rgba(0, 0, 0, 0.15);
	transform: translateY(0); /* Presiona al hacer click */
}
```

### 🔄 Alternativas Modernas

```css
/* 2025: filter drop-shadow (sigue la forma, no la caja) */
.imagen-con-sombra {
	filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.2));
	/* Perfecto para imágenes PNG con transparencia */
}
```

### ✅ Recomendación 2025

- **Elevación baja**: `0 2px 8px rgba(0, 0, 0, 0.1)` - Cards normales
- **Elevación media**: `0 4px 16px rgba(0, 0, 0, 0.15)` - Hover states
- **Elevación alta**: `0 10px 40px rgba(0, 0, 0, 0.2)` - Modals, dropdowns
- Usa opacidad baja (0.1-0.3) para sombras sutiles
- Combina múltiples sombras para efectos realistas

---

## 9️⃣ TEMAS HTML: div y span

### 📖 Teoría

`<div>` y `<span>` son contenedores genéricos sin significado semántico. Úsalos cuando no exista un elemento semántico apropiado.

### 💡 Concepto Clave

**`<div>`**: Contenedor de **bloque** (block-level) - para secciones grandes.
**`<span>`**: Contenedor **inline** - para pequeñas porciones de texto.

### 🛠️ Ejemplos

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<style>
			/* div es block - ocupa todo el ancho */
			.seccion {
				background: #ecf0f1;
				padding: 20px;
				margin-bottom: 10px;
			}

			/* span es inline - solo ocupa su contenido */
			.destacado {
				color: #e74c3c;
				font-weight: bold;
			}
		</style>
	</head>
	<body>
		<!-- DIV: Para estructura y layout -->
		<div class="seccion">
			<h2>Título de Sección</h2>
			<p>Este es un párrafo con <span class="destacado">texto destacado</span> en el medio.</p>
		</div>

		<div class="seccion">
			<h2>Otra Sección</h2>
			<p>Más contenido aquí.</p>
		</div>
	</body>
</html>
```

### 🔄 Cuándo Usar

**Usa `<div>` cuando:**

- ✅ Necesitas un contenedor para layout (Grid, Flexbox)
- ✅ Agrupas elementos para aplicar estilos
- ✅ No existe un elemento semántico apropiado (`<section>`, `<article>`, etc.)

**Usa `<span>` cuando:**

- ✅ Necesitas estilizar parte de un texto
- ✅ Aplicas estilos inline a palabras específicas
- ✅ Envuelves contenido para JavaScript

**❌ No uses cuando:**

- Exista un elemento semántico mejor (`<header>`, `<nav>`, `<strong>`, `<em>`, etc.)

### ✅ Recomendación 2025

Prefiere elementos semánticos siempre que sea posible. Usa `<div>` y `<span>` solo como último recurso.

---

## 🔟 ATRIBUTOS DE DATOS (data-\*)

### 📖 Teoría

Los **data attributes** permiten almacenar información personalizada en elementos HTML que puede ser usada por CSS o JavaScript. Son atributos que comienzan con `data-`.

### 💡 Concepto Clave

Los data attributes son como "notas adhesivas" en tus elementos HTML: puedes poner cualquier información personalizada que necesites.

### 🛠️ Sintaxis Básica

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<style>
			/* Acceder a data attributes en CSS */
			[data-estado="activo"] {
				background-color: #2ecc71;
				color: white;
			}

			[data-estado="inactivo"] {
				background-color: #95a5a6;
				color: #ecf0f1;
			}

			[data-prioridad="alta"] {
				border-left: 5px solid #e74c3c;
			}

			[data-prioridad="baja"] {
				border-left: 5px solid #3498db;
			}
		</style>
	</head>
	<body>
		<!-- Data attributes personalizados -->
		<div class="tarea" data-estado="activo" data-prioridad="alta" data-id="123">Tarea importante activa</div>

		<div class="tarea" data-estado="inactivo" data-prioridad="baja" data-id="456">Tarea de baja prioridad</div>
	</body>
</html>
```

### 🚀 Casos de Uso Avanzados

```html
<!DOCTYPE html>
<html>
	<head>
		<style>
			/* Mostrar el valor del data attribute con ::before */
			.precio::before {
				content: "Precio: $";
			}

			.precio::after {
				content: attr(data-precio);
				font-weight: bold;
				color: #2ecc71;
			}

			/* Estilos condicionales con data attributes */
			.producto[data-stock="0"] {
				opacity: 0.5;
				pointer-events: none;
			}

			.producto[data-stock="0"]::after {
				content: "AGOTADO";
				position: absolute;
				top: 50%;
				left: 50%;
				transform: translate(-50%, -50%);
				background: #e74c3c;
				color: white;
				padding: 0.5rem 1rem;
				border-radius: 4px;
			}
		</style>
	</head>
	<body>
		<div class="precio" data-precio="199.99"></div>

		<div class="producto" data-stock="0" data-categoria="electronicos">Producto agotado</div>

		<div class="producto" data-stock="15" data-categoria="ropa">Producto disponible</div>
	</body>
</html>
```

### 🎨 Integración con JavaScript

```html
<!DOCTYPE html>
<html>
	<head>
		<style>
			.tab {
				padding: 1rem;
				cursor: pointer;
				background: #ecf0f1;
			}

			.tab[data-activo="true"] {
				background: #3498db;
				color: white;
			}

			.contenido {
				display: none;
				padding: 2rem;
			}

			.contenido[data-visible="true"] {
				display: block;
			}
		</style>
	</head>
	<body>
		<div class="tab" data-activo="true" data-tab-id="1">Tab 1</div>
		<div class="tab" data-activo="false" data-tab-id="2">Tab 2</div>

		<div class="contenido" data-visible="true" data-contenido-id="1">Contenido del Tab 1</div>

		<div class="contenido" data-visible="false" data-contenido-id="2">Contenido del Tab 2</div>

		<script>
			// JavaScript puede acceder y modificar data attributes
			const tabs = document.querySelectorAll(".tab");
			tabs.forEach((tab) => {
				tab.addEventListener("click", () => {
					const tabId = tab.dataset.tabId; // Acceso vía dataset
					console.log("Tab ID:", tabId);
				});
			});
		</script>
	</body>
</html>
```

### ✅ Recomendación 2025

- Usa `data-*` para información que CSS o JavaScript necesitarán
- Mantén nombres descriptivos: `data-user-id`, `data-loading-state`
- No uses para información sensible (es visible en HTML)
- Prefiere clases para estilos puros, data attributes para estado dinámico

---

## 📊 RESUMEN VISUAL DE LA SEMANA 2

### Box Model Completo

```
┌─────────────────────────────────┐
│         MARGIN (externo)         │
│  ┌───────────────────────────┐  │
│  │    BORDER (borde)         │  │
│  │  ┌─────────────────────┐  │  │
│  │  │  PADDING (interno)  │  │  │
│  │  │  ┌───────────────┐  │  │  │
│  │  │  │   CONTENT     │  │  │  │
│  │  │  │  (contenido)  │  │  │  │
│  │  │  └───────────────┘  │  │  │
│  │  └─────────────────────┘  │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘
```

### Unidades - Cuándo Usar

```
Font-sizes:   rem ✅
Padding:      rem ✅
Margin:       rem ✅
Width:        %, vw, rem ✅
Height:       vh, auto ✅
Borders:      px ✅
Shadows:      px ✅
Border-radius: rem, % ✅
```

### Checklist de Conceptos Dominados

- [ ] Entiendo las 4 capas del Box Model
- [ ] Uso `box-sizing: border-box` por defecto
- [ ] Conozco la diferencia entre unidades absolutas y relativas
- [ ] Puedo usar calc(), min(), max() y clamp()
- [ ] Entiendo cuándo usar rem vs em vs px
- [ ] Uso vw/vh para layouts responsive
- [ ] Sé la diferencia entre outline y border
- [ ] Aplico box-shadows para profundidad visual
- [ ] Uso div y span apropiadamente
- [ ] Implemento data attributes cuando es necesario

---

## 🎯 Próximos Pasos

Ahora que dominas el Box Model y las unidades CSS, estás listo para:

1. **Practicar**: Crea diferentes componentes jugando con spacing
2. **Experimentar**: Usa DevTools (F12) para visualizar el Box Model
3. **Proyecto**: Aplica estos conceptos en el Dashboard de Estadísticas

¡Recuerda que el Box Model es la BASE de todo CSS! Dominarlo es esencial para crear layouts profesionales.

---

**¡Excelente trabajo llegando hasta aquí! 🚀**

_Cuando estés listo, pregúntame sobre el proyecto Dashboard de Estadísticas de la Semana 2._
