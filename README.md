# 🦁 Linktree · Federazione CAVA

Página de enlaces (estilo "link in bio") para el **Comitato delle Associazioni Venete dell'Argentina**, pensada para escanear vía QR y usar principalmente desde el celular.

Hecha en **HTML + CSS**, con un script mínimo para los idiomas, sin frameworks ni dependencias — liviana, fácil de editar y de hostear en cualquier lado.


---

## 📁 Estructura del proyecto

```
.
├── index.html   → Estructura de la página (contenido, textos, links)
├── style.css    → Todos los estilos (colores, tipografía, layout)
├── fonts/       → Tipografía ZT Nature en los pesos que usa la página
└── fotos/       → Imágenes que usa la página
    ├── isotipo.png       → Círculo arriba de los links
    ├── iconoweb.png      → Ícono de la pestaña del navegador
    ├── fondito.jpg       → Fondo de la página
    ├── vista-previa.png  → Imagen al compartir el link
    └── firma-logo.png    → Logo para la firma de mail
```

> ⚠️ No muevas ni renombres `fotos/firma-logo.png`: las firmas de mail pueden estar usando su dirección.

---

## 🚀 Cómo publicarlo / actualizarlo

1. Abrí `index.html` en el navegador para ver los cambios en el momento (doble clic alcanza).
2. Para publicarlo online, guardá los cambios, publicalo y el link original va a andar siempre.
3. Apuntá el código QR a la URL final una vez publicado.

---

## 🛠️ Cómo editar lo más común

### Cambiar un link o agregar uno nuevo
Los enlaces viven dentro de `<div class="links">` en `index.html`. Cada uno sigue esta estructura:

```html
<a class="link" href="URL_ACA" target="_blank" rel="noopener">
  <svg viewBox="0 0 24 24">...</svg>
  Texto visible
</a>
```

Para agregar una red nueva, copiá un bloque `<a class="link">` existente, cambiá el `href`, el texto, y el ícono SVG de adentro (hay miles de íconos gratuitos en [Lucide](https://lucide.dev/icons/) o [Material Symbols](https://fonts.google.com/icons), buscá "outline" o "filled" según el estilo que uses).

> ⚠️ Importante: el mail usa `href="mailto:direccion@mail.com"` en vez de una URL normal — no lleva `target="_blank"`.

### Cambiar nombre, subtítulo o logo
Están arriba de todo en `index.html`, antes de `<div class="links">`. El logo es una imagen (`<img>`) que se muestra en un círculo — para cambiarlo, solo hay que reemplazar el `src`. Usá una versión achicada, no un original en alta resolución, que es mucho más pesado.

### Cambiar textos e idiomas
La página detecta el idioma del dispositivo y se muestra en español, italiano o inglés. Si el dispositivo está en otro idioma, queda en español. Los botones ES, IT y EN permiten cambiarlo, y la elección queda guardada en ese navegador.

- Todos los textos están en `TRADUCCIONES`, dentro del `<script>` al final de `index.html`. Para cambiar un texto en español, cambialo ahí y también en el HTML.
- Si agregás un botón, ponele `data-i18n="nombre"` a su texto y sumá `nombre` en cada idioma de `TRADUCCIONES`.

### Cambiar la vista previa al compartir
La tarjeta que aparece al pasar el link por WhatsApp o Facebook se define con las etiquetas `og:` del `<head>` de `index.html`, y su imagen es `fotos/vista-previa.png` (1200 x 630). Siempre sale en español, porque esas aplicaciones no detectan el idioma de quien recibe el link. Si cambia la dirección de la página, hay que actualizarla en `og:url` y `og:image`.

### Cambiar colores
Todos los colores están centralizados como **variables CSS** al inicio de `style.css`, dentro de `:root`. Por ejemplo:

```css
:root{
  --texto: ...;
  --crema: ...;
  --crema-2: ...;
  --laguna: ...;
  --oro: ...;
}
```

Cambiando el valor de una variable ahí, se actualiza en todo el sitio automáticamente — no hace falta tocar el resto del CSS.

---

## 🤝 Si algún día alguien más retoma esto

Este sitio fue armado para ser **lo más simple de mantener posible**, incluso para alguien sin experiencia en programación:

- No hay que instalar nada ni correr comandos — es abrir el archivo y editar texto.
- Todo el contenido (textos, links, colores) está a la vista en dos archivos, sin lógica oculta ni configuración externa.
- Si algo se rompe visualmente, el 90% de las veces alcanza con revisar que no falte cerrar una etiqueta (`<a>`, `<div>`, `<svg>`) o una llave `{ }` en el CSS.

Cualquier duda sobre una sección puntual, los comentarios dentro del propio `style.css` y `index.html` deberían guiar bastante.

---
<p align="center">
  <sub>Hecho con ❤️ para la Federazione CAVA — por <a href="https://github.com/wurst-bruno">@wurst-bruno</a></sub>
</p>
