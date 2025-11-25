# Mini-Guía de apoyo para entender el código

<br>

## 1. Pseudoclases y Pseudoelementos

En CSS podemos modificar la apariencia de un elemento **dependiendo de su estado** o **añadiendo contenido especial**. Para eso existen **pseudoclases** y **pseudoelementos**.

### 🔹 Pseudoclases (`:`)

Una pseudoclase se activa cuando un elemento está en una **situación concreta**.

Ejemplos habituales:

| Pseudoclase | Cuándo se activa                    | Para qué sirve                         |
| ----------- | ----------------------------------- | -------------------------------------- |
| `:hover`    | cuando el ratón pasa por encima     | crear efectos al pasar el cursor       |
| `:visited`  | cuando un enlace ya fue visitado    | cambiar el color después de hacer clic |
| `:active`   | mientras se pulsa un botón o enlace | dar efecto de presión                  |
| `:focus`    | cuando un campo recibe el cursor    | resaltar inputs de formularios         |

Ejemplo:

```css
a:hover {
  color: red;
}
```

Significa:

> cuando el ratón esté sobre un enlace, cambia su color a rojo.

---

### 🔹 Pseudoelementos (`::`)

Los pseudoelementos permiten **crear partes extra** dentro de un elemento sin añadir HTML.

Los más usados son:

| Pseudoelemento | Qué representa                         |
| -------------- | -------------------------------------- |
| `::before`     | contenido añadido antes del elemento   |
| `::after`      | contenido añadido después del elemento |

Ejemplo:

```css
button::after {
  content: " →";
}
```

Esto añade una flecha al final del botón **sin modificar el HTML**.

---

### 🔹 ¿Por qué aparecen en el *reset* (`*::before`, `*::after`)?

En el reset usamos:

```css
*, *::before, *::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

Este código consigue que:

* **todos los elementos** empiecen sin márgenes ni rellenos
* también lo hagan los pseudoelementos, aunque todavía no los estemos usando
* todo mida mejor gracias a `box-sizing: border-box`

Resultado práctico para vosotros:

> La página empieza “limpia” y se ve igual en todos los navegadores.

---

## 2. Explicación de algunas propiedades CSS nuevas

Estas propiedades aparecen en el CSS del mini-proyecto y es importante entender para qué sirven.

---

### 🔹 `position`

Controla **cómo se coloca un elemento** en la página.

Valores importantes aquí:

* `fixed`: el elemento queda **fijo en la pantalla**, aunque hagamos scroll.
  Se usa para el botón hamburguesa.

```css
.open-menu {
  position: fixed;
  top: 14px;
  left: 14px;
}
```

* `sticky`: el elemento se queda pegado cuando llegamos a cierta posición.
  Se usa para el header.

```css
.site-header {
  position: sticky;
  top: 0;
}
```

---

### 🔹 `z-index`

Indica qué elemento está **por encima** cuando se superponen.

```css
.site-header {
  z-index: 50;
}
```

Cuanto mayor el número, más arriba está.

---

### 🔹 `left` (y `top`, `right`, `bottom`)

Sirven para mover un elemento **cuando tiene position distinto de `static`**.

Ejemplo del menú lateral oculto:

```css
.side-menu {
  position: fixed;
  left: -230px; /* escondido */
}
.side-menu.active {
  left: 0;      /* visible */
}
```

---

### 🔹 `transition`

Hace que los cambios sean **suaves y animados**.

```css
.side-menu {
  transition: left 0.3s ease;
}
```

En vez de aparecer de golpe, se desliza.

---

### 🔹 `cursor`

Cambia la forma del cursor al pasar por encima.

```css
.open-menu {
  cursor: pointer;
}
```

Sirve para indicar que algo es **interactivo**.

---

### 🔹 `gap`

Marca el **espacio entre elementos** en Flex o Grid.

```css
.main-nav ul {
  display: flex;
  gap: 12px;
}
```

Es más cómodo que usar márgenes uno por uno.

---

### 🔹 `box-sizing`

Controla cómo se calcula el tamaño de los elementos.

Con el reset usamos:

```css
*, *::before, *::after {
  box-sizing: border-box;
}
```

Esto significa:

* el ancho incluye padding y borde
* es más fácil maquetar sin sorpresas
* los elementos no “crecen” sin darse cuenta

---

## 3. Explicación del código JavaScript

Aunque todavía no hemos visto programación, es útil entender **qué hace** el script del menú.

Este es el código:

```js
const sideMenu = document.getElementById("sideMenu");
const toggleBtn = document.querySelector(".open-menu");

toggleBtn.addEventListener("click", () => {
  sideMenu.classList.toggle("active");
  toggleBtn.classList.toggle("active");

  toggleBtn.textContent =
    sideMenu.classList.contains("active") ? "✖" : "☰";
});
```

### 🔹 ¿Qué está pasando?

1. **Selecciona elementos del HTML**

```js
const sideMenu = document.getElementById("sideMenu");
const toggleBtn = document.querySelector(".open-menu");
```

* `sideMenu` = el menú lateral
* `toggleBtn` = el botón hamburguesa

---

2. **Detecta cuándo hacemos clic**

```js
toggleBtn.addEventListener("click", () => {
```

Significa:

> cuando pulses el botón, ejecuta lo que hay dentro.

---

3. **Abre o cierra el menú**

```js
sideMenu.classList.toggle("active");
```

* si el menú estaba cerrado → se abre
* si estaba abierto → se cierra

El efecto lo hace **el CSS**, no JavaScript:

```css
.side-menu { left: -230px; }
.side-menu.active { left: 0; }
```

---

4. **Cambia el icono del botón**

```js
toggleBtn.textContent =
  sideMenu.classList.contains("active") ? "✖" : "☰";
```

* Si el menú está abierto → muestra ✖
* Si está cerrado → muestra ☰

---

### ✅ Idea final para recordar

> El JavaScript no diseña la web:

> solo detecta la acción del usuario (clic)

> y activa o desactiva clases CSS para mostrar u ocultar el menú.
