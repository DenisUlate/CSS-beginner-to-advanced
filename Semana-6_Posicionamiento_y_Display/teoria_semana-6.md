# 📅 SEMANA 6: Posicionamiento & Display

Fecha: **21 Oct 2025** | Estado: ✅ Completado

---

## 🎯 Objetivos de Aprendizaje

- ✅ Dominar todas las propiedades de posicionamiento
- ✅ Entender el flujo del documento
- ✅ Trabajar con z-index y stacking context
- ✅ Controlar display modes

---

## 📚 Temas Cubiertos

### CSS

- ✅ `display`: block, inline, inline-block, none
- ✅ `visibility: hidden` vs `display: none`
- ✅ `position`: static, relative, absolute, fixed, sticky
- ✅ `top, right, bottom, left`
- ✅ `z-index` y stacking context
- ✅ Floating elements (legacy)
- ✅ Multi-column layout
- ✅ `overflow`: visible, hidden, scroll, auto

### HTML

- ✅ Estructura para layouts complejos

---

## 📖 1. Display Modes

### ¿Qué es `display`?

Define el tipo de caja de renderizado que usa un elemento y cómo interactúa con otros elementos.

### Valores Principales

#### `block`

```css
div,
p,
h1 {
	display: block;
	/* Ocupa todo el ancho disponible */
	/* Se apilan verticalmente */
	/* Acepta width, height, margin, padding */
}
```

#### `inline`

```css
span,
a,
strong {
	display: inline;
	/* Solo ocupa el ancho de su contenido */
	/* Se coloca en línea con otros elementos */
	/* NO acepta width/height */
	/* margin/padding solo horizontal */
}
```

#### `inline-block`

```css
.button {
	display: inline-block;
	/* Híbrido: se coloca en línea PERO acepta width/height */
	width: 150px;
	height: 40px;
	/* ✅ MEJOR OPCIÓN para botones */
}
```

#### `none`

```css
.hidden {
	display: none;
	/* Elemento completamente removido del flujo */
	/* NO ocupa espacio */
}
```

### 🆚 `visibility: hidden` vs `display: none`

```css
/* Ocultar pero mantener el espacio */
.invisible {
	visibility: hidden;
	/* Oculto pero SIGUE ocupando espacio */
}

/* Remover completamente */
.removed {
	display: none;
	/* Oculto y NO ocupa espacio */
}

/* ✅ MODERNO 2025: Ocultar accesiblemente */
.visually-hidden {
	position: absolute;
	width: 1px;
	height: 1px;
	overflow: hidden;
	clip: rect(0, 0, 0, 0);
	/* Oculto visualmente pero accesible para screen readers */
}
```

---

## 📖 2. Position Properties

### ¿Qué es `position`?

Controla el método de posicionamiento de un elemento en el documento.

### Valores de Position

#### `static` (Default)

```css
.element {
	position: static;
	/* Comportamiento normal del flujo del documento */
	/* top, right, bottom, left NO tienen efecto */
}
```

#### `relative`

```css
.relative-box {
	position: relative;
	top: 20px; /* Se mueve desde su posición ORIGINAL */
	left: 30px;
	/* El espacio original SIGUE reservado */
	/* Crea contexto de posicionamiento para hijos absolute */
}
```

#### `absolute`

```css
.absolute-box {
	position: absolute;
	top: 0;
	right: 0;
	/* Se posiciona relativo al ancestro positioned más cercano */
	/* Es REMOVIDO del flujo normal */
	/* Útil para: badges, tooltips, overlays */
}
```

#### `fixed`

```css
.fixed-header {
	position: fixed;
	top: 0;
	left: 0;
	right: 0;
	/* Se posiciona relativo al VIEWPORT */
	/* Permanece fijo al hacer scroll */
	/* Útil para: headers, modals, FABs */
}
```

#### `sticky` (✅ MODERNO 2025)

```css
.sticky-nav {
	position: sticky;
	top: 0;
	/* Híbrido entre relative y fixed */
	/* Actúa como relative hasta cierto scroll */
	/* Luego se "pega" como fixed */
	/* ✅ MEJOR para headers en muchos casos */
}
```

---

## 📖 3. Z-Index y Stacking Context

### ¿Qué es `z-index`?

Controla el orden de apilamiento de elementos posicionados (no funciona con `position: static`).

### Stacking Context

Un grupo de elementos que se apilan juntos. Se crea con:

- `position: relative/absolute/fixed/sticky` + `z-index`
- `opacity` menor a 1
- `transform`, `filter`, `backdrop-filter`
- `isolation: isolate` (moderno 2025)

### ✅ Mejores Prácticas 2025

```css
/* ❌ EVITAR: Z-index arbitrarios */
.header {
	z-index: 999999;
}
.modal {
	z-index: 99999999;
}

/* ✅ USAR: Sistema escalado con CSS Variables */
:root {
	--z-dropdown: 1000;
	--z-sticky: 1020;
	--z-fixed: 1030;
	--z-modal-backdrop: 1040;
	--z-modal: 1050;
	--z-notification: 1060;
	--z-tooltip: 1070;
}

.header {
	z-index: var(--z-sticky);
}
.modal {
	z-index: var(--z-modal);
}

/* ✅ MODERNO 2025: Crear contexto sin position */
.component {
	isolation: isolate;
}
```

---

## 📖 4. Overflow

### ¿Qué es `overflow`?

Controla qué sucede cuando el contenido es más grande que su contenedor.

### Valores

```css
/* VISIBLE: Default, el contenido se desborda */
overflow: visible;

/* HIDDEN: Oculta el contenido que se desborda */
overflow: hidden;

/* SCROLL: Siempre muestra scrollbars */
overflow: scroll;

/* AUTO: Scrollbar solo si es necesario (✅ RECOMENDADO) */
overflow: auto;

/* Control por eje */
overflow-x: auto;
overflow-y: hidden;
```

### Text Overflow

```css
.truncated {
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
}
```

---

## 📖 5. Floating Elements (Legacy)

### ⚠️ En 2025: EVITAR para layouts

```css
/* ✅ USO VÁLIDO: Texto rodeando imagen */
.article-image {
	float: left;
	margin-right: 1rem;
}

/* ❌ NO USAR: Layouts con float (usar Grid/Flexbox) */
.column {
	float: left;
}
```

---

## 📖 6. Multi-Column Layout

### Para artículos estilo periódico

```css
.article {
	columns: 3;
	column-gap: 2rem;
	column-rule: 1px solid #e2e8f0;
}

.article h2 {
	break-inside: avoid; /* Evita romper elementos */
}
```

---

## 💼 Proyecto de la Semana

**Header Sticky con Modal Profesional**

Ver archivos:

- `index.html` - Estructura HTML completa
- `style.css` - Estilos con técnicas modernas 2025

### Características Implementadas:

✅ Header sticky con navegación  
✅ Modal centrado con overlay  
✅ Z-index management (sistema escalado)  
✅ Animaciones suaves de apertura/cierre  
✅ Close button funcional  
✅ Responsive design  
✅ Accesibilidad (focus trap, ESC key)

---

## 🎯 Conceptos Clave Aprendidos

1. **Display modes** controlan el comportamiento de la caja
2. **Position** controla cómo se coloca en el documento
3. **Z-index** solo funciona con elementos posicionados
4. **Stacking context** puede "atrapar" z-index de hijos
5. **Sticky** es mejor que fixed en muchos casos (2025)
6. **Overflow** controla el desbordamiento de contenido
7. **Floats** son legacy (usar Grid/Flexbox para layouts)

---

## 📚 Recursos Adicionales

- [MDN: CSS Positioning](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
- [MDN: Stacking Context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)
- [CSS Tricks: All About Floats](https://css-tricks.com/all-about-floats/)
- [Can I Use: Position Sticky](https://caniuse.com/css-sticky)

---

**Siguiente Semana:** Semana 7 - Transitions, Transforms & Animations 🎬
