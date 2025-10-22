# 💼 Proyecto Semana 6: Header Sticky con Modal

## 🎯 Descripción

Landing page profesional que implementa:

- **Header Sticky** que permanece visible al hacer scroll
- **Modal centrado** con overlay y animaciones
- **Z-index management** con sistema escalado
- **FAB (Floating Action Button)** para scroll to top
- **Responsive design** completo

---

## ✨ Características Implementadas

### 🔝 Header Sticky (Position: Sticky)

- ✅ Header que se "pega" al top al hacer scroll
- ✅ Efecto de sombra al scroll
- ✅ Navegación con active states
- ✅ Menu mobile responsive
- ✅ Backdrop blur effect (moderno)

**Técnicas CSS usadas:**

```css
.header {
	position: sticky;
	top: 0;
	z-index: var(--z-sticky);
}
```

### 🎭 Modal con Overlay (Position: Fixed)

- ✅ Modal centrado en pantalla
- ✅ Overlay semi-transparente con blur
- ✅ Animaciones de entrada/salida
- ✅ Close button con position absolute
- ✅ Cierre con ESC key
- ✅ Cierre al click fuera del modal
- ✅ Form funcional

**Técnicas CSS usadas:**

```css
.modal-overlay {
	position: fixed;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
	z-index: var(--z-modal-backdrop);
}

.modal {
	position: relative;
	z-index: var(--z-modal);
}
```

### 📊 Z-Index Management

Sistema escalado con CSS Variables (✅ Mejor Práctica 2025):

```css
:root {
	--z-dropdown: 1000;
	--z-sticky: 1020;
	--z-fixed: 1030;
	--z-modal-backdrop: 1040;
	--z-modal: 1050;
	--z-notification: 1060;
	--z-tooltip: 1070;
}
```

### 🔄 Floating Action Button (Position: Fixed)

- ✅ Botón flotante en esquina inferior derecha
- ✅ Aparece después de scroll
- ✅ Scroll suave al top
- ✅ Animación de entrada

**Técnicas CSS usadas:**

```css
.fab {
	position: fixed;
	bottom: 2rem;
	right: 2rem;
	z-index: var(--z-fixed);
}
```

---

## 🚀 Cómo Probarlo

### Opción 1: Abrir directamente

1. Abre `index.html` en tu navegador
2. Haz scroll para ver el header sticky
3. Click en "Solicitar Demo" para abrir el modal
4. Scroll down para ver el FAB aparecer

### Opción 2: Live Server (recomendado)

1. Si usas VS Code, instala la extensión "Live Server"
2. Click derecho en `index.html` → "Open with Live Server"
3. Se abrirá en `localhost:5500`

---

## 🧪 Funcionalidades a Probar

### ✅ Checklist de Pruebas

**Header Sticky:**

- [ ] El header se mantiene visible al hacer scroll
- [ ] Aparece sombra después de 50px de scroll
- [ ] Los enlaces de navegación marcan la sección activa
- [ ] En mobile, el menú hamburguesa funciona
- [ ] El logo es clickeable

**Modal:**

- [ ] Click en "Solicitar Demo" abre el modal
- [ ] Click en el botón X cierra el modal
- [ ] Click en "Cancelar" cierra el modal
- [ ] Click fuera del modal lo cierra
- [ ] Presionar ESC cierra el modal
- [ ] El scroll de la página se bloquea cuando el modal está abierto
- [ ] El formulario se puede llenar y enviar

**FAB (Scroll to Top):**

- [ ] El botón aparece después de 500px de scroll
- [ ] Click hace scroll suave al top
- [ ] Desaparece cuando estás arriba

**Responsive:**

- [ ] Cambia el tamaño de la ventana para ver cambios
- [ ] En mobile, el menú es vertical
- [ ] Los botones se adaptan al ancho
- [ ] El modal es responsive

---

## 📚 Conceptos CSS Aplicados

### Position Values

| Property   | Uso en el Proyecto                       |
| ---------- | ---------------------------------------- |
| `sticky`   | Header principal                         |
| `fixed`    | Modal overlay, FAB button, Mobile menu   |
| `absolute` | Close button, Portfolio tags             |
| `relative` | Cards, Nav links (para pseudo-elementos) |

### Display Values

| Property       | Uso en el Proyecto         |
| -------------- | -------------------------- |
| `flex`         | Header, Navigation, Grids  |
| `grid`         | Services, Portfolio, Stats |
| `inline-block` | Botones, Tags              |
| `none`         | Estados ocultos            |

### Z-Index Hierarchy

```
Base Layer:        1
Dropdown:          1000
Sticky Header:     1020
Fixed Elements:    1030
Modal Backdrop:    1040
Modal:             1050
Notifications:     1060
Tooltips:          1070
```

---

## 🎨 Técnicas Modernas (2025)

### 1. CSS Custom Properties

```css
:root {
	--z-modal: 1050;
	--color-primary: #667eea;
	--transition-base: 250ms ease;
}
```

### 2. Backdrop Filter

```css
.header.scrolled {
	backdrop-filter: blur(10px);
}
```

### 3. Logical Properties (Preparado para RTL)

```css
/* En lugar de left/right, usar: */
padding-inline: 2rem; /* left + right */
padding-block: 1rem; /* top + bottom */
```

### 4. clamp() para Responsive Typography

```css
font-size: clamp(2rem, 5vw, 3.5rem);
/* min: 2rem, ideal: 5vw, max: 3.5rem */
```

### 5. Modern Selectors

```css
.nav-link:focus-visible {
	/* Solo con teclado */
	outline: 2px solid var(--color-primary);
}
```

---

## 🔧 Estructura de Archivos

```
Semana-6_Posicionamiento_y_Display/
├── index.html          # HTML completo con semantic markup
├── style.css           # CSS con todas las técnicas modernas
├── teoria_semana-6.md  # Teoría completa de la semana
└── README.md           # Este archivo
```

---

## 🎓 Lo que Aprendiste

### Position:

- ✅ `sticky` es mejor que `fixed` para headers en muchos casos
- ✅ `fixed` para modals y elementos que deben estar siempre visibles
- ✅ `absolute` para posicionar dentro de un contenedor `relative`
- ✅ `relative` crea contexto de posicionamiento

### Z-Index:

- ✅ Solo funciona con elementos posicionados
- ✅ Usar sistema escalado con CSS Variables
- ✅ Stacking context puede "atrapar" z-index de hijos
- ✅ `isolation: isolate` crea contexto sin position

### Display:

- ✅ `block` vs `inline` vs `inline-block`
- ✅ `display: none` vs `visibility: hidden`
- ✅ Flexbox para layouts unidimensionales
- ✅ Grid para layouts bidimensionales

### Overflow:

- ✅ `overflow: auto` para scroll cuando sea necesario
- ✅ `overflow: hidden` para recortar contenido
- ✅ `text-overflow: ellipsis` para truncar texto

---

## 🐛 Troubleshooting

### El header no se pega

```css
/* Asegúrate de: */
.header {
	position: sticky; /* no relative */
	top: 0; /* siempre definir top */
	z-index: 1020; /* mayor que contenido */
}
```

### El modal no aparece encima

```css
/* Verifica z-index: */
.modal-overlay {
	z-index: 1040; /* Debe ser muy alto */
}
```

### El modal no se centra

```css
.modal-overlay {
	display: flex;
	align-items: center;
	justify-content: center;
}
```

---

## 📈 Próximos Pasos

1. **Personaliza** los colores en las CSS Variables
2. **Agrega** más páginas al modal (tabs)
3. **Implementa** animaciones más complejas
4. **Conecta** el formulario a un backend real
5. **Optimiza** con lazy loading de imágenes

---

## 📖 Recursos Adicionales

- [MDN: CSS Position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
- [MDN: Z-Index](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index)
- [CSS Tricks: Position](https://css-tricks.com/almanac/properties/p/position/)
- [Can I Use: Sticky](https://caniuse.com/css-sticky)

---

**¡Excelente trabajo completando la Semana 6!** 🎉

Siguiente: **Semana 7 - Transitions, Transforms & Animations** 🎬
