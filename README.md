## 📘 PRÁCTICA 8 – Mini-proyecto: “Mi sitio web moderno en HTML y CSS”

### 1. Objetivo de la práctica

Vas a crear **una página web completa** (una sola página) que combine:

* Estructura HTML5 semántica: `header`, `main`, `section`, `footer`…
* Dos menús:

  * Menú superior dentro del `header` (navegación principal).
  * Menú lateral con botón hamburguesa (☰), que se abre/cierra con un efecto deslizante.

* Varias secciones de contenido (tipo “web real”).
* Algo de maquetación con **Flexbox y/o Grid**.
* Un poco de dinamismo con pseudoclases como `:hover`.

Este mini-proyecto se hará **en casa y en clase durante unas 2 semanas**, y después tendrás **una prueba en el aula** donde te pediré modificaciones y/o preguntas sobre tu propia web.

---

### 2. Tema y estructura del proyecto

📌 **El tema lo eliges tú**: videojuegos, viajes, deportes, recetas, música, cine, anime, coches, etc.

La web debe ser una **single page** (`index.html`) con al menos:

1. **Cabecera global (`<header class="site-header">`)**

   * Debe incluir:

     * un título de la web (`<h1>`)
     * un menú superior (`<nav class="main-nav">`) con varios enlaces que apunten a secciones de la página.

2. **Botón hamburguesa + menú lateral (`<nav id="sideMenu">`)**

   * Un botón ☰ fijo en pantalla que abra/cierre el menú lateral.
   * El menú lateral debe contener enlaces de navegación (pueden ser los mismos del menú superior u otros).

3. **Contenido principal (`<main>`) con estas zonas mínimas:**

   * 🟦 **Sección Hero**
     Sección destacada al inicio (texto + imagen al menos).
     Ejemplo: “Bienvenidos a mi web de videojuegos retro”.

   * 🟨 **Sección con una tabla**
     Con información coherente con tu tema (por ejemplo: tabla de precios, comparativa de productos, clasificación de equipos, etc.).

   * 🟥 **Sección con un formulario**
     Ejemplo: formulario de contacto, formulario de suscripción, formulario de reserva, etc.
     Debe tener:

     * al menos 3 campos (`input`, `textarea`, `select`, etc.)
     * un botón de envío (`type="submit"`).

   * 🟩 **Sección galería**
     Una galería de imágenes (mínimo 6), organizada con **CSS** de forma visual (por ejemplo, usando Grid).

   * 🟪 **Alguna sección adicional**
     Por ejemplo: “Sobre mí”, “Servicios”, “Noticias”, “FAQ”… con texto, listas, etc.

4. **Pie de página (`<footer>`)**

   * Con texto de derechos/autor.
   * Un enlace que te lleve de vuelta al principio de la página.

---

### 3. Requisitos de maquetación y estilo (CSS)

Además del HTML, tu web debe cumplir estos requisitos de **CSS**:

1. **Reset CSS básico**
   Al principio de tu archivo `main.css` incluye este bloque (puedes añadir un comentario explicativo):

   ```css
   *, *::before, *::after {
     margin: 0;
     padding: 0;
     box-sizing: border-box;
   }
   ```

2. **Menú superior sticky**
   El header debe mantenerse arriba al hacer scroll (por ejemplo, usando `position: sticky; top: 0;`), de forma que el menú superior siempre esté visible.

3. **Botón hamburguesa fijo**
   El botón ☰ debe estar fijo en una esquina (normalmente arriba a la izquierda), usando `position: fixed;`.

4. **Menú lateral deslizante**
   El menú lateral (`#sideMenu`) debe:

   * estar oculto inicialmente (fuera de pantalla, por ejemplo con `left: -230px`)
   * entrar en pantalla cuando tenga una clase (`.active`) aplicada
   * con una transición suave (`transition: left 0.3s;`)

   El JavaScript para abrir/cerrar **te lo proporciono** (ver plantilla código).
   El diseño visual (colores, tamaños, tipografías…) lo decides tú.

5. **Uso de Flex y/o Grid en alguna parte**
   Deberás usar:

   * **Flexbox** al menos en un sitio (por ejemplo para el menú superior, o una fila de elementos).
   * **CSS Grid** al menos en un sitio (por ejemplo para la galería de imágenes, o para organizar la sección Hero en dos columnas texto/imagen).

6. **Pseudoclases y dinamismo básico**
   Debes usar como mínimo:

   * `:hover` en alguno de estos:

     * enlaces del menú
     * botones
     * tarjetas o imágenes de la galería

   Opcionalmente, puedes usar otras pseudoclases (`:focus`, `:active`, etc.) si quieres.

7. **Diseño propio**
   El diseño de la web (colores, tipografía, bordes, sombras, etc.) **no te lo damos hecho**:

   * Tú decides la paleta de colores.
   * Tú decides la tipografía (`font-family`).
   * Tú decides el tamaño de los encabezados, estilos de botones, etc.

---

### 4. Archivos y estructura recomendada

Estructura mínima del proyecto:

```text
proyecto/
│
├── index.html
├── styles/
│     └── main.css
└── img/
      └── (imágenes que tú elijas)
```

---

### 5. Plantilla base (mínima) para que no empieces de cero

Puedes partir de esta base y adaptarla.
⚠️ OJO: el CSS que te doy es **solo lo necesario** para que funcione el menú lateral y el botón fijo.
El resto del diseño lo completas tú.

#### `index.html` (esqueleto)

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- TODO: Cambia el título por algo relacionado con tu temática -->
  <title>Mi Mini-Proyecto Web</title>
  <link rel="stylesheet" href="">
</head>
<body>

  <!-- CABECERA GLOBAL DEL SITIO -->
  <header class="site-header">
    <!-- TODO: Cambia el título por algo relacionado con tu temática -->
    <h1>Mi Sitio Web</h1>

    <!-- TODO: Menú superior con enlaces a secciones de la misma página -->
    <nav class="main-nav">
        Inicio
        Galería
        Tabla
        Formulario
        Contacto
    </nav>
  </header>

  <!-- BOTÓN HAMBURGUESA FIJO PARA EL MENÚ LATERAL -->
  <button class="open-menu" aria-label="Abrir menú lateral">☰</button>

  <!-- MENÚ LATERAL DESLIZANTE -->
  <nav id="sideMenu" class="side-menu">
        Inicio
        Galería
        Tabla
        Formulario
        Contacto
  </nav>

  <!-- CONTENIDO PRINCIPAL -->
  <main>

    <!-- SECCIÓN HERO -->
    <section id="hero">
      <!-- TODO: Crear una sección destacada (texto + imagen) -->
      <h2>Sección Hero</h2>
      <p>Aquí puedes presentar el tema principal de tu web.</p>
      <!-- TODO: Añadir imagen relacionada -->
    </section>

    <!-- SECCIÓN GALERÍA -->
    <section>
      <h2>Galería de imágenes</h2>
      <!-- TODO: Usar CSS (preferiblemente Flex/Grid) para organizar las imágenes -->
      <!-- Mínimo 6 imágenes -->
    </section>

    <!-- SECCIÓN TABLA -->
    <section>
      <h2>Tabla de datos</h2>
      <!-- TODO: Crear una tabla coherente con tu temática -->
      <!-- Ejemplo: clasificación, precios, comparativa, etc. -->
    </section>

    <!-- SECCIÓN FORMULARIO -->
    <section>
      <h2>Formulario</h2>
      <!-- TODO: Crear un formulario con al menos 3 campos y un botón de envío -->
    </section>

    <!-- OTRAS SECCIONES QUE QUIERAS -->
    <!-- Por ejemplo: Sobre mí, Servicios, Noticias, etc. -->

    <!-- SECCIÓN CONTACTO / CIERRE -->
    <section>
      <h2>Contacto</h2>
      <!-- TODO: Texto, datos de contacto ficticios, redes, etc. -->
    </section>

  </main>

  <!-- PIE DE PÁGINA -->
  <footer class="site-footer">
    <p><a href="#hero">&copy; 2025 — 1º DAM, IES Saladillo</a></p>
  </footer>

  <!-- JavaScript mínimo para abrir/cerrar el menú lateral -->
  <script>
    const sideMenu = document.getElementById("sideMenu");
    const toggleBtn = document.querySelector(".open-menu");

    toggleBtn.addEventListener("click", () => {
      sideMenu.classList.toggle("active");
      toggleBtn.classList.toggle("active");

      toggleBtn.textContent =
        sideMenu.classList.contains("active") ? "✖" : "☰";
    });
  </script>

</body>
</html>
```

---

#### `styles/main.css` (solo lo imprescindible del menú y algo base)

El reset mínimo no se puede eliminar de tu fichero CSS.

```css
/* ===== RESET CSS básico ===== */
*, *::before, *::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* ===== ESTILOS BASE ===== */
body {
  font-family: system-ui, -apple-system, "Segoe UI", sans-serif;
}

/* TODO: Alinear el contenido de main, poner colores de fondo, etc. */
main {
  /* Ejemplo: */
  /* width: min(1100px, 90%); */
  /* margin: 20px auto; */
}

/* ===== CABECERA Y MENÚ SUPERIOR ===== */
.site-header {
  position: sticky;
  top: 0;
  z-index: 10;
  /* TODO: Añade color de fondo, color de texto, padding, etc. */
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.site-header h1 {
  /* TODO: Estilo del título (tamaño, margen, etc.) */
}

.main-nav ul {
  list-style: none;
  display: flex;
  gap: 10px;
}

.main-nav a {
  /* TODO: Estilo de enlaces del menú superior (color, padding, :hover, etc.) */
}

/* ===== BOTÓN HAMBURGUESA PARA GESTIONAR EL MENÚ LATERAL ===== */
.open-menu {
  position: fixed;
  top: 14px;
  left: 14px;
  z-index: 20;
  font-size: 26px;
  /* TODO: Colores, borde, padding, etc. */
  cursor: pointer;
  transition: transform 0.3s ease, background-color 0.3s ease;
}

/* Efecto visual cuando el menú está abierto */
.open-menu.active {
  /* TODO: Cambia color de fondo, rota un poco el icono, etc. */
}

/* ===== MENÚ LATERAL DESLIZANTE ===== */
.side-menu {
  position: fixed;
  top: 0;
  left: -230px;            /* oculto inicialmente */
  width: 230px;
  height: 100%;
  /* TODO: color de fondo, color de texto… */
  padding-top: 60px;
  transition: left 0.3s ease;
  z-index: 15;
}

.side-menu.active {
  left: 0;                 /* aparece cuando tiene la clase "active" */
}

.side-menu ul {
  list-style: none;
  padding: 0;
}

.side-menu a {
  display: block;
  padding: 12px 20px;
  /* TODO: color de texto, quitar subrayado, etc. */
}

/* TODO: Añade :hover para los enlaces del menú lateral */
.side-menu a:hover {
}

/* ===== PIE DE PÁGINA ===== */
.site-footer {
  /* TODO: estilo del footer (color de fondo, texto centrado, padding…) */
}

.site-footer a {
  /* TODO: estilo del enlace del footer y :visited si lo deseas */
}
```

---
