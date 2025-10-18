# 📅 SEMANA 4: Colores, Fondos & Efectos Visuales

## 📖 Sistemas de Color en CSS

### Teoría

CSS ofrece múltiples formas de definir colores, desde nombres simples hasta sistemas avanzados con control de transparencia y luminosidad. En 2025, los métodos modernos priorizan la precisión perceptual y la flexibilidad para manipular colores dinámicamente.

### 💡 Concepto Clave

Los colores se pueden expresar de varias formas, pero los sistemas modernos (HSL, OKLCH, color-mix) ofrecen mayor control y legibilidad que los métodos antiguos (hex, rgb).

---

### 1️⃣ **Named Colors** (Colores con Nombre)

```css
/* 140+ colores predefinidos */
.element {
	color: red;
	background: dodgerblue;
	border-color: tomato;
}
```

**Cuándo usar:** Prototipado rápido, ejemplos simples  
**Limitación:** Solo 140 colores, no permiten transparencia

---

### 2️⃣ **Hexadecimal (Hex)**

```css
/* #RRGGBB o #RGB */
.element {
	color: #ff5733; /* 6 dígitos */
	background: #f57; /* 3 dígitos (shorthand) */
	border-color: #ff573380; /* 8 dígitos con alpha */
}
```

**Pros:** Compacto, muy usado  
**Contras:** No intuitivo, difícil de ajustar

---

### 3️⃣ **RGB y RGBA**

```css
/* rgb(red, green, blue) */
.element {
	color: rgb(255, 87, 51); /* Sin transparencia */
	background: rgba(255, 87, 51, 0.5); /* Con transparencia */

	/* Sintaxis moderna (2025) */
	color: rgb(255 87 51); /* Sin comas */
	background: rgb(255 87 51 / 0.5); /* Slash para alpha */
}
```

**Pros:** Valores 0-255 intuitivos  
**Contras:** Difícil ajustar tonos manualmente

---

### 4️⃣ **HSL y HSLA** ⭐ (Recomendado)

```css
/* hsl(tono, saturación, luminosidad) */
.primary {
	/* H: 0-360° | S: 0-100% | L: 0-100% */
	color: hsl(14, 100%, 60%); /* Naranja vibrante */
	background: hsla(14, 100%, 60%, 0.3); /* Con transparencia */

	/* Sintaxis moderna */
	color: hsl(14 100% 60%);
	background: hsl(14 100% 60% / 0.3);
}

/* Fácil crear variaciones */
.primary-light {
	color: hsl(14 100% 80%);
} /* Más claro */
.primary-dark {
	color: hsl(14 100% 40%);
} /* Más oscuro */
```

**Pros:** Intuitivo, fácil ajustar tono/brillo  
**Recomendado para:** Variables CSS, temas

---

### 5️⃣ **color-mix()** 🆕 (2025)

```css
/* Mezcla dos colores dinámicamente */
.button {
	--primary: hsl(200 80% 50%);

	background: var(--primary);

	/* Hover: mezcla con blanco 20% */
	&:hover {
		background: color-mix(in oklch, var(--primary), white 20%);
	}

	/* Active: mezcla con negro 30% */
	&:active {
		background: color-mix(in oklch, var(--primary), black 30%);
	}
}
```

**Cuándo usar:** Hover effects, temas dinámicos, variaciones automáticas  
**Ventaja:** No necesitas calcular colores manualmente

---

## 🎨 Fondos en CSS

### 1️⃣ **background-color**

```css
.section {
	background-color: hsl(200 50% 95%);
}
```

---

### 2️⃣ **background-image**

```css
.hero {
	background-image: url("hero.jpg");
}
```

---

### 3️⃣ **background-size**

```css
.banner {
	background-image: url("pattern.png");
	background-size: cover; /* Cubre todo el contenedor */
	/* background-size: contain; */ /* Contiene imagen completa */
	/* background-size: 50%;     */ /* Tamaño específico */
}
```

**Valores clave:**

- `cover`: Cubre todo (puede recortar)
- `contain`: Muestra imagen completa (puede dejar espacio)
- `100px 200px`: Ancho y alto específicos

---

### 4️⃣ **background-position**

```css
.card {
	background-image: url("icon.svg");
	background-position: center; /* Centrado */
	/* background-position: top right; */ /* Esquina superior derecha */
	/* background-position: 20px 40px; */ /* Posición exacta */
}
```

---

### 5️⃣ **background-repeat**

```css
.pattern {
	background-image: url("tile.png");
	background-repeat: no-repeat; /* Sin repetir */
	/* background-repeat: repeat-x; */ /* Solo horizontal */
	/* background-repeat: repeat-y; */ /* Solo vertical */
}
```

---

### 6️⃣ **background-attachment**

```css
.parallax {
	background-image: url("mountain.jpg");
	background-attachment: fixed; /* Efecto parallax */
	/* background-attachment: scroll; */ /* Se mueve con scroll (default) */
}
```

---

### 7️⃣ **Multiple Backgrounds** ⭐

```css
.complex-bg {
	background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url("hero.jpg");
	background-size: cover, cover;
	background-position: center, center;
}

/* Ejemplo: Pattern + Gradiente + Color */
.decorative {
	background: url("dots.png") repeat, linear-gradient(135deg, #667eea 0%, #764ba2 100%), #667eea;
}
```

**Orden:** Primero la imagen de arriba, última la del fondo

---

## 🌈 Gradientes

### 1️⃣ **linear-gradient()** (Gradiente Lineal)

```css
/* Básico */
.gradient-basic {
	background: linear-gradient(to right, #ff6b6b, #4ecdc4);
}

/* Con ángulo */
.gradient-angle {
	background: linear-gradient(45deg, #667eea, #764ba2);
}

/* Múltiples colores */
.gradient-multi {
	background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
}

/* Color stops precisos */
.gradient-stops {
	background: linear-gradient(to bottom, #1e3c72 0%, #2a5298 30%, #7e22ce 70%, #c026d3 100%);
}
```

**Sintaxis:** `linear-gradient(dirección, color1, color2, ...)`  
**Direcciones:** `to right`, `to bottom`, `45deg`, `135deg`

---

### 2️⃣ **radial-gradient()** (Gradiente Radial)

```css
/* Básico (desde el centro) */
.radial-basic {
	background: radial-gradient(circle, #ff6b6b, #4ecdc4);
}

/* Elipse */
.radial-ellipse {
	background: radial-gradient(ellipse, #667eea, #764ba2);
}

/* Con posición */
.radial-position {
	background: radial-gradient(circle at top right, #ff6b6b, #4ecdc4);
}

/* Tamaño específico */
.radial-size {
	background: radial-gradient(circle 200px at center, rgba(255, 107, 107, 0.8), transparent);
}
```

**Cuándo usar:** Efectos de spotlight, halos, botones circulares

---

### 3️⃣ **conic-gradient()** 🆕 (2025) (Gradiente Cónico)

```css
/* Básico */
.conic-basic {
	background: conic-gradient(#ff6b6b, #4ecdc4, #ff6b6b);
}

/* Pie chart effect */
.pie-chart {
	background: conic-gradient(from 0deg, #ff6b6b 0deg 120deg, #4ecdc4 120deg 240deg, #feca57 240deg 360deg);
	border-radius: 50%;
}

/* Loading spinner */
.spinner {
	background: conic-gradient(from 0deg, transparent 0deg, transparent 270deg, #667eea 270deg, #667eea 360deg);
	border-radius: 50%;
	animation: spin 1s linear infinite;
}

@keyframes spin {
	to {
		transform: rotate(360deg);
	}
}
```

**Cuándo usar:** Pie charts, color wheels, loaders circulares

---

## 💧 Opacity y Transparencia

### 1️⃣ **opacity** (Opacidad del Elemento Completo)

```css
.card {
	opacity: 0.8; /* 0 (invisible) a 1 (opaco) */
}

/* Efecto hover */
.image {
	opacity: 0.7;
	transition: opacity 0.3s;
}

.image:hover {
	opacity: 1;
}
```

**⚠️ Limitación:** Afecta TODO el elemento (contenido, bordes, texto)

---

### 2️⃣ **Transparencia en Colores** ⭐ (Recomendado)

```css
/* Mejor control: solo afecta el color específico */
.card {
	background: rgba(255, 255, 255, 0.9); /* Fondo semi-transparente */
	color: rgb(0 0 0); /* Texto opaco */
	border: 1px solid hsla(200, 50%, 50%, 0.5); /* Borde semi-transparente */
}
```

**Ventaja:** Control independiente de cada propiedad

---

### 3️⃣ **backdrop-filter** 🆕 (Efecto de Desenfoque/Filtro)

```css
/* Glass morphism effect */
.glass-card {
	background: rgba(255, 255, 255, 0.1);
	backdrop-filter: blur(10px);
	border: 1px solid rgba(255, 255, 255, 0.2);
	border-radius: 16px;
	padding: 2rem;
}

/* Variaciones */
.backdrop-brightness {
	backdrop-filter: brightness(1.5); /* Más brillante */
}

.backdrop-contrast {
	backdrop-filter: contrast(0.8); /* Menos contraste */
}

/* Combinado */
.glass-advanced {
	backdrop-filter: blur(20px) brightness(1.2) saturate(1.5);
}
```

**Cuándo usar:** Glass morphism, overlays modernos, modals

---

## 🛠️ Ejemplos Prácticos Completos

### Ejemplo 1: Card con Gradiente Moderno

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Card con Gradiente</title>
		<style>
			body {
				min-height: 100vh;
				display: grid;
				place-items: center;
				background: hsl(220 15% 15%);
				font-family: system-ui;
			}

			.card {
				width: 300px;
				padding: 2rem;
				background: linear-gradient(135deg, hsl(280 80% 60%) 0%, hsl(320 80% 55%) 100%);
				border-radius: 20px;
				color: white;
				box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
				transition: transform 0.3s;
			}

			.card:hover {
				transform: translateY(-10px);
			}

			.card h2 {
				margin: 0 0 1rem 0;
			}
		</style>
	</head>
	<body>
		<div class="card">
			<h2>Card Moderno</h2>
			<p>Gradiente lineal con efecto hover</p>
		</div>
	</body>
</html>
```

---

### Ejemplo 2: Glass Morphism Card

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Glass Morphism</title>
		<style>
			body {
				min-height: 100vh;
				display: grid;
				place-items: center;
				background: linear-gradient(135deg, #667eea 0%, #764ba2 100%),
					url("https://images.unsplash.com/photo-1557683316-973673baf926");
				background-size: cover;
				background-blend-mode: overlay;
			}

			.glass-card {
				width: 350px;
				padding: 2rem;
				background: rgba(255, 255, 255, 0.1);
				backdrop-filter: blur(10px) saturate(1.5);
				border: 1px solid rgba(255, 255, 255, 0.2);
				border-radius: 20px;
				color: white;
				box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
			}

			.glass-card h2 {
				margin: 0 0 1rem 0;
				font-size: 1.5rem;
			}
		</style>
	</head>
	<body>
		<div class="glass-card">
			<h2>Glass Morphism</h2>
			<p>Efecto de cristal esmerilado con backdrop-filter</p>
		</div>
	</body>
</html>
```

---

### Ejemplo 3: Hero con Multiple Backgrounds

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Hero Section</title>
		<style>
			.hero {
				height: 100vh;
				display: grid;
				place-items: center;
				background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.4)),
					url("https://images.unsplash.com/photo-1517694712202-14dd9538aa97");
				background-size: cover;
				background-position: center;
				background-attachment: fixed; /* Parallax */
				color: white;
				text-align: center;
			}

			.hero h1 {
				font-size: clamp(2rem, 5vw, 4rem);
				margin: 0;
			}

			.hero p {
				font-size: clamp(1rem, 2vw, 1.5rem);
				opacity: 0.9;
			}
		</style>
	</head>
	<body>
		<section class="hero">
			<div>
				<h1>Bienvenido</h1>
				<p>Hero con overlay y parallax</p>
			</div>
		</section>
	</body>
</html>
```

---

## 🔄 Comparación: Métodos Antiguos vs Modernos

| Concepto             | Método Antiguo ❌        | Método Moderno 2025 ✅                        |
| -------------------- | ------------------------ | --------------------------------------------- |
| **Colores**          | `#ff5733`                | `hsl(14 100% 60%)`                            |
| **Transparencia**    | `opacity: 0.5` en todo   | `background: rgba(...)` específico            |
| **Variaciones**      | Calcular hex manualmente | `color-mix(in oklch, ...)`                    |
| **Blur backgrounds** | Imágenes pre-difuminadas | `backdrop-filter: blur(10px)`                 |
| **Gradientes**       | Imágenes PNG             | `linear-gradient()`, `radial-gradient()`      |
| **Color stops**      | Sin control              | `linear-gradient(...color 0%, ...color 100%)` |

---

## ✅ Mejores Prácticas 2025

### 1. **Usa HSL para colores principales**

```css
:root {
	--primary: hsl(200 80% 50%);
	--primary-light: hsl(200 80% 70%);
	--primary-dark: hsl(200 80% 30%);
}
```

### 2. **color-mix() para variaciones automáticas**

```css
.button {
	background: var(--primary);
}

.button:hover {
	background: color-mix(in oklch, var(--primary), white 15%);
}
```

### 3. **backdrop-filter para efectos glass**

```css
.modal {
	background: rgba(255, 255, 255, 0.1);
	backdrop-filter: blur(10px);
}
```

### 4. **Gradientes en lugar de imágenes**

```css
/* Más rápido, escalable, sin HTTP request */
.hero {
	background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

### 5. **Transparencia específica, no opacity global**

```css
/* ❌ Evitar */
.card {
	opacity: 0.9; /* Afecta TODO */
}

/* ✅ Mejor */
.card {
	background: rgba(255, 255, 255, 0.9); /* Solo el fondo */
	color: rgb(0 0 0); /* Texto opaco */
}
```

---

## 📌 Casos de Uso Reales

### 🎯 Landing Page Hero

- Multiple backgrounds (overlay + imagen)
- `background-attachment: fixed` para parallax
- Gradiente como overlay

### 🎯 Dashboard Cards

- `backdrop-filter` para glass effect
- HSL para colores de estado (success, warning, error)
- `color-mix()` para hover states

### 🎯 E-commerce Product Cards

- `background-size: cover` para imágenes
- Gradientes sutiles para depth
- Transparencia en overlays de precio

### 🎯 Loading Spinners

- `conic-gradient()` para spinners circulares
- Animaciones con `@keyframes`

---

## 🎓 Ejercicio Práctico Sugerido

Crea una **Card de Producto** que incluya:

1. Imagen de fondo con `background-size: cover`
2. Overlay con gradiente lineal
3. Glass card con `backdrop-filter`
4. Botón con `color-mix()` en hover
5. Efecto parallax en el hero

---

Ahora voy a guardar toda esta teoría en un archivo markdown en la carpeta de la Semana 4:
