# 📅 Semana 8: CSS Grid Master

**Fecha:** 17 Nov 2025 | **Estado:** ✅ En progreso

---

## 🎯 Objetivos de Aprendizaje

✅ Dominar CSS Grid completamente  
✅ Crear layouts complejos bidimensionales  
✅ Grid template areas  
✅ Responsive grid systems

---

## 📚 Teoría Completa de CSS Grid

### 🔹 ¿Qué es CSS Grid?

**CSS Grid** es un sistema de layout bidimensional que te permite controlar tanto filas como columnas simultáneamente. Es perfecto para:

- Layouts completos de páginas
- Dashboards complejos
- Diseños tipo revista/periódico
- Galerías adaptativas
- Cualquier diseño que requiera control preciso en 2D

**Diferencia clave con Flexbox:**

- **Flexbox**: Unidimensional (fila O columna)
- **Grid**: Bidimensional (filas Y columnas)

---

## 💡 Conceptos Fundamentales

### 1. Grid Container vs Grid Items

```css
.grid-container {
	display: grid; /* El contenedor se convierte en grid */
}

.grid-item {
	/* Los hijos directos son grid items */
}
```

### 2. Grid Lines (Líneas de la Cuadrícula)

Las líneas son los separadores entre tracks (columnas/filas):

```
Línea 1    Línea 2    Línea 3    Línea 4
    |          |          |          |
    | Columna 1| Columna 2| Columna 3|
    |          |          |          |
```

### 3. Grid Tracks (Columnas y Filas)

Son los espacios entre líneas:

- **Column Track**: Espacio vertical entre dos líneas verticales
- **Row Track**: Espacio horizontal entre dos líneas horizontales

### 4. Grid Cell (Celda)

La intersección de una fila y una columna.

### 5. Grid Area (Área)

Un espacio rectangular formado por una o más celdas.

---

## 🛠️ Propiedades del Grid Container

### 1. **display: grid**

```css
.container {
	display: grid; /* Grid de bloque */
	/* o */
	display: inline-grid; /* Grid inline */
}
```

### 2. **grid-template-columns / grid-template-rows**

Define el tamaño de columnas y filas:

```css
/* Valores fijos */
grid-template-columns: 200px 300px 200px;

/* Unidades fr (fracción del espacio disponible) */
grid-template-columns: 1fr 2fr 1fr; /* 2da columna es el doble */

/* Mezcla */
grid-template-columns: 200px 1fr 200px; /* Sidebar fijo, centro flexible */

/* repeat() */
grid-template-columns: repeat(3, 1fr); /* 3 columnas iguales */
grid-template-columns: repeat(4, 100px); /* 4 columnas de 100px */

/* minmax() */
grid-template-columns: repeat(3, minmax(200px, 1fr));
/* Mínimo 200px, máximo 1fr */

/* auto-fit y auto-fill */
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
/* Se adapta automáticamente */
```

**Ejemplo completo:**

```css
.gallery {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
	grid-template-rows: repeat(3, 200px);
	gap: 20px;
}
```

### 3. **grid-template-areas**

Define el layout con nombres visuales:

```css
.page-layout {
	display: grid;
	grid-template-areas:
		"header header header"
		"sidebar main aside"
		"footer footer footer";

	grid-template-columns: 200px 1fr 200px;
	grid-template-rows: auto 1fr auto;
	gap: 10px;
}

.header {
	grid-area: header;
}
.sidebar {
	grid-area: sidebar;
}
.main {
	grid-area: main;
}
.aside {
	grid-area: aside;
}
.footer {
	grid-area: footer;
}
```

**Ventajas:**

- Visual e intuitivo
- Fácil reorganización responsive
- Código más legible

**Ejemplo responsive:**

```css
@media (max-width: 768px) {
	.page-layout {
		grid-template-areas:
			"header"
			"main"
			"sidebar"
			"aside"
			"footer";

		grid-template-columns: 1fr;
	}
}
```

### 4. **gap (anteriormente grid-gap)**

Espacio entre celdas:

```css
/* Ambos (filas y columnas) */
gap: 20px;

/* Separado */
row-gap: 20px;
column-gap: 30px;

/* Shorthand */
gap: 20px 30px; /* filas columnas */
```

### 5. **Alineación en Grid Container**

```css
.container {
	/* Alineación de items dentro de sus celdas */
	justify-items: start | end | center | stretch; /* Horizontal */
	align-items: start | end | center | stretch; /* Vertical */

	/* Alineación del grid completo dentro del contenedor */
	justify-content: start | end | center | stretch | space-between | space-around | space-evenly;
	align-content: start | end | center | stretch | space-between | space-around | space-evenly;

	/* Shorthand */
	place-items: center; /* align-items + justify-items */
	place-content: center; /* align-content + justify-content */
}
```

### 6. **grid-auto-flow**

Controla cómo se colocan los items automáticamente:

```css
grid-auto-flow: row; /* Por defecto, llena filas */
grid-auto-flow: column; /* Llena columnas */
grid-auto-flow: dense; /* Intenta llenar huecos */
```

### 7. **grid-auto-columns / grid-auto-rows**

Tamaño de tracks implícitos (creados automáticamente):

```css
grid-auto-rows: 100px; /* Filas implícitas de 100px */
grid-auto-rows: minmax(100px, auto); /* Mínimo 100px, se expanden */
grid-auto-columns: 200px; /* Columnas implícitas de 200px */
```

---

## 🎯 Propiedades de Grid Items

### 1. **grid-column / grid-row**

Posiciona items por líneas:

```css
.item {
	/* Por líneas */
	grid-column-start: 1;
	grid-column-end: 3;
	grid-row-start: 1;
	grid-row-end: 2;

	/* Shorthand */
	grid-column: 1 / 3; /* start / end */
	grid-row: 1 / 2;

	/* Con span (ocupa X tracks) */
	grid-column: 1 / span 2; /* Desde 1, ocupa 2 columnas */
	grid-row: 1 / span 3; /* Desde 1, ocupa 3 filas */

	/* Span sin inicio (automático) */
	grid-column: span 2; /* Ocupa 2 columnas desde donde esté */
}
```

**Ejemplo:**

```css
.featured-article {
	grid-column: 1 / 4; /* Ocupa columnas 1, 2, 3 */
	grid-row: 1 / 3; /* Ocupa filas 1, 2 */
}
```

### 2. **grid-area**

Dos usos:

**A) Asignar a un área nombrada:**

```css
.header {
	grid-area: header; /* Nombre del template-areas */
}
```

**B) Shorthand de posicionamiento:**

```css
.item {
	grid-area: 1 / 2 / 3 / 4;
	/* row-start / col-start / row-end / col-end */
}
```

### 3. **Alineación Individual**

```css
.item {
	justify-self: start | end | center | stretch; /* Horizontal */
	align-self: start | end | center | stretch; /* Vertical */
	place-self: center; /* Shorthand */
}
```

---

## 🚀 Funciones Avanzadas de Grid

### 1. **repeat()**

Repite un patrón de tracks:

```css
/* Básico */
grid-template-columns: repeat(3, 100px);
/* = 100px 100px 100px */

/* Con patrones */
grid-template-columns: repeat(3, 100px 200px);
/* = 100px 200px 100px 200px 100px 200px */

/* Con fr */
grid-template-columns: repeat(4, 1fr);
/* 4 columnas iguales */

/* Auto-repeat */
grid-template-columns: repeat(auto-fit, 200px);
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
```

### 2. **minmax()**

Define un rango de tamaño:

```css
/* Mínimo 200px, máximo 1fr */
grid-template-columns: repeat(3, minmax(200px, 1fr));

/* Mínimo contenido, máximo 500px */
grid-template-rows: minmax(min-content, 500px);

/* Mínimo 100px, máximo automático (contenido) */
grid-auto-rows: minmax(100px, auto);
```

**Valores especiales:**

- `min-content`: Tamaño mínimo del contenido
- `max-content`: Tamaño máximo del contenido
- `auto`: Se ajusta según el contenido

### 3. **auto-fit vs auto-fill**

**auto-fit**: Colapsa tracks vacías, expande items:

```css
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
```

**auto-fill**: Mantiene tracks vacías:

```css
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
```

**Cuándo usar:**

- ✅ **auto-fit**: Galerías, cards que deben expandirse
- ✅ **auto-fill**: Cuando quieres mantener columnas consistentes

### 4. **fr (fracción)**

Unidad flexible que representa una fracción del espacio disponible:

```css
/* 3 columnas iguales */
grid-template-columns: 1fr 1fr 1fr;

/* Ratio 2:1 */
grid-template-columns: 2fr 1fr;

/* Sidebar fijo, contenido flexible */
grid-template-columns: 250px 1fr;

/* 3 columnas: fija + flexible + flexible */
grid-template-columns: 200px 1fr 2fr;
```

**Importante:** `fr` se calcula DESPUÉS de elementos fijos:

```css
grid-template-columns: 200px 1fr 2fr;
/* 200px fijos, el resto se divide en 3 partes (1fr + 2fr) */
```

---

## 🆕 Subgrid (2025)

Permite que un grid item herede las tracks del grid padre:

```css
.parent-grid {
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	gap: 20px;
}

.nested-item {
	display: grid;
	grid-column: 1 / 4;

	/* 🆕 Usa las columnas del padre */
	grid-template-columns: subgrid;

	/* Puede tener su propio gap */
	gap: 10px;
}
```

**Ventajas:**

- Alineación perfecta con el grid padre
- Evita problemas de desalineación
- Código más limpio

**Compatibilidad 2025:** ✅ Chrome, Firefox, Safari (excelente)

---

## 📱 Grid Responsive - Mejores Prácticas

### Método 1: Media Queries

```css
.grid {
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	gap: 20px;
}

@media (max-width: 1024px) {
	.grid {
		grid-template-columns: repeat(2, 1fr);
	}
}

@media (max-width: 768px) {
	.grid {
		grid-template-columns: 1fr;
	}
}
```

### Método 2: auto-fit (Sin media queries)

```css
.grid {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
	gap: 20px;
}
/* Se adapta automáticamente al ancho disponible */
```

### Método 3: Grid Template Areas Responsive

```css
.layout {
	display: grid;
	grid-template-areas:
		"header header"
		"sidebar main"
		"footer footer";
	grid-template-columns: 250px 1fr;
}

@media (max-width: 768px) {
	.layout {
		grid-template-areas:
			"header"
			"main"
			"sidebar"
			"footer";
		grid-template-columns: 1fr;
	}
}
```

---

## 🔥 Patrones Comunes de Grid

### 1. **Holy Grail Layout**

```css
.holy-grail {
	display: grid;
	grid-template-areas:
		"header header header"
		"nav main aside"
		"footer footer footer";

	grid-template-columns: 200px 1fr 200px;
	grid-template-rows: auto 1fr auto;
	min-height: 100vh;
}
```

### 2. **Dashboard Layout**

```css
.dashboard {
	display: grid;
	grid-template-columns: 250px repeat(3, 1fr);
	grid-template-rows: 80px repeat(3, minmax(200px, auto));
	gap: 20px;
}

.sidebar {
	grid-column: 1;
	grid-row: 1 / -1;
}
.header {
	grid-column: 2 / -1;
	grid-row: 1;
}
.main-chart {
	grid-column: 2 / 4;
	grid-row: 2 / 4;
}
```

### 3. **Masonry-style Grid (Pinterest)**

```css
.masonry {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
	grid-auto-rows: 10px; /* Pequeñas unidades */
	gap: 10px;
}

.masonry-item {
	grid-row-end: span 20; /* Ajustar según altura */
}
```

### 4. **Galería Responsive**

```css
.gallery {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
	gap: 15px;
}

.gallery-item:nth-child(3n) {
	grid-column: span 2; /* Cada 3er item es más ancho */
}
```

---

## 🎯 Grid vs Flexbox - Cuándo Usar Cada Uno

### Usa **Grid** cuando:

✅ Necesitas control en 2 dimensiones (filas Y columnas)  
✅ Layout completo de página  
✅ Elementos deben alinearse en ambas direcciones  
✅ Necesitas posicionamiento preciso  
✅ Diseños tipo dashboard o revista

### Usa **Flexbox** cuando:

✅ Layout en 1 dimensión (fila O columna)  
✅ Componentes pequeños (navbar, cards, buttons)  
✅ Necesitas que items se ajusten dinámicamente  
✅ Orden visual diferente al HTML  
✅ Alineación simple de contenido

### Combínalos:

```css
.page {
	display: grid; /* Layout general */
	grid-template-columns: 250px 1fr;
}

.navbar {
	display: flex; /* Navbar con flexbox */
	justify-content: space-between;
}

.card {
	display: grid; /* Card con grid */
	grid-template-rows: auto 1fr auto;
}
```

---

## 💻 Ejemplos Prácticos Completos

### Ejemplo 1: Card Grid Gallery

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<style>
			.gallery {
				display: grid;
				grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
				gap: 20px;
				padding: 20px;
			}

			.card {
				background: white;
				border-radius: 12px;
				overflow: hidden;
				box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);

				display: grid;
				grid-template-rows: 200px auto 1fr auto;
			}

			.card img {
				width: 100%;
				height: 100%;
				object-fit: cover;
			}
			.card-content {
				padding: 1rem;
			}
			.card-footer {
				padding: 1rem;
				border-top: 1px solid #eee;
			}
		</style>
	</head>
	<body>
		<div class="gallery">
			<div class="card">
				<img src="..." alt="" />
				<h3 class="card-content">Título</h3>
				<p class="card-content">Descripción</p>
				<div class="card-footer">Footer</div>
			</div>
			<!-- Más cards -->
		</div>
	</body>
</html>
```

### Ejemplo 2: Responsive Dashboard

```css
.dashboard {
	display: grid;
	grid-template-areas:
		"sidebar header header"
		"sidebar stats stats"
		"sidebar main aside"
		"sidebar footer footer";

	grid-template-columns: 250px 1fr 300px;
	grid-template-rows: 80px 150px 1fr 80px;
	gap: 20px;
	min-height: 100vh;
}

@media (max-width: 1024px) {
	.dashboard {
		grid-template-areas:
			"header"
			"stats"
			"main"
			"aside"
			"sidebar"
			"footer";

		grid-template-columns: 1fr;
		grid-template-rows: auto;
	}
}
```

---

## 🔍 Debugging Grid

### DevTools

**Chrome/Edge/Firefox:**

1. Inspecciona el elemento grid
2. Activa la badge "grid" en el inspector
3. Verás las líneas de grid superpuestas

**Herramientas útiles:**

- Ver números de línea
- Ver nombres de áreas
- Ver gap visualizado
- Highlight de tracks

### CSS para Debugging

```css
.grid-container {
	background: lightblue; /* Ver el contenedor */
}

.grid-item {
	border: 2px solid red; /* Ver los items */
	background: rgba(255, 255, 255, 0.8);
}
```

---

## ✅ Checklist de Dominio de Grid

### Nivel Básico

- [ ] Crear un grid simple con columnas y filas
- [ ] Usar gap para espaciado
- [ ] Posicionar items con grid-column/grid-row
- [ ] Usar repeat() y fr

### Nivel Intermedio

- [ ] Implementar grid-template-areas
- [ ] Usar minmax() para tracks flexibles
- [ ] Hacer spanning de múltiples celdas
- [ ] Grid responsive con media queries

### Nivel Avanzado

- [ ] Usar auto-fit/auto-fill para grids adaptativos
- [ ] Combinar Grid + Flexbox eficientemente
- [ ] Implementar layouts complejos (dashboard, magazine)
- [ ] Usar subgrid (2025)
- [ ] Optimizar performance

---

## 🚀 Mejores Prácticas 2025

### 1. **Usa gap en lugar de margins**

❌ Evita:

```css
.grid-item {
	margin: 10px;
}
```

✅ Mejor:

```css
.grid-container {
	gap: 20px;
}
```

### 2. **Prioriza auto-fit para responsive**

```css
grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
/* Menos media queries, más mantenible */
```

### 3. **Usa fr para flexibilidad**

❌ Evita porcentajes:

```css
grid-template-columns: 33.33% 33.33% 33.33%;
```

✅ Mejor:

```css
grid-template-columns: repeat(3, 1fr);
```

### 4. **Nombra áreas para claridad**

```css
grid-template-areas:
	"header header"
	"sidebar main"
	"footer footer";
/* Más legible que números de línea */
```

### 5. **Mobile-first responsive**

```css
/* Mobile por defecto */
.grid {
	grid-template-columns: 1fr;
}

/* Desktop con media query */
@media (min-width: 768px) {
	.grid {
		grid-template-columns: repeat(3, 1fr);
	}
}
```

---

## 🎓 Recursos Adicionales

- [MDN CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
- [CSS Tricks Complete Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Grid by Example](https://gridbyexample.com/)
- [Can I Use - Grid](https://caniuse.com/css-grid)
- [Grid Garden (Game)](https://cssgridgarden.com/)

---

## 📝 Resumen Rápido

**Grid es:**

- Sistema de layout bidimensional (filas + columnas)
- Ideal para layouts completos de página
- Poderoso para diseños complejos

**Propiedades clave del container:**

```css
display: grid;
grid-template-columns: repeat(3, 1fr);
grid-template-rows: repeat(2, 200px);
gap: 20px;
```

**Propiedades clave de items:**

```css
grid-column: 1 / 3;
grid-row: 1 / 2;
```

**Funciones esenciales:**

- `repeat()`: Repetir tracks
- `minmax()`: Rango de tamaño
- `fr`: Unidad flexible
- `auto-fit`/`auto-fill`: Responsive automático

---

✨ **¡Domina Grid y podrás crear cualquier layout profesional imaginable!**
