# Flexbox - Sistema de Layout Unidimensional Flexible

## 📖 Teoría

Flexbox es un sistema de layout CSS diseñado para distribuir espacio y alinear elementos a lo largo de **una dimensión** (fila o columna). Es la herramienta perfecta para componentes como navegaciones, cards, toolbars y cualquier layout que necesite distribución automática de espacio. Se activa con `display: flex` en el contenedor padre.

## 💡 Concepto Clave

**Flex Container + Flex Items**: El elemento con `display: flex` se convierte en contenedor flexible, y sus hijos directos en items flexibles que pueden crecer, encogerse y alinearse automáticamente.

---

## 🎯 Propiedades del Contenedor (Flex Container)

### 1. `display: flex`
Activa el contexto de flexbox en el contenedor.

```css
.container {
  display: flex; /* Los hijos se vuelven flex items */
}
```

---

### 2. `flex-direction` - Dirección del eje principal

```css
.container {
  flex-direction: row;          /* ➡️ Horizontal (default) */
  flex-direction: column;        /* ⬇️ Vertical */
  flex-direction: row-reverse;   /* ⬅️ Horizontal invertido */
  flex-direction: column-reverse; /* ⬆️ Vertical invertido */
}
```

**¿Cuándo usar?**
- `row`: Navegaciones horizontales, toolbars
- `column`: Sidebars, formularios verticales, layouts mobile-first

---

### 3. `justify-content` - Alineación en el eje principal

Distribuye el espacio **sobrante** entre/alrededor de los items.

```css
.container {
  justify-content: flex-start;   /* ⬅️ Inicio (default) */
  justify-content: center;       /* ⬛ Centro */
  justify-content: flex-end;     /* ➡️ Final */
  justify-content: space-between; /* ⬛ ⬛ ⬛ */
  justify-content: space-around;  /* ⬛ ⬛ ⬛ (espacio alrededor) */
  justify-content: space-evenly;  /* ⬛ ⬛ ⬛ (espacio igual) */
}
```

**Recomendación 2025**: `space-evenly` para distribución uniforme moderna.

---

### 4. `align-items` - Alineación en el eje transversal

Alinea items en el eje **perpendicular** al principal.

```css
.container {
  align-items: stretch;    /* Estirar (default) */
  align-items: flex-start; /* Arriba/Izquierda */
  align-items: center;     /* Centro (muy común) */
  align-items: flex-end;   /* Abajo/Derecha */
  align-items: baseline;   /* Línea base del texto */
}
```

**Uso típico**: `align-items: center` para centrado vertical perfecto.

---

### 5. `gap` - Espaciado moderno entre items

```css
.container {
  gap: 1rem;              /* Espacio igual horizontal y vertical */
  gap: 1rem 2rem;         /* row-gap column-gap */
  row-gap: 1rem;          /* Solo filas */
  column-gap: 2rem;       /* Solo columnas */
}
```

**✅ Mejor práctica 2025**: Usa `gap` en lugar de `margin` para espaciado entre items.

---

### 6. `flex-wrap` - Salto de línea

```css
.container {
  flex-wrap: nowrap;       /* No saltar línea (default) */
  flex-wrap: wrap;         /* ✅ Saltar a nueva línea */
  flex-wrap: wrap-reverse; /* Saltar invertido */
}
```

**Clave para responsive**: `flex-wrap: wrap` permite que items se adapten automáticamente.

---

### 7. `align-content` - Distribución de líneas múltiples

Solo funciona cuando hay **múltiples líneas** (`flex-wrap: wrap`).

```css
.container {
  flex-wrap: wrap;
  align-content: space-between; /* Distribuye líneas */
  align-content: center;        /* Centra líneas */
}
```

---

## 🎯 Propiedades de los Items (Flex Items)

### 1. `flex-grow` - Capacidad de crecer

Define qué tan rápido crece un item comparado con otros.

```css
.item {
  flex-grow: 0; /* No crece (default) */
  flex-grow: 1; /* Crece proporcionalmente */
  flex-grow: 2; /* Crece el doble que los demás */
}
```

**Ejemplo práctico**: Sidebar fijo + contenido que crece
```css
.sidebar { flex-grow: 0; }
.main { flex-grow: 1; } /* Ocupa todo el espacio restante */
```

---

### 2. `flex-shrink` - Capacidad de encogerse

Define qué tan rápido se encoge un item cuando no hay espacio.

```css
.item {
  flex-shrink: 1; /* Se encoge (default) */
  flex-shrink: 0; /* ✅ No se encoge (mantiene tamaño) */
}
```

---

### 3. `flex-basis` - Tamaño base inicial

Tamaño del item **antes** de distribuir espacio sobrante.

```css
.item {
  flex-basis: auto;   /* Tamaño del contenido (default) */
  flex-basis: 200px;  /* Tamaño base fijo */
  flex-basis: 30%;    /* Tamaño base en porcentaje */
}
```

---

### 4. `flex` - Shorthand (Recomendado)

Combina `flex-grow`, `flex-shrink` y `flex-basis`.

```css
.item {
  flex: 1;           /* flex-grow: 1, flex-shrink: 1, flex-basis: 0 */
  flex: 0 0 200px;   /* No crece, no encoge, 200px base */
  flex: 1 1 auto;    /* Crece y encoge, tamaño automático */
}
```

**✅ Valores comunes 2025**:
- `flex: 1` → Item flexible que toma todo el espacio disponible
- `flex: 0 0 auto` → Item rígido que mantiene su tamaño
- `flex: 1 1 100%` → Item que ocupa fila completa en wrap

---

### 5. `align-self` - Alineación individual

Sobrescribe `align-items` para un item específico.

```css
.special-item {
  align-self: center;    /* Este item se centra verticalmente */
  align-self: flex-end;  /* Este va al final */
}
```

---

### 6. `order` - Reordenar visualmente

Cambia el orden visual sin modificar el HTML.

```css
.item-1 { order: 2; }
.item-2 { order: 1; } /* Aparece primero visualmente */
.item-3 { order: 3; }
```

**⚠️ Nota de accesibilidad**: El orden del DOM no cambia, solo el visual.

---

## 🚀 Ejemplos Prácticos Modernos (2025)

### Ejemplo 1: Centrado Perfecto

```html
<div class="center-container">
  <div class="card">¡Perfecto centrado!</div>
</div>
```

```css
.center-container {
  display: flex;
  justify-content: center; /* Centrado horizontal */
  align-items: center;     /* Centrado vertical */
  min-height: 100vh;       /* Altura completa */
}

.card {
  padding: 2rem;
  background: oklch(90% 0.1 200);
  border-radius: 8px;
}
```

---

### Ejemplo 2: Navegación Responsive con gap

```html
<nav class="navbar">
  <div class="logo">Logo</div>
  <ul class="nav-links">
    <li><a href="#">Inicio</a></li>
    <li><a href="#">Proyectos</a></li>
    <li><a href="#">Contacto</a></li>
  </ul>
</nav>
```

```css
.navbar {
  display: flex;
  justify-content: space-between; /* Logo a la izq, links a la der */
  align-items: center;
  padding: 1rem 2rem;
  background: oklch(20% 0.05 250);
}

.nav-links {
  display: flex;
  gap: 2rem; /* ✅ Espaciado moderno entre links */
  list-style: none;
}
```

---

### Ejemplo 3: Card Gallery Responsive

```html
<div class="gallery">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
  <div class="card">Card 4</div>
</div>
```

```css
.gallery {
  display: flex;
  flex-wrap: wrap;           /* ✅ Permite salto de línea */
  gap: 1.5rem;               /* ✅ Espaciado uniforme */
  padding: 2rem;
}

.card {
  flex: 1 1 250px;           /* Crece, encoge, base 250px */
  min-width: 250px;          /* Ancho mínimo */
  padding: 1.5rem;
  background: oklch(95% 0.02 180);
  border-radius: 8px;
}
```

**¿Por qué funciona?**
- `flex: 1 1 250px`: Cards intentan ser al menos 250px
- `flex-wrap: wrap`: Si no caben, saltan a nueva línea
- `gap`: Espaciado automático sin márgenes complejos

---

### Ejemplo 4: Layout Sidebar + Main (Holy Grail)

```html
<div class="layout">
  <aside class="sidebar">Sidebar</aside>
  <main class="main-content">Contenido principal</main>
</div>
```

```css
.layout {
  display: flex;
  gap: 1rem;
  min-height: 100vh;
}

.sidebar {
  flex: 0 0 250px;  /* No crece, no encoge, 250px fijo */
  background: oklch(95% 0.02 200);
}

.main-content {
  flex: 1;          /* Ocupa todo el espacio restante */
  padding: 2rem;
}
```

---

## 🔄 Flexbox vs Grid (¿Cuándo usar qué?)

### ✅ Usa Flexbox cuando:
- Layout **unidimensional** (fila o columna, no ambas)
- Componentes como navbars, toolbars, botones
- Necesitas alineación dinámica de items
- Distribución de espacio automática

### ✅ Usa Grid cuando:
- Layout **bidimensional** (filas Y columnas)
- Layouts de página completos
- Necesitas control preciso de filas y columnas

**💡 Mejor práctica 2025**: Combínalos. Grid para layouts, Flexbox para componentes dentro del grid.

---

## ✅ Patrón Recomendado: Flex Container Moderno

```css
.container {
  display: flex;
  flex-wrap: wrap;              /* Responsive automático */
  gap: clamp(1rem, 3vw, 2rem);  /* Gap fluido */
  justify-content: space-evenly; /* Distribución uniforme */
  align-items: center;           /* Centrado vertical */
}

.container > * {
  flex: 1 1 clamp(250px, 30%, 400px); /* Items fluidos */
}
```

**Ventajas**:
- ✅ Responsive sin media queries
- ✅ Gap fluido con clamp
- ✅ Items se adaptan automáticamente

---

## 📌 Casos de Uso Reales

| Componente | Propiedades clave |
|------------|-------------------|
| **Navbar** | `justify-content: space-between`, `align-items: center`, `gap` |
| **Card Gallery** | `flex-wrap: wrap`, `gap`, `flex: 1 1 300px` |
| **Botones alineados** | `justify-content: flex-end`, `gap` |
| **Centrado perfecto** | `justify-content: center`, `align-items: center` |
| **Footer sticky** | `flex-direction: column`, `min-height: 100vh`, `margin-top: auto` |

---

## 🎯 Mejores Prácticas 2025

1. **Usa `gap` en lugar de margins** → Código más limpio
2. **Prefiere `flex: 1` sobre anchos fijos** → Más flexible
3. **Combina `flex-wrap: wrap`** → Responsive automático
4. **`clamp()` para valores fluidos** → Responsive avanzado
5. **Logical properties**: `inline-start` vs `left` → Mejor i18n

---

# 💼 PROYECTO: Card Portfolio Gallery

## Descripción
Crear una galería de tarjetas de proyectos con navegación superior, **completamente responsive usando solo Flexbox** (sin media queries tradicionales).

## 🎯 Objetivos
- Navbar con logo y links
- Galería de 6-8 tarjetas adaptables
- Tarjetas con imagen, título, descripción y botón
- Layout que se adapta automáticamente

## 📋 Requisitos Técnicos

### 1. Estructura HTML
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Portfolio Gallery - Flexbox</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <!-- Navbar -->
  <nav class="navbar">
    <div class="logo">Mi Portfolio</div>
    <ul class="nav-links">
      <li><a href="#">Proyectos</a></li>
      <li><a href="#">Sobre mí</a></li>
      <li><a href="#">Contacto</a></li>
    </ul>
  </nav>

  <!-- Hero Section -->
  <section class="hero">
    <h1>Mis Proyectos</h1>
    <p>Explora mi trabajo reciente</p>
  </section>

  <!-- Card Gallery -->
  <main class="gallery">
    <article class="card">
      <div class="card-image">🎨</div>
      <h3>Proyecto 1</h3>
      <p>Diseño web moderno con Flexbox</p>
      <a href="#" class="btn">Ver más</a>
    </article>
    
    <article class="card">
      <div class="card-image">💻</div>
      <h3>Proyecto 2</h3>
      <p>Aplicación responsive</p>
      <a href="#" class="btn">Ver más</a>
    </article>
    
    <article class="card">
      <div class="card-image">🚀</div>
      <h3>Proyecto 3</h3>
      <p>Landing page con animaciones</p>
      <a href="#" class="btn">Ver más</a>
    </article>
    
    <!-- Agregar 3-5 cards más con emojis diferentes -->
  </main>

  <!-- Footer -->
  <footer class="footer">
    <p>&copy; 2025 Mi Portfolio</p>
  </footer>
</body>
</html>
```

### 2. CSS Base (Starter)

```css
/* Reset y Variables */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: system-ui, -apple-system, sans-serif;
  line-height: 1.6;
  color: oklch(20% 0.02 250);
}

/* TODO: Implementar con Flexbox */
```

## ✅ Checklist de Implementación

### Parte 1: Navbar (10 min)
- [ ] `display: flex` en `.navbar`
- [ ] `justify-content: space-between` para separar logo y links
- [ ] `.nav-links` con `display: flex` y `gap`
- [ ] `align-items: center` para centrado vertical
- [ ] Padding y background color

### Parte 2: Hero Section (5 min)
- [ ] `display: flex`, `flex-direction: column`
- [ ] `align-items: center` y `justify-content: center`
- [ ] `min-height` para altura
- [ ] Texto centrado

### Parte 3: Gallery (10 min)
- [ ] `.gallery` con `display: flex` y `flex-wrap: wrap`
- [ ] `gap` entre cards
- [ ] `.card` con `flex: 1 1 280px` (cards flexibles)
- [ ] `justify-content: center` o `space-evenly`

### Parte 4: Cards (7 min)
- [ ] `.card` con padding, border-radius, box-shadow
- [ ] Contenido de la card con `display: flex`, `flex-direction: column`
- [ ] `.card-image` centrado con Flexbox
- [ ] Botón con `align-self: flex-start` o centrado

### Parte 5: Footer (3 min)
- [ ] `display: flex`, `justify-content: center`, `align-items: center`
- [ ] Padding y background

## 🎨 Sugerencias de Diseño

```css
/* Paleta de colores recomendada */
--color-primary: oklch(60% 0.2 250);      /* Azul */
--color-background: oklch(98% 0.01 250);  /* Casi blanco */
--color-card: oklch(100% 0 0);            /* Blanco */
--color-text: oklch(20% 0.02 250);        /* Casi negro */
--color-accent: oklch(70% 0.15 180);      /* Verde/cyan */

/* Espaciado */
gap: clamp(1rem, 2vw, 2rem);

/* Tamaño de cards */
flex: 1 1 clamp(250px, 30%, 350px);
```

## 🎯 Desafíos Extra (Si terminas antes)

1. **Hover effects en cards**: Escala o elevación
2. **Botón sticky "Volver arriba"** con Flexbox
3. **Agregar filtros** (botones con Flexbox)
4. **Footer con múltiples columnas** usando Flexbox

## 📌 Conceptos Clave a Aplicar

✅ `display: flex` en contenedores  
✅ `justify-content` y `align-items` para alineación  
✅ `flex-wrap: wrap` para responsive  
✅ `gap` para espaciado moderno  
✅ `flex: 1 1 [base]` para items flexibles  
✅ `flex-direction: column` donde sea necesario  

## ⏱️ Tiempo estimado: 30 minutos

¡Excelente práctica! Este proyecto te enseñará cómo Flexbox puede crear layouts completamente responsive **sin necesidad de media queries complicadas**. El truco está en combinar `flex-wrap: wrap` con valores `flex` inteligentes y `gap` para espaciado automático.

**💡 Tip**: Empieza por el navbar, luego el hero, después las cards, y finalmente ajusta tamaños y colores. ¡Manos a la obra! 🚀