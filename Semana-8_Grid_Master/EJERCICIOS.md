# 🎯 Ejercicios Prácticos - CSS Grid

## Instrucciones Generales

- Crea un archivo HTML/CSS por cada ejercicio
- Usa las técnicas aprendidas en la semana
- Experimenta y prueba diferentes soluciones
- Verifica en DevTools cómo funciona tu grid
- Haz tu solución responsive

---

## 📝 NIVEL 1: FUNDAMENTOS

### Ejercicio 1.1: Grid Básico 3x3

**Objetivo:** Crear un grid simple de 9 celdas (3x3)

**Requisitos:**

- 3 columnas de igual tamaño usando `fr`
- 3 filas de 150px cada una
- Gap de 15px
- Cada celda con color de fondo diferente
- Centrar contenido dentro de cada celda

**Bonus:** Hacer hover effects en las celdas

---

### Ejercicio 1.2: Spanning Básico

**Objetivo:** Practicar hacer que elementos ocupen múltiples celdas

**Requisitos:**

- Grid de 4 columnas x 3 filas
- Elemento 1: Ocupa 2 columnas x 1 fila
- Elemento 2: Ocupa 1 columna x 2 filas
- Elemento 3: Ocupa 3 columnas x 1 fila
- Resto de elementos: 1 celda cada uno
- Gap de 20px

**Visualización esperada:**

```
┌─────────────┬──────┬──────┐
│      1      │  3   │  4   │
├─────────────┼──────┼──────┤
│   5    │ 6  │  2   │  7   │
│        │    │      │      │
├────────┴────┴──────┴──────┤
│          Elemento 3        │
└────────────────────────────┘
```

---

### Ejercicio 1.3: Galería de Imágenes

**Objetivo:** Crear una galería simple con grid

**Requisitos:**

- Grid de 4 columnas
- Al menos 12 items (pueden ser divs con emoji o texto)
- Usar `repeat()` para las columnas
- Grid auto-rows de 200px
- Gap de 10px
- Cada 5to elemento debe ocupar 2 columnas

---

## 📝 NIVEL 2: INTERMEDIO

### Ejercicio 2.1: Layout con Grid Template Areas

**Objetivo:** Crear un layout de blog usando template areas

**Requisitos:**

- Usar `grid-template-areas`
- Estructura:
  - Header (ancho completo)
  - Sidebar izquierdo (250px)
  - Main content (flexible)
  - Sidebar derecho (300px)
  - Footer (ancho completo)
- Min-height: 100vh
- Gap de 15px
- Responsive: En mobile, cambiar a layout vertical

**Código inicial:**

```css
grid-template-areas:
	"header header header"
	"sidebar-left main sidebar-right"
	"footer footer footer";
```

---

### Ejercicio 2.2: Card Grid Responsive

**Objetivo:** Galería de cards que se adapta automáticamente

**Requisitos:**

- Usa `auto-fit` con `minmax()`
- Cada card debe tener:
  - Imagen (200px altura)
  - Título
  - Descripción
  - Footer con botón
- Mínimo 250px, máximo 1fr por card
- Gap de 20px
- Cards con border-radius y box-shadow
- Hover effect: translateY y shadow

---

### Ejercicio 2.3: Masonry-style Grid

**Objetivo:** Crear un grid estilo Pinterest

**Requisitos:**

- Grid con `auto-fit`
- Items de diferentes alturas
- Usar `grid-row-end: span X` para diferentes alturas
- Mínimo 8 items
- Algunos items ocupan 1 row
- Otros ocupan 2 rows
- Otros ocupan 3 rows
- Gap de 15px

**Tip:** Usa `grid-auto-rows: 50px` para crear unidades pequeñas

---

## 📝 NIVEL 3: AVANZADO

### Ejercicio 3.1: Dashboard Completo

**Objetivo:** Crear un dashboard funcional

**Requisitos:**

- Sidebar fijo (250px)
- Header con búsqueda y perfil
- 4 stats cards (1 columna cada una)
- Chart principal (3 columnas x 2 filas)
- 2 charts secundarios (1 columna cada uno)
- Lista de actividades (2 columnas)
- Grid de al menos 5 columnas
- Responsive completo (desktop, tablet, mobile)

**Estructura:**

```
┌─────┬────────────────────────────┐
│     │         Header             │
│ S   ├───┬───┬───┬────────────────┤
│ i   │ 1 │ 2 │ 3 │       4        │
│ d   ├───┴───┴───┼────────────────┤
│ e   │           │                │
│ b   │  Main     │   Side         │
│ a   │  Chart    │   Chart        │
│ r   │           │                │
│     ├───────────┴────────────────┤
│     │      Activity Feed         │
└─────┴────────────────────────────┘
```

---

### Ejercicio 3.2: Magazine Layout Personalizado

**Objetivo:** Crear tu propio diseño de revista

**Requisitos:**

- Grid de 6 columnas mínimo
- Al menos 10 artículos
- Featured article (4 columnas x 2 filas)
- 2 artículos medianos (2 columnas x 2 filas cada uno)
- 4 artículos pequeños (1 columna x 1 fila)
- 2 artículos horizontales (3 columnas x 1 fila)
- 1 sidebar ad (2 columnas x 3 filas)
- Gap de 20px
- Responsive (desktop → tablet → mobile)

---

### Ejercicio 3.3: E-commerce Product Grid

**Objetivo:** Grid de productos con funcionalidad avanzada

**Requisitos:**

- Auto-fit responsive
- Cada producto card debe tener:
  - Imagen (aspect-ratio 4:3)
  - Badge de "Nuevo" o "Oferta"
  - Título del producto
  - Precio (tachado si está en oferta)
  - Rating con estrellas
  - Botón "Agregar al carrito"
- Mínimo 16 productos
- Filtros en la parte superior
- Cada 6to producto es "destacado" y ocupa 2 columnas

**Bonus:**

- Implementar estados: normal, hover, featured
- Agregar skeleton loading state

---

## 📝 NIVEL 4: EXPERTO

### Ejercicio 4.1: Netflix-style Grid

**Objetivo:** Grid dinámico estilo Netflix

**Requisitos:**

- Múltiples filas de contenido
- Cada fila es un grid horizontal con scroll
- Títulos de categorías
- Cards con hover effect (scale + shadow)
- Featured content (16:9 ratio, ancho completo)
- Responsive

**Estructura de cada fila:**

```css
.content-row {
	display: grid;
	grid-auto-flow: column;
	grid-auto-columns: minmax(200px, 1fr);
	gap: 10px;
	overflow-x: auto;
}
```

---

### Ejercicio 4.2: Calendario Mensual

**Objetivo:** Crear un calendario con Grid

**Requisitos:**

- Grid de 7 columnas (días de la semana)
- Headers: Lun, Mar, Mié, Jue, Vie, Sáb, Dom
- 5-6 filas (semanas)
- Días del mes actual
- Días del mes anterior/siguiente (opacidad reducida)
- Día actual destacado
- Eventos en algunos días
- Responsive: En mobile mostrar semana actual

**Funcionalidades:**

- Click en día para ver eventos
- Hover effect en días
- Badge con número de eventos

---

### Ejercicio 4.3: Admin Dashboard Completo

**Objetivo:** Dashboard profesional completo

**Requisitos:**

- Sidebar colapsable
- Top navbar con notifications
- Grid principal con:
  - 6 stats cards (3 columnas x 2 filas)
  - 1 main chart (4 columnas x 3 filas)
  - 1 map widget (2 columnas x 3 filas)
  - 1 recent activity (3 columnas x 2 filas)
  - 1 tasks list (3 columnas x 2 filas)
- Mini charts en stats cards
- Data tables
- Modal functionality
- 3 breakpoints responsive

**Features avanzadas:**

- Dark mode toggle
- Grid reorganizable (drag & drop opcional)
- Animaciones suaves
- Loading states

---

## 🎯 PROYECTO FINAL: Sistema Completo

### Ejercicio 5: Portfolio Personal con Grid

**Objetivo:** Crear un portfolio completo usando Grid

**Requisitos obligatorios:**

1. **Homepage:**

   - Hero section (grid de 2 columnas)
   - Sobre mí (grid asimétrico)
   - Skills grid (auto-fit)
   - Featured projects (3 columnas)

2. **Projects Page:**

   - Grid de proyectos con filtros
   - Proyecto destacado (4 columnas x 2 filas)
   - Proyectos secundarios (2 columnas x 1 fila)
   - Proyectos pequeños (1 columna x 1 fila)

3. **Blog Page:**

   - Layout tipo magazine
   - Featured post
   - Grid de posts con categorías
   - Sidebar con widgets

4. **Contact Page:**
   - Form con grid layout
   - Mapa de ubicación
   - Información de contacto

**Requisitos técnicos:**

- Mínimo 4 páginas
- Completamente responsive (mobile, tablet, desktop)
- Usar grid-template-areas donde corresponda
- Auto-fit para galerías
- Combinación de Grid + Flexbox
- Animaciones y transitions
- Dark/Light mode

**Bonus:**

- Subgrid implementado
- Container queries
- Performance optimizada
- Accesibilidad completa

---

## ✅ Criterios de Evaluación

### Para cada ejercicio, evalúa:

**Funcionalidad (40%):**

- [ ] Cumple todos los requisitos
- [ ] Grid funciona correctamente
- [ ] Responsive en todos los breakpoints

**Código (30%):**

- [ ] HTML semántico
- [ ] CSS organizado
- [ ] Uso correcto de propiedades Grid
- [ ] Código comentado

**Diseño (20%):**

- [ ] Visualmente atractivo
- [ ] Espaciado consistente
- [ ] Paleta de colores armoniosa
- [ ] Tipografía legible

**Extras (10%):**

- [ ] Animaciones/transitions
- [ ] Hover effects
- [ ] Detalles adicionales
- [ ] Creatividad

---

## 💡 Tips para Resolver los Ejercicios

### 1. **Planifica primero**

- Dibuja el layout en papel
- Identifica filas y columnas
- Decide qué elementos spanning necesitas

### 2. **Usa DevTools**

- Activa el overlay de grid en el inspector
- Verifica números de línea
- Experimenta en tiempo real

### 3. **Mobile-first**

- Empieza con diseño mobile (1 columna)
- Agrega complejidad con media queries
- Prueba en diferentes dispositivos

### 4. **Nombra bien tus clases**

- `.grid-container` para el contenedor
- `.grid-item` para items genéricos
- `.featured-item` para items especiales

### 5. **Comenta tu código**

- Explica decisiones de diseño
- Documenta valores especiales
- Nota áreas que pueden mejorarse

---

## 🎓 Recursos Útiles

### Para practicar interactivamente:

- [Grid Garden](https://cssgridgarden.com/) - Juego para aprender Grid
- [CSS Grid Generator](https://cssgrid-generator.netlify.app/) - Generador visual

### Para inspiración:

- [CSS Tricks Grid Examples](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Grid by Example](https://gridbyexample.com/)
- [Codepen Grid Tags](https://codepen.io/tag/grid)

### Para debugging:

- Chrome DevTools Grid Inspector
- Firefox Grid Inspector
- Edge DevTools Grid Tools

---

## 📊 Progreso Recomendado

### Semana 8 - Día 1-2:

- Ejercicios Nivel 1 (1.1 - 1.3)
- Revisar teoría

### Semana 8 - Día 3-4:

- Ejercicios Nivel 2 (2.1 - 2.3)
- Experimentar con ejemplos

### Semana 8 - Día 5-6:

- Ejercicios Nivel 3 (3.1 - 3.3)
- Proyecto magazine del curso

### Semana 8 - Día 7:

- Ejercicio Nivel 4 (elegir uno)
- Revisar y refactorizar código

**Extra:** Proyecto Final (1-2 semanas adicionales)

---

## 🏆 Checklist de Dominio

Al terminar estos ejercicios, deberías poder:

- [ ] Crear grids de cualquier complejidad
- [ ] Usar grid-template-areas con confianza
- [ ] Hacer spanning de elementos sin problemas
- [ ] Implementar grids responsive sin media queries (auto-fit)
- [ ] Combinar Grid con Flexbox eficientemente
- [ ] Debuggear problemas de Grid con DevTools
- [ ] Crear layouts profesionales tipo dashboard
- [ ] Optimizar performance de grids complejos

---

**¡Éxito con los ejercicios! 🚀**

Recuerda: La práctica hace al maestro. No te frustres si algo no sale a la primera, experimenta y aprende de cada intento.
