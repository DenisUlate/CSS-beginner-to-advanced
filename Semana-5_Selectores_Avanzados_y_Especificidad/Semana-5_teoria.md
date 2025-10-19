# 📅 SEMANA 5: Selectores Avanzados & Especificidad

**Fecha:** \_\_\_ | **Estado:** ⬜ No iniciado | ⬜ En progreso | ✅ Completado

---

## 🎯 Objetivos de Aprendizaje

- ✅ Dominar todos los tipos de selectores CSS
- ✅ Entender especificidad y resolución de conflictos
- ✅ Usar pseudo-clases y pseudo-elementos modernos
- ✅ Optimizar selectores para mejor mantenibilidad

---

## 📖 1. SELECTORES DE AGRUPACIÓN

### Teoría

Los selectores de agrupación permiten aplicar los mismos estilos a múltiples elementos usando comas. Evitan duplicación de código y facilitan mantenimiento.

### Concepto Clave

**Una regla, múltiples objetivos** → Aplica estilos a varios selectores simultáneamente.

### 🛠️ Ejemplo Básico

```css
/* ❌ Código repetitivo */
h1 {
	color: #2563eb;
	font-weight: 700;
}
h2 {
	color: #2563eb;
	font-weight: 700;
}
h3 {
	color: #2563eb;
	font-weight: 700;
}

/* ✅ Agrupación eficiente */
h1,
h2,
h3 {
	color: #2563eb;
	font-weight: 700;
}
```

### ✅ Mejores Prácticas

- Una línea por selector para mejor legibilidad
- Agrupa solo selectores con estilos realmente compartidos
- Usa variables CSS para valores repetidos

---

## 📖 2. COMBINADORES CSS

### 2.1 Descendant Combinator (Espacio)

Selecciona elementos que son **descendientes** (en cualquier nivel) de un elemento padre.

```css
/* Selecciona todos los <p> dentro de <article>, sin importar cuán profundos */
article p {
	line-height: 1.6;
}
```

**Uso:** Aplicar estilos generales a elementos anidados.

---

### 2.2 Child Combinator (>)

Selecciona elementos que son **hijos directos** del elemento padre.

```css
/* Solo los <li> que son hijos directos de <ul> */
ul > li {
	list-style: none;
}

/* No afecta a <li> dentro de <ul> anidados */
```

**Uso:** Control preciso, evita afectar elementos anidados profundamente.

---

### 2.3 Adjacent Sibling Combinator (+)

Selecciona el elemento **inmediatamente siguiente** al elemento especificado.

```css
/* Solo el <p> que está justo después de <h2> */
h2 + p {
	font-size: 1.125rem; /* Párrafo de introducción más grande */
	color: #64748b;
}
```

**Caso de Uso Real:** Estilizar el primer párrafo después de un título.

---

### 2.4 General Sibling Combinator (~)

Selecciona **todos los elementos hermanos** que siguen al elemento especificado.

```css
/* Todos los <p> que vienen después de <h2> */
h2 ~ p {
	margin-block-start: 1rem;
}
```

**Diferencia con `+`:** Este afecta a TODOS los hermanos siguientes, no solo al inmediato.

---

## 📖 3. SELECTORES DE ATRIBUTO

### Teoría

Permiten seleccionar elementos basados en sus atributos HTML. Muy útiles para formularios, links y elementos dinámicos.

### 3.1 Existencia de Atributo

```css
/* Todos los elementos con atributo "required" */
input[required] {
	border-left: 3px solid #ef4444;
}

/* Todos los links con "target" */
a[target] {
	background-image: url("external-link-icon.svg");
}
```

---

### 3.2 Valor Exacto [attr="value"]

```css
/* Solo inputs de tipo "email" */
input[type="email"] {
	background-image: url("email-icon.svg");
}

/* Links a sitio específico */
a[href="https://github.com"]
{
	color: #333;
}
```

---

### 3.3 Comienza con [attr^="value"]

```css
/* Links externos (comienzan con "https://") */
a[href^="https://"]
{
	padding-inline-end: 1.25rem;
}

/* Links a archivos PDF */
a[href^="downloads/"]::after {
	content: " 📄";
}
```

**Caso de Uso:** Iconos automáticos para tipos de links.

---

### 3.4 Termina con [attr$="value"]

```css
/* Links a PDFs */
a[href$=".pdf"]::after {
	content: " (PDF)";
	font-size: 0.875rem;
	color: #dc2626;
}

/* Imágenes PNG */
img[src$=".png"] {
	image-rendering: crisp-edges;
}
```

---

### 3.5 Contiene [attr*="value"]

```css
/* Links que contienen "youtube" en cualquier parte */
a[href*="youtube"] {
	color: #ff0000;
}

/* Clases que contienen "btn" */
[class*="btn"] {
	padding: 0.5rem 1rem;
	border-radius: 0.375rem;
}
```

**⚠️ Precaución:** Puede ser más lento, úsalo conscientemente.

---

## 📖 4. PSEUDO-CLASES ESENCIALES

### 4.1 Estados de Interacción

```css
/* Hover: cuando el mouse pasa sobre el elemento */
button:hover {
	background-color: #1d4ed8;
	transform: translateY(-2px);
}

/* Focus: cuando el elemento recibe foco (teclado/click) */
input:focus {
	outline: 2px solid #3b82f6;
	outline-offset: 2px;
}

/* Active: mientras se presiona el elemento */
button:active {
	transform: scale(0.98);
}

/* Visited: links ya visitados */
a:visited {
	color: #7c3aed;
}
```

**✅ Accesibilidad:** SIEMPRE incluye estilos `:focus` para navegación por teclado.

---

### 4.2 Pseudo-clases Estructurales

```css
/* Primer hijo */
li:first-child {
	margin-block-start: 0;
}

/* Último hijo */
li:last-child {
	border-block-end: none;
}

/* Elementos pares (2, 4, 6...) */
tr:nth-child(even) {
	background-color: #f8fafc;
}

/* Elementos impares (1, 3, 5...) */
tr:nth-child(odd) {
	background-color: white;
}

/* Cada 3er elemento */
.card:nth-child(3n) {
	margin-inline-end: 0;
}

/* Primer elemento de su tipo */
p:first-of-type {
	font-size: 1.25rem; /* Intro más grande */
}
```

---

### 4.3 nth-child() Avanzado

```css
/* Primeros 3 elementos */
li:nth-child(-n + 3) {
	font-weight: 700;
}

/* Todos excepto los primeros 2 */
li:nth-child(n + 3) {
	opacity: 0.7;
}

/* Del 5to al 10mo */
li:nth-child(n + 5):nth-child(-n + 10) {
	background: #fef3c7;
}
```

---

## 🚀 5. PSEUDO-CLASES MODERNAS (2025)

### 5.1 :not() - Negación

```css
/* Todos los elementos EXCEPTO el último */
.item:not(:last-child) {
	margin-block-end: 1rem;
}

/* Inputs excepto checkboxes y radios */
input:not([type="checkbox"]):not([type="radio"]) {
	width: 100%;
}

/* ⚠️ Evita negaciones complejas, afecta legibilidad */
```

---

### 5.2 :is() - Simplificación

```css
/* ❌ Repetitivo */
header h1,
header h2,
header h3 {
	color: white;
}

main h1,
main h2,
main h3 {
	color: white;
}

/* ✅ Con :is() */
:is(header, main) :is(h1, h2, h3) {
	color: white;
}
```

**Ventaja:** Reduce duplicación, más fácil de mantener.

---

### 5.3 :where() - Especificidad Cero

```css
/* Especificidad: (0,0,0) - Fácil de sobrescribir */
:where(article, section) p {
	color: #475569;
}

/* Comparación con :is() */
:is(article, section) p {
	/* Especificidad: (0,1,1) */
}
```

**Uso:** Estilos base que queremos sobrescribir fácilmente.

---

### 5.4 :has() - Selector Padre (¡REVOLUCIONARIO! 🔥)

```css
/* Card que CONTIENE una imagen */
.card:has(img) {
	display: grid;
	grid-template-columns: 200px 1fr;
}

/* Formulario con errores */
form:has(input:invalid) {
	border: 2px solid #ef4444;
}

/* Artículo sin imágenes */
article:not(:has(img)) {
	max-inline-size: 65ch;
}

/* Lista que contiene enlaces */
li:has(> a) {
	padding: 0; /* El padding lo tiene el <a> */
}
```

**💡 Game Changer:** Por primera vez podemos seleccionar padres basados en sus hijos.

---

## 📖 6. PSEUDO-ELEMENTOS

### Teoría

Los pseudo-elementos crean elementos "virtuales" que no existen en el HTML. Se usan con `::` (doble dos puntos).

### 6.1 ::before y ::after

```css
/* Añadir contenido decorativo */
.quote::before {
	content: "" "; /* Comilla de apertura */
	font-size: 3rem;
	color: #cbd5e1;
}

.quote::after {
	content: " "";
	font-size: 3rem;
	color: #cbd5e1;
}

/* Iconos automáticos */
.external-link::after {
	content: " ↗";
	font-size: 0.875rem;
}

/* Decoración visual */
.btn::before {
	content: "";
	position: absolute;
	inset: 0;
	background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1));
	opacity: 0;
	transition: opacity 0.3s;
}

.btn:hover::before {
	opacity: 1;
}
```

**⚠️ Importante:** `content` es OBLIGATORIO, aunque esté vacío.

---

### 6.2 ::first-letter

```css
/* Drop cap (letra capital) */
.article-intro::first-letter {
	font-size: 3.5rem;
	font-weight: 700;
	float: left;
	line-height: 1;
	margin-inline-end: 0.5rem;
	color: #2563eb;
}
```

**Caso de Uso:** Artículos, revistas digitales, blogs editoriales.

---

### 6.3 ::first-line

```css
/* Primera línea destacada */
p::first-line {
	font-variant: small-caps;
	font-weight: 600;
	letter-spacing: 0.05em;
}
```

---

### 6.4 ::selection

```css
/* Personalizar selección de texto */
::selection {
	background-color: #fbbf24;
	color: #78350f;
}

/* Por elemento específico */
code::selection {
	background-color: #1e293b;
	color: #fbbf24;
}
```

---

### 6.5 ::marker

```css
/* Personalizar viñetas de listas */
li::marker {
	content: "▸ ";
	color: #3b82f6;
	font-size: 1.25rem;
}

/* Numeración personalizada */
ol li::marker {
	content: counter(list-item) ". ";
	font-weight: 700;
	color: #dc2626;
}
```

---

## 📊 7. ESPECIFICIDAD CSS

### 📖 Teoría

La especificidad determina qué regla CSS se aplica cuando hay conflictos. Es un sistema de puntuación que CSS usa para decidir el "ganador".

### 💡 Concepto Clave

**A mayor especificidad, mayor prioridad** → El navegador aplica la regla más específica.

---

### 🎯 Cálculo de Especificidad

Se representa como: **(a, b, c, d)**

| Componente | Valor   | Ejemplo                    |
| ---------- | ------- | -------------------------- |
| **a**      | Inline  | `style="color: red"`       |
| **b**      | IDs     | `#header`                  |
| **c**      | Classes | `.btn`, `[type]`, `:hover` |
| **d**      | Tags    | `div`, `p`, `::before`     |

---

### 📈 Ejemplos de Cálculo

```css
/* (0, 0, 0, 1) - Solo elemento */
p {
	color: blue;
}

/* (0, 0, 1, 1) - Clase + elemento */
.intro p {
	color: green;
}

/* (0, 1, 0, 1) - ID + elemento */
#main p {
	color: red; /* ✅ GANA */
}

/* (0, 0, 2, 2) - 2 clases + 2 elementos */
article.featured p.intro {
	color: purple;
}

/* (0, 1, 1, 1) - ID + clase + elemento */
#main .intro p {
	color: orange; /* ✅ GANA sobre el anterior */
}

/* (1, 0, 0, 0) - Inline style */
<p style="color: yellow;">
	/* ✅ GANA sobre todos los anteriores */
</p>;
```

---

### 🔢 Reglas de Comparación

1. Se compara de **izquierda a derecha**: (a → b → c → d)
2. Si `a` es mayor, gana (sin importar b, c, d)
3. Si `a` es igual, se compara `b`
4. Y así sucesivamente...

```css
/* (0, 1, 0, 0) = 100 puntos */
#header {
}

/* (0, 0, 10, 0) = 10 puntos */
.a .b .c .d .e .f .g .h .i .j {
} /* ❌ PIERDE */

/* Un ID siempre gana contra cualquier cantidad de clases */
```

---

### ⚠️ !important - El Último Recurso

```css
/* Especificidad: INFINITA (casi) */
p {
	color: red !important; /* ✅ GANA sobre TODO */
}

#main .intro p {
	color: blue; /* ❌ PIERDE */
}
```

**Cuándo EVITARLO:**

- ❌ Para "arreglar" problemas de especificidad
- ❌ En proyectos mantenibles
- ❌ En frameworks/componentes reutilizables

**Cuándo USARLO:**

- ✅ Utilidades inmutables (`.hidden { display: none !important; }`)
- ✅ Sobrescribir CSS de terceros (último recurso)
- ✅ Hojas de estilo de usuario (accesibilidad)

---

### ✅ Mejores Prácticas de Especificidad

```css
/* ❌ MAL: Especificidad alta innecesaria */
#header nav ul li a.active {
	color: red;
}

/* ✅ BIEN: Solo lo necesario */
.nav-link.active {
	color: red;
}

/* ❌ MAL: Dependencia de estructura HTML */
div.container div.wrapper div.content p {
	color: blue;
}

/* ✅ BIEN: Clase directa */
.content-text {
	color: blue;
}

/* ❌ MAL: IDs en CSS (alta especificidad) */
#sidebar {
	width: 300px;
}

/* ✅ BIEN: Clases reutilizables */
.sidebar {
	width: 300px;
}
```

---

### 🎯 Estrategias para Manejar Especificidad

#### 1. **Usa Clases, no IDs**

```css
/* ❌ */
#header {
}
/* ✅ */
.header {
}
```

#### 2. **Evita Selectores Profundos**

```css
/* ❌ */
.header nav ul li a {
}
/* ✅ */
.nav-link {
}
```

#### 3. **Usa :where() para Especificidad Cero**

```css
/* Estilos base fáciles de sobrescribir */
:where(.btn) {
	padding: 0.5rem 1rem;
}

/* Fácil de sobrescribir sin !important */
.btn-large {
	padding: 1rem 2rem;
}
```

#### 4. **Estructura en Capas** (2025 - @layer)

```css
@layer base, components, utilities;

@layer base {
	p {
		color: black;
	} /* Especificidad baja */
}

@layer components {
	.card p {
		color: gray;
	} /* Gana sobre base */
}

@layer utilities {
	.text-red {
		color: red;
	} /* Gana sobre components */
}
```

---

## 🎨 Caso de Uso Completo

### Componente de Card con Selectores Avanzados

```css
/* Card base */
.card {
	background: white;
	border-radius: 0.5rem;
	box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

/* Card con imagen */
.card:has(img) {
	display: grid;
	grid-template-columns: 200px 1fr;
}

/* Primera card destacada */
.card:first-of-type {
	border: 2px solid #3b82f6;
}

/* Cards alternas con fondo */
.card:nth-child(even) {
	background: #f8fafc;
}

/* Título de card con icono */
.card h3::before {
	content: "📌 ";
}

/* Links dentro de card */
.card a:not(.btn) {
	color: #2563eb;
	text-decoration: underline;
}

/* Links externos en card */
.card a[href^="https://"]::after
{
	content: " ↗";
}

/* Card en hover */
.card:hover {
	box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
	transform: translateY(-4px);
}

/* Botón dentro de card */
.card .btn:last-child {
	margin-block-start: auto; /* Se pega al final */
}
```

---

## 🚀 Ejercicios Prácticos

### Nivel 1: Básico

1. Crea estilos para una tabla con filas alternas (zebra striping)
2. Estiliza todos los enlaces externos con un icono
3. Aplica estilos diferentes al primer y último elemento de una lista

### Nivel 2: Intermedio

4. Crea un menú de navegación con estilos hover y active
5. Implementa un formulario con indicadores visuales de campos requeridos
6. Usa ::before y ::after para crear flechas decorativas

### Nivel 3: Avanzado

7. Implementa un grid de cards que cambia layout cuando contiene imagen
8. Crea un sistema de tabs usando :has() para mostrar/ocultar contenido
9. Desarrolla un componente que se auto-adapta según su contenido

---

## 📚 Recursos Adicionales

- **MDN Selectors Reference:** [https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)
- **Specificity Calculator:** [https://specificity.keegan.st/](https://specificity.keegan.st/)
- **:has() Support:** Can I Use - :has()

---

## ✅ Checklist de Dominio

- [ ] Puedo explicar la diferencia entre `>` y espacio
- [ ] Sé usar selectores de atributo para casos prácticos
- [ ] Entiendo cómo calcular especificidad
- [ ] Puedo usar :nth-child() con fórmulas
- [ ] Sé cuándo usar :is() vs :where()
- [ ] Comprendo el poder de :has()
- [ ] Puedo crear contenido decorativo con ::before/::after
- [ ] Evito !important y alta especificidad innecesaria

---

**🎯 Próximo Paso:** Aplica estos selectores en el proyecto de la semana para consolidar tu aprendizaje.

**💡 Recuerda:** La clave es la especificidad baja y los selectores mantenibles. Menos es más.
