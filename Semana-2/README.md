# 📊 Dashboard de Estadísticas - Proyecto Semana 2

## 🎯 Objetivo del Proyecto

Crear un dashboard de estadísticas moderno aplicando **todos los conceptos de Box Model y unidades CSS** aprendidos en la Semana 2.

## ✅ Requisitos Cumplidos

### 📋 Requisitos Funcionales

- [x] **8 tarjetas de estadísticas** (superando el mínimo de 6)

  - 4 estadísticas principales (Usuarios, Ventas, Pedidos, Conversión)
  - 4 métricas secundarias (Tiempo, Páginas, Rebote, Móviles)

- [x] **Cards con Box Model aplicado correctamente**

  - Padding, margin y borders bien definidos
  - `box-sizing: border-box` en todo el proyecto

- [x] **Uso de 4+ tipos de unidades**

  - `rem` para tipografía y spacing
  - `em` para iconos proporcionales
  - `%` para layouts fluidos
  - `vw/vh` para responsive
  - `px` para borders y shadows precisos

- [x] **Shadows y borders creativos**

  - Múltiples niveles de sombra
  - Borders laterales por prioridad
  - Efectos hover con elevación

- [x] **Responsive con unidades relativas**
  - CSS Grid con `auto-fit` y `minmax()`
  - Sin breakpoints fijos, totalmente fluido

### 🛠️ Conceptos CSS Aplicados

#### 1. Box Model Completo

```css
.stat-card {
	/* Content area */
	padding: var(--spacing-lg); /* Espacio interno */
	border: 1px solid var(--color-gray-200); /* Border */
	margin-bottom: var(--spacing-xl); /* Espacio externo */
	/* Todo con box-sizing: border-box para cálculo intuitivo */
}
```

#### 2. Unidades Modernas 2025

- **rem**: Escalable con font-size raíz
- **clamp()**: Tipografía fluida sin media queries
- **calc()**: Cálculos precisos mezclando unidades
- **min()/max()**: Límites automáticos
- **vw/vh**: Responsive al viewport

#### 3. CSS Grid Responsive

```css
.stats-grid {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(min(100%, 280px), 1fr));
	gap: clamp(1rem, 3vw, 2rem);
}
```

#### 4. CSS Variables (Custom Properties)

- Sistema de colores consistente
- Spacing escalable
- Tipografía fluida
- Sombras por niveles

#### 5. Data Attributes para Estilos Condicionales

```html
<div class="stat-card" data-priority="high" data-stat-type="users"></div>
```

```css
[data-priority="high"] {
	border-left: 4px solid var(--color-accent);
}
```

## 🎨 Características Visuales

### Colores y Branding

- **Primario**: `#2c3e50` (Azul oscuro)
- **Secundario**: `#3498db` (Azul claro)
- **Éxito**: `#2ecc71` (Verde)
- **Error**: `#e74c3c` (Rojo)
- **Advertencia**: `#f39c12` (Naranja)

### Tipografía Fluida

```css
:root {
	--font-size-xs: clamp(0.75rem, 1vw, 0.875rem);
	--font-size-base: clamp(1rem, 2vw, 1.125rem);
	--font-size-3xl: clamp(2rem, 5vw, 3rem);
}
```

### Efectos Interactivos

- **Hover**: Elevación con `translateY(-4px)`
- **Sombras**: Múltiples niveles de profundidad
- **Transiciones**: Suaves y naturales
- **Focus**: Estados accesibles

## 📱 Responsive Design

### Móvil (< 480px)

- 1 columna
- Padding reducido
- Iconos centrados

### Tablet (480px - 768px)

- 1-2 columnas
- Spacing medio

### Desktop (> 768px)

- 4 columnas máximo
- Layout completo

### Funciones Responsivas Usadas

```css
/* Sin media queries gracias a clamp() */
padding: clamp(1rem, 3vw, 2rem);
font-size: clamp(1.25rem, 4vw, 2.5rem);
grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
```

## 🚀 Funciones CSS Modernas Aplicadas

### calc()

```css
padding-top: calc(var(--spacing-sm) + 2px);
height: calc(100vh - 120px);
```

### min() / max()

```css
padding: min(3vw, var(--spacing-xl));
width: max(50%, 300px);
```

### clamp()

```css
/* Tipografía que escala suavemente */
font-size: clamp(1.75rem, 4vw, 2.5rem);
gap: clamp(1rem, 3vw, 2rem);
```

## 📊 Estadísticas del Proyecto

- **Líneas HTML**: ~160
- **Líneas CSS**: ~400+
- **Variables CSS**: 25+
- **Tarjetas**: 8
- **Data Attributes**: 16+
- **Funciones CSS usadas**: calc(), min(), max(), clamp()
- **Unidades diferentes**: rem, em, %, vw, vh, px

## 🏗️ Estructura de Archivos

```
Semana-2/
├── index.html          # Estructura HTML del dashboard
├── styles.css          # Estilos CSS completos
├── teoria-semana-2.md  # Teoría de conceptos
└── README.md           # Esta documentación
```

## ✅ Checklist de Verificación

### Box Model

- [x] `box-sizing: border-box` aplicado universalmente
- [x] Padding usando `rem` para escalabilidad
- [x] Margins con espaciado consistente
- [x] Borders con `px` para precisión
- [x] Content area bien definida

### Unidades CSS

- [x] `rem` para tipografía y spacing
- [x] `em` para elementos proporcionales (iconos)
- [x] `%` para layouts fluidos
- [x] `vw/vh` para responsive
- [x] `px` para detalles precisos

### Funciones CSS

- [x] `calc()` para cálculos complejos
- [x] `min()` para límites superiores
- [x] `max()` para límites inferiores
- [x] `clamp()` para valores fluidos

### Layout y Grid

- [x] CSS Grid con `auto-fit`
- [x] `minmax()` para flexibilidad
- [x] `gap` para espaciado uniforme
- [x] Responsive sin media queries

### Efectos Visuales

- [x] Box shadows múltiples
- [x] Hover effects suaves
- [x] Transiciones performantes
- [x] Estados de focus accesibles

### Data Attributes

- [x] Estilos condicionales por prioridad
- [x] Atributos semánticos
- [x] CSS que reacciona a data

## 🎓 Conceptos Dominados

Al completar este proyecto, has aplicado exitosamente:

1. **Box Model completo** con todas sus capas
2. **box-sizing: border-box** como estándar
3. **Unidades relativas** para responsive design
4. **Funciones CSS modernas** para layouts fluidos
5. **CSS Grid** con auto-fit para responsive
6. **Variables CSS** para mantener consistencia
7. **Data attributes** para estilos condicionales
8. **Efectos visuales** con shadows y transforms
9. **Responsive design** sin frameworks
10. **Accesibilidad** básica con focus states

## 🔄 Próximos Pasos

Este proyecto te prepara para:

- **Semana 3**: Tipografía avanzada
- **Semana 4**: Colores y gradientes
- **Semana 5**: Selectores avanzados
- Proyectos más complejos con estos fundamentos sólidos

---

**¡Excelente trabajo dominando Box Model y unidades CSS! 🎉**

_Proyecto completado - Semana 2 del Curso CSS Avanzado 2025_
