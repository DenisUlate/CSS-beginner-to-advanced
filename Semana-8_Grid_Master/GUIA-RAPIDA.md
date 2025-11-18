# 🚀 CSS Grid - Guía Rápida de Referencia

## Activar Grid

```css
.container {
	display: grid;
}
```

---

## 📐 Definir Columnas y Filas

```css
/* Valores fijos */
grid-template-columns: 200px 300px 200px;
grid-template-rows: 100px 200px;

/* Unidad fr (flexible) */
grid-template-columns: 1fr 2fr 1fr;

/* repeat() */
grid-template-columns: repeat(3, 1fr);

/* minmax() */
grid-template-columns: repeat(3, minmax(200px, 1fr));

/* auto-fit (responsive automático) */
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

/* auto-fill */
grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));

/* Mix */
grid-template-columns: 250px repeat(3, 1fr) 250px;
```

---

## 🎨 Grid Template Areas

```css
.container {
	display: grid;
	grid-template-areas:
		"header header header"
		"sidebar main aside"
		"footer footer footer";

	grid-template-columns: 250px 1fr 250px;
	grid-template-rows: auto 1fr auto;
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

---

## 📏 Gap (Espaciado)

```css
/* Ambos */
gap: 20px;

/* Separado */
row-gap: 20px;
column-gap: 30px;

/* Shorthand */
gap: 20px 30px; /* row column */
```

---

## 📍 Posicionar Items

```css
/* Por líneas */
grid-column: 1 / 3; /* start / end */
grid-row: 1 / 2;

/* Con span (ocupar X tracks) */
grid-column: 1 / span 2; /* Desde 1, ocupa 2 */
grid-row: span 3; /* Ocupa 3 filas */

/* Shorthand completo */
grid-area: 1 / 2 / 3 / 4;
/* row-start / col-start / row-end / col-end */
```

---

## 🎯 Alineación en Container

```css
/* Items dentro de sus celdas */
justify-items: start | end | center | stretch; /* ↔ horizontal */
align-items: start | end | center | stretch; /* ↕ vertical */

/* Grid completo dentro del contenedor */
justify-content: start | end | center | stretch | space-between | space-around | space-evenly;
align-content: start | end | center | stretch | space-between | space-around | space-evenly;

/* Shorthand */
place-items: center; /* align-items + justify-items */
place-content: center; /* align-content + justify-content */
```

---

## 🎯 Alineación de Items Individuales

```css
.item {
	justify-self: start | end | center | stretch; /* ↔ */
	align-self: start | end | center | stretch; /* ↕ */
	place-self: center; /* Shorthand */
}
```

---

## 🔄 Grid Auto Flow

```css
grid-auto-flow: row; /* Por defecto, llena filas */
grid-auto-flow: column; /* Llena columnas */
grid-auto-flow: dense; /* Intenta llenar huecos */
```

---

## ⚙️ Grid Auto Rows/Columns

```css
/* Tamaño de tracks implícitos (auto-creados) */
grid-auto-rows: 100px;
grid-auto-rows: minmax(100px, auto);
grid-auto-columns: 200px;
```

---

## 🆕 Subgrid (2025)

```css
.parent {
	display: grid;
	grid-template-columns: repeat(4, 1fr);
}

.child {
	display: grid;
	grid-column: 1 / 4;
	grid-template-columns: subgrid; /* Hereda del padre */
}
```

---

## 📱 Patrones Responsive

### Auto-fit (sin media queries)

```css
.gallery {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
	gap: 20px;
}
```

### Con Media Queries

```css
.grid {
	grid-template-columns: repeat(4, 1fr);
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

### Grid Template Areas Responsive

```css
.layout {
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

## 💡 Ejemplos Rápidos

### Grid Básico 3x3

```css
.grid {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-template-rows: repeat(3, 150px);
	gap: 20px;
}
```

### Featured Item (2 columnas x 2 filas)

```css
.featured {
	grid-column: span 2;
	grid-row: span 2;
}
```

### Sidebar + Main

```css
.container {
	display: grid;
	grid-template-columns: 250px 1fr;
	gap: 20px;
}
```

### Galería Auto-Responsive

```css
.gallery {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
	gap: 20px;
}
```

### Centrar un Item

```css
.container {
	display: grid;
	place-items: center;
	min-height: 100vh;
}
```

### Holy Grail Layout

```css
.page {
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

---

## 🔍 Valores Especiales

```css
/* Tamaños */
auto              /* Basado en contenido */
min-content       /* Tamaño mínimo del contenido */
max-content       /* Tamaño máximo del contenido */
fit-content(200px)/* Entre min y max, límite 200px */

/* Unidades */
fr                /* Fracción del espacio disponible */
%                 /* Porcentaje del contenedor */
px, em, rem       /* Valores fijos */
vw, vh            /* Viewport width/height */

/* Funciones */
repeat()          /* Repetir patrón */
minmax()          /* Rango min-max */
min()             /* Valor mínimo */
max()             /* Valor máximo */
clamp()           /* Valor entre min y max */
```

---

## 🎨 Debugging

### Chrome/Firefox DevTools

1. Inspecciona el elemento grid
2. Activa el badge "grid"
3. Verás las líneas superpuestas
4. Puedes ver números de línea
5. Ver nombres de áreas

### CSS Visual

```css
.grid-container {
	background: lightblue;
}

.grid-item {
	border: 2px solid red;
	background: rgba(255, 255, 255, 0.8);
}
```

---

## ⚡ Mejores Prácticas 2025

### ✅ Hacer

```css
/* Usa fr en lugar de porcentajes */
grid-template-columns: repeat(3, 1fr);

/* Usa gap en lugar de margins */
gap: 20px;

/* Usa auto-fit para responsive */
grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));

/* Usa template areas para layouts complejos */
grid-template-areas: "header header" "sidebar main";

/* Mobile-first */
.grid {
	grid-template-columns: 1fr;
}
@media (min-width: 768px) {
	.grid {
		grid-template-columns: repeat(3, 1fr);
	}
}
```

### ❌ Evitar

```css
/* Porcentajes cuando fr es mejor */
grid-template-columns: 33.33% 33.33% 33.33%;

/* Margins en items (usa gap) */
.grid-item {
	margin: 10px;
}

/* Demasiados media queries (usa auto-fit) */

/* !important innecesario */

/* Valores mágicos sin comentar */
grid-column: 2 / 7; /* ¿Por qué 7? */
```

---

## 📊 Comparación Grid vs Flexbox

| Característica | Grid                  | Flexbox             |
| -------------- | --------------------- | ------------------- |
| Dimensiones    | 2D (filas + columnas) | 1D (fila O columna) |
| Uso ideal      | Layouts de página     | Componentes         |
| Control        | Preciso               | Flexible            |
| Alineación     | Ambas direcciones     | Una dirección       |
| Orden visual   | Fácil cambiar         | Fácil cambiar       |
| Responsive     | auto-fit/auto-fill    | flex-wrap           |

**Recomendación:** Usa Grid para layout general y Flexbox para componentes internos.

---

## 🎯 Trucos Rápidos

### Centrar Perfectamente

```css
display: grid;
place-items: center;
```

### Ocupar Todo el Viewport

```css
display: grid;
grid-template-rows: auto 1fr auto;
min-height: 100vh;
```

### Grid de Cards Uniformes

```css
display: grid;
grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
grid-auto-rows: 1fr;
```

### Mantener Aspect Ratio

```css
.item {
	aspect-ratio: 16 / 9;
}
```

### Grid Asimétrico

```css
grid-template-columns: 2fr 1fr;
/* Primera columna es el doble */
```

---

## 🔗 Recursos Útiles

- [MDN CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
- [CSS Tricks Complete Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Grid by Example](https://gridbyexample.com/)
- [Grid Garden Game](https://cssgridgarden.com/)
- [Can I Use Grid](https://caniuse.com/css-grid)

---

## 📋 Checklist de Implementación

Antes de publicar tu grid, verifica:

- [ ] Funciona en Chrome, Firefox, Safari, Edge
- [ ] Responsive en mobile, tablet, desktop
- [ ] Gap consistente (no margins en items)
- [ ] Sin scroll horizontal no deseado
- [ ] Items no se superponen sin intención
- [ ] Template areas bien nombradas
- [ ] Código comentado
- [ ] DevTools grid overlay muestra estructura correcta
- [ ] Accesibilidad: orden lógico en HTML
- [ ] Performance: evitar grids anidados innecesarios

---

**💾 Guarda esta guía como referencia rápida - ¡La necesitarás!**
