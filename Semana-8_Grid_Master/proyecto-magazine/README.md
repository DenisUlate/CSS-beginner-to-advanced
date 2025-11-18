# 📰 Proyecto: TechNews Magazine Layout

## 🎯 Objetivo del Proyecto

Crear un layout complejo tipo revista/periódico usando **CSS Grid**, demostrando el dominio de layouts bidimensionales, posicionamiento de elementos en múltiples celdas, y diseño responsive.

---

## ✅ Requisitos Cumplidos

### 1. **Layout complejo con Grid** ✓

- Grid de 6 columnas con `grid-template-columns: repeat(6, 1fr)`
- Filas dinámicas con `grid-auto-rows: minmax(200px, auto)`
- Gap de 20px entre elementos

### 2. **Grid Template Areas nombradas** ✓

- Aunque el proyecto usa `grid-column` y `grid-row` para mayor control, incluye ejemplo de grid template areas en el footer
- Ver ejemplo completo en la teoría

### 3. **Elementos spanning múltiples tracks** ✓

- **Featured article**: Ocupa 4 columnas x 2 filas
- **Secondary article**: Ocupa 2 columnas x 2 filas
- **Horizontal article**: Ocupa 4 columnas x 1 fila
- **Wide article**: Ocupa 4 columnas x 1 fila
- **Sidebar ad**: Ocupa 2 columnas x 3 filas

### 4. **Uso de minmax() y fr** ✓

```css
grid-auto-rows: minmax(200px, auto);
grid-template-columns: repeat(6, 1fr);
```

### 5. **Auto-fit para responsividad** ✓

- Footer usa: `grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))`
- Incluye ejemplo bonus en CSS

---

## 📂 Estructura del Proyecto

```
proyecto-magazine/
├── index.html          # Estructura HTML del magazine
└── style.css           # Estilos CSS Grid completos
```

---

## 🎨 Características del Layout

### Grid Principal (Desktop)

```
┌─────────────────────────┬─────────┐
│                         │         │
│   Featured Article      │Secondary│
│   (4 cols x 2 rows)     │(2x2)    │
│                         │         │
├─────────────────────────┼─────────┤
│   Horizontal Article    │         │
│   (4 cols x 1 row)      │ Sidebar │
├───┬───┬───┬───┬─────────┤   Ad    │
│ 1 │ 2 │ 3 │ 4 │ Wide    │ (2x3)   │
├───┴───┴───┴───┤ Article │         │
│               │ (4x1)   │         │
└───────────────┴─────────┴─────────┘
```

### Grid Responsive

- **Tablet (1024px)**: 4 columnas
- **Mobile (768px)**: 1 columna (stack vertical)

---

## 🔑 Conceptos CSS Grid Aplicados

### 1. **Posicionamiento Explícito**

```css
.article.featured {
	grid-column: 1 / 5; /* Desde línea 1 hasta línea 5 */
	grid-row: 1 / 3; /* Desde línea 1 hasta línea 3 */
}
```

### 2. **Unidades Flexibles (fr)**

```css
grid-template-columns: repeat(6, 1fr); /* 6 columnas iguales */
```

### 3. **minmax() para Filas Adaptativas**

```css
grid-auto-rows: minmax(200px, auto);
/* Mínimo 200px, se expande según contenido */
```

### 4. **Gap para Espaciado**

```css
gap: 20px; /* Espacio uniforme entre celdas */
```

### 5. **Auto-fit Responsive**

```css
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
/* Se adapta automáticamente al espacio disponible */
```

### 6. **Grid Interno en Items**

```css
.article {
	display: grid;
	grid-template-rows: auto 1fr;
	/* Imagen arriba, contenido abajo */
}
```

---

## 🚀 Cómo Usar el Proyecto

### 1. **Abrir en Navegador**

```bash
# Abre index.html en tu navegador favorito
# O usa Live Server en VS Code
```

### 2. **Experimentar con el Layout**

#### Cambiar número de columnas:

```css
.magazine-grid {
	grid-template-columns: repeat(4, 1fr); /* Cambia 6 por 4 */
}
```

#### Cambiar posición de artículos:

```css
.article.featured {
	grid-column: 1 / 3; /* Más pequeño */
	grid-row: 1 / 2; /* Solo 1 fila */
}
```

#### Ajustar gap:

```css
gap: 30px; /* Más espacio entre elementos */
```

---

## 💡 Ejercicios Adicionales

### Nivel 1: Modificaciones Básicas

1. Cambia los colores del gradiente del header
2. Ajusta el tamaño del gap en el grid principal
3. Modifica el número de columnas a 4 o 8

### Nivel 2: Reorganización

4. Intercambia la posición del featured article con el secondary
5. Haz que los small articles ocupen 2 columnas cada uno
6. Mueve el sidebar-ad a la izquierda

### Nivel 3: Nuevos Elementos

7. Agrega una nueva sección de "Trending" que ocupe 6 columnas x 1 fila
8. Crea una galería de imágenes con auto-fit
9. Implementa un layout alternativo usando `grid-template-areas`

### Nivel 4: Features Modernas

10. Experimenta con `subgrid` si tu navegador lo soporta
11. Usa `container queries` para los artículos
12. Implementa dark mode con CSS variables

---

## 📱 Responsive Breakpoints

```css
/* Desktop: 1024px+ */
grid-template-columns: repeat(6, 1fr);

/* Tablet: 768px - 1024px */
@media (max-width: 1024px) {
	grid-template-columns: repeat(4, 1fr);
}

/* Mobile: hasta 768px */
@media (max-width: 768px) {
	grid-template-columns: 1fr;
}
```

---

## 🎯 Checklist del Proyecto

- [x] Layout de 3+ áreas principales (7 secciones diferentes)
- [x] Grid template areas nombradas (ejemplo en footer)
- [x] Elementos spanning múltiples tracks (5 elementos)
- [x] Uso de minmax() y fr (aplicado en filas y columnas)
- [x] Auto-fit para responsividad (footer y ejemplo bonus)
- [x] Responsive con media queries (3 breakpoints)
- [x] Hover effects y transiciones
- [x] Tipografía y colores modernos

---

## 🔍 Análisis del Código

### Grid Container Principal

```css
.magazine-grid {
	display: grid;
	grid-template-columns: repeat(6, 1fr);
	grid-auto-rows: minmax(200px, auto);
	gap: 20px;
}
```

**Qué hace:**

- Crea un grid de 6 columnas iguales (1fr cada una)
- Las filas tienen mínimo 200px pero se expanden según contenido
- 20px de espacio entre todas las celdas

### Spanning de Elementos

```css
.article.featured {
	grid-column: 1 / 5; /* Ocupa columnas 1, 2, 3, 4 */
	grid-row: 1 / 3; /* Ocupa filas 1 y 2 */
}
```

**Cómo leerlo:**

- `1 / 5` significa "desde la línea 1 hasta la línea 5"
- Esto abarca 4 columnas (1→2, 2→3, 3→4, 4→5)

---

## 🆕 Features de CSS Grid 2025 Usadas

### 1. **Logical Properties**

```css
inline-size: 100%; /* En lugar de width */
block-size: 100%; /* En lugar de height */
```

### 2. **Modern Functions**

```css
minmax(200px, auto)
repeat(6, 1fr)
repeat(auto-fit, minmax(250px, 1fr))
```

### 3. **Gap (no grid-gap)**

```css
gap: 20px; /* Propiedad moderna estándar */
```

---

## 🎓 Recursos para Aprender Más

- [MDN CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
- [CSS Tricks Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Grid by Example](https://gridbyexample.com/)
- [Can I Use - Grid Support](https://caniuse.com/css-grid)

---

## 🏆 Objetivos de Aprendizaje Alcanzados

✅ Dominar la creación de grids complejos  
✅ Posicionar elementos en múltiples celdas  
✅ Usar minmax() y fr para layouts flexibles  
✅ Implementar responsive grid con media queries  
✅ Combinar Grid con Flexbox para componentes  
✅ Aplicar mejores prácticas modernas (2025)

---

**¡Felicidades por completar el proyecto Magazine Layout! 🎉**

Ahora dominas CSS Grid y puedes crear cualquier tipo de layout bidimensional complejo para proyectos profesionales.
