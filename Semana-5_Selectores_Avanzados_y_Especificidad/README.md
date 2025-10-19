# 📅 SEMANA 5: Selectores Avanzados & Especificidad

## 🎯 Descripción del Proyecto

Este proyecto demuestra **todos los selectores avanzados de CSS** incluyendo combinadores, selectores de atributo, pseudo-clases, pseudo-clases modernas (2025), pseudo-elementos, y el sistema de especificidad.

---

## 📂 Archivos del Proyecto

```
Semana-5_Selectores_Avanzados_y_Especificidad/
├── index.html          # Ejemplos interactivos de todos los selectores
├── style.css           # CSS con comentarios explicativos
├── Semana-5_teoria.md  # Guía teórica completa
└── README.md           # Este archivo
```

---

## 🚀 Cómo Usar Este Proyecto

### Opción 1: Live Server (Recomendado)

1. Abre VS Code
2. Haz clic derecho en `index.html`
3. Selecciona **"Open with Live Server"**
4. Navega por las diferentes secciones

### Opción 2: Navegador Directo

1. Abre `index.html` directamente en tu navegador
2. Explora los ejemplos interactivos

---

## 📚 Temas Cubiertos

### 1️⃣ Combinadores CSS

- ✅ **Descendant** (espacio): `article p`
- ✅ **Child** (`>`): `ul > li`
- ✅ **Adjacent Sibling** (`+`): `h2 + p`
- ✅ **General Sibling** (`~`): `h2 ~ p`

### 2️⃣ Selectores de Atributo

- ✅ Existencia: `[required]`
- ✅ Valor exacto: `[type="email"]`
- ✅ Comienza con: `[href^="https://"]`
- ✅ Termina con: `[href$=".pdf"]`
- ✅ Contiene: `[href*="youtube"]`

### 3️⃣ Pseudo-clases Clásicas

- ✅ Estados: `:hover`, `:focus`, `:active`, `:visited`
- ✅ Estructurales: `:first-child`, `:last-child`, `:nth-child()`
- ✅ Negación: `:not()`

### 4️⃣ Pseudo-clases Modernas (2025) 🔥

- ✅ `:is()` - Simplificación
- ✅ `:where()` - Especificidad cero
- ✅ `:has()` - Selector padre (¡revolucionario!)

### 5️⃣ Pseudo-elementos

- ✅ `::before` y `::after` - Contenido decorativo
- ✅ `::first-letter` - Drop cap
- ✅ `::first-line` - Primera línea
- ✅ `::selection` - Selección de texto
- ✅ `::marker` - Viñetas personalizadas

### 6️⃣ Especificidad

- ✅ Cálculo de especificidad (a, b, c, d)
- ✅ Resolución de conflictos
- ✅ Mejores prácticas
- ✅ `!important` (cuándo evitarlo)

---

## 🎨 Características Destacadas

### Sistema de Cards Inteligente

El proyecto incluye un **componente complejo** que demuestra:

- Cards que detectan si contienen imagen (`:has(img)`)
- Cambio automático de layout grid/flexbox
- Links con iconos automáticos según tipo
- Filas alternas (zebra striping)
- Estados de hover y focus
- Primera y última card destacadas

### Ejemplos Interactivos

- ✅ Tablas con filas alternas
- ✅ Formularios con validación visual
- ✅ Links con iconos según tipo (PDF, externo, email)
- ✅ Notificaciones con iconos automáticos
- ✅ Citas con comillas decorativas
- ✅ Drop cap editorial

---

## 💡 Ejercicios Propuestos

### Nivel Básico ⭐

1. **Zebra Striping**: Crea una lista de productos con fondo alterno
2. **Links Externos**: Aplica icono a todos los links https://
3. **Primer Párrafo**: Destaca el primer párrafo después de cada h2

### Nivel Intermedio ⭐⭐

4. **Menú de Navegación**:

   - Hover effects
   - Active state
   - Focus visible para accesibilidad

5. **Formulario Inteligente**:

   - Campos requeridos con borde rojo
   - Validación visual con colores
   - Iconos según tipo de input

6. **Notificaciones**:
   - Success, warning, error
   - Iconos con ::before
   - Colores semánticos

### Nivel Avanzado ⭐⭐⭐

7. **Componente Adaptativo con :has()**:

   - Card que cambia layout si tiene imagen
   - Sidebar que detecta contenido
   - Grid que se adapta según items

8. **Sistema de Tags**:

   - Tags normales vs destacados
   - Hover effects
   - Contador automático con ::after

9. **Galería de Imágenes**:
   - Layout grid responsive
   - Overlay con ::before/::after
   - Primera y última imagen destacadas
   - nth-child para efectos escalonados

---

## 🔍 Inspecciona el Código

### Para Aprender Más:

1. **Abre las DevTools** (F12)
2. Inspecciona cualquier elemento
3. Ve a la pestaña "Computed"
4. Observa qué reglas se aplican y su especificidad

### Experimenta:

- Cambia valores en `style.css`
- Crea tus propios selectores
- Combina múltiples técnicas
- Prueba en diferentes navegadores

---

## 📊 Especificidad - Reglas Clave

```
ID (#selector)          > Clase (.selector)    > Elemento (div)
(0,1,0,0) = 100 puntos    (0,0,1,0) = 10 puntos   (0,0,0,1) = 1 punto
```

**Jerarquía:**

1. Inline styles (más específico)
2. IDs
3. Classes, pseudo-classes, attributes
4. Elements, pseudo-elements (menos específico)

**⚠️ Evita:**

- IDs para estilos (usa classes)
- `!important` (excepto utilities)
- Selectores muy profundos

**✅ Prioriza:**

- Classes reutilizables
- Especificidad baja
- Nombres semánticos

---

## 🎯 Proyecto Final: Smart Cards

El proyecto incluye un **sistema de cards adaptativo** que:

✅ Detecta automáticamente si contiene imagen  
✅ Cambia layout según contenido  
✅ Aplica estilos especiales a primera/última  
✅ Links con iconos según tipo  
✅ Hover effects suaves  
✅ Cards destacadas con clase

**Código clave:**

```css
/* Card que contiene imagen */
.smart-card:has(img) {
	display: grid;
	grid-template-columns: 1fr;
}

/* Links externos */
.smart-card a[href^="https://"]::after
{
	content: " ↗";
}

/* Primera card */
.smart-card:first-child {
	border: 3px solid var(--color-warning);
}
```

---

## 🚦 Compatibilidad de Navegadores

| Selector   | Chrome  | Firefox | Safari   | Edge    |
| ---------- | ------- | ------- | -------- | ------- |
| `:has()`   | ✅ 105+ | ✅ 121+ | ✅ 15.4+ | ✅ 105+ |
| `:is()`    | ✅ 88+  | ✅ 78+  | ✅ 14+   | ✅ 88+  |
| `:where()` | ✅ 88+  | ✅ 78+  | ✅ 14+   | ✅ 88+  |
| `::marker` | ✅ 86+  | ✅ 68+  | ✅ 11.1+ | ✅ 86+  |

**Nota:** Todos los selectores usados tienen excelente soporte en 2025.

---

## 📚 Recursos Adicionales

### Documentación

- [MDN: CSS Selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)
- [MDN: Specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)
- [CSS Tricks: Complete Guide to Selectors](https://css-tricks.com/almanac/)

### Herramientas

- [Specificity Calculator](https://specificity.keegan.st/)
- [Can I Use](https://caniuse.com/) - Compatibilidad de navegadores
- [CSS Validator](https://jigsaw.w3.org/css-validator/)

### Práctica

- [CSS Diner](https://flukeout.github.io/) - Juego de selectores
- [Selectors Explained](https://kittygiraudel.github.io/selectors-explained/)

---

## ✅ Checklist de Dominio

Marca cuando te sientas cómodo con cada concepto:

### Combinadores

- [ ] Entiendo la diferencia entre espacio y `>`
- [ ] Sé cuándo usar `+` vs `~`
- [ ] Puedo crear selectores complejos combinados

### Atributos

- [ ] Uso `[attr^="value"]` para prefijos
- [ ] Uso `[attr$="value"]` para sufijos
- [ ] Uso `[attr*="value"]` para coincidencias parciales

### Pseudo-clases

- [ ] Uso `:nth-child()` con fórmulas
- [ ] Entiendo `:nth-of-type()`
- [ ] Aplico estados hover/focus/active

### Pseudo-clases Modernas

- [ ] Uso `:is()` para simplificar código
- [ ] Entiendo la diferencia entre `:is()` y `:where()`
- [ ] Puedo usar `:has()` para seleccionar padres

### Pseudo-elementos

- [ ] Creo contenido decorativo con `::before`/`::after`
- [ ] Uso `::first-letter` para drop caps
- [ ] Personalizo `::selection` y `::marker`

### Especificidad

- [ ] Puedo calcular especificidad manualmente
- [ ] Entiendo por qué un estilo sobrescribe otro
- [ ] Evito `!important` y alta especificidad

---

## 🎓 Próximos Pasos

1. ✅ Completa todos los ejercicios propuestos
2. ✅ Experimenta con combinaciones de selectores
3. ✅ Crea tu propio proyecto usando estos conceptos
4. ✅ Revisa el código de `style.css` línea por línea
5. ✅ Practica en [CSS Diner](https://flukeout.github.io/)

---

## 💬 Preguntas Frecuentes

### ¿Cuándo usar :is() vs :where()?

- **:is()**: Cuando quieres mantener especificidad
- **:where()**: Para estilos base fáciles de sobrescribir

### ¿:has() funciona en todos los navegadores?

Sí, desde 2023 tiene soporte completo en todos los navegadores modernos.

### ¿Cuándo usar !important?

Solo para:

- Utilidades inmutables (`.hidden { display: none !important; }`)
- Sobrescribir CSS de terceros (último recurso)
- Hojas de estilo de accesibilidad

### ¿Qué especificidad debo usar?

La **mínima necesaria**. Prefiere classes sobre IDs, selectores simples sobre complejos.

---

**🎯 ¡Disfruta explorando el poder de los selectores CSS!**

_Esta semana es fundamental para escribir CSS profesional y mantenible._
