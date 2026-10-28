# 📻 Túnel del Terror: Sala 2 - Radio Fantasma

- **Módulo:** Lenguaje de Marcas y Sistemas de Gestión de Información (1.º DAM)
- **Tema:** UD3 - Estructura de un documento HTML5 y bloques de contenido
- **Autores / Equipo de Desarrollo:** Fila 2 (David Cuco, Maximiliano Abilahoud, Adrián Durán, Álvaro Gil, Raúl Antonio Carrasco, Francisco Martínez, Alberto Florido, David Uzón)
- **Sala asignada:** Sala 2 - Radio Fantasma (Mesa 2)

---

## 1. Historia de la Sala

La antigua emisora local **"Radio Oculta 104.5"** cortó sus transmisiones inesperadamente a la medianoche del 31 de octubre de 1999. Hoy en día, los visitantes sintonizan una frecuencia abandonada donde se escuchan interferencias y mensajes en bucle. La página web simula el panel de control y el diario de bitácora de la emisora, ocultando la pista de la frecuencia que el ordenador de 2.º (JavaFX) necesita para liberar la siguiente letra del juego.

---

## 2. Pista Acordada con 2.º (JavaFX)

- **Pista oculta:** `FRECUENCIA_888`
- **Mecánica:** La frecuencia está oculta en la página HTML mediante metadatos y etiquetas de contenido (`<abbr title="...">` y el documento incrustado `pergamino.html`). Al introducir o sintonizar este valor en la aplicación JavaFX de la mesa de 2.º, se entregará la letra **«I»**.

---

## 3. Vista Previa de la Sala

![Vista previa de la Sala 2 - Radio Fantasma](./docs/captura-sala.png)

---

## 4. Diario de Investigación (Retos HTML - UD2 / UD3)

| Reto / Paso | Pregunta / Reto planteado | Fuente oficial / Concepto UD3 | Prueba realizada en `pruebas.html` | Decisión tomada para la sala |
| :--- | :--- | :--- | :--- | :--- |
| **Reto 1** | ¿Cómo definir el tipo de documento para evitar las peculiaridades del modo del navegador? | Contrato `<!DOCTYPE html>` (HTML5) | Inserción en la primera línea de `pruebas.html`. | Se coloca `<!DOCTYPE html>` al inicio estricto sin líneas en blanco anteriores. |
| **Reto 2** | ¿Cómo configurar la cabecera `<head>` y el idioma para evitar símbolos extraños con eñes y tildes? | `<html lang="es">` y `<meta charset="UTF-8">` | Verificación de renderizado de tildes y eñes sin entidades. | Se añade `lang="es"` en `<html>` y `charset="UTF-8"` como primer hijo del `<head>`. |
| **Reto 3** | ¿Cómo jerarquizar los títulos sin saltar niveles según las pautas semánticas? | Jerarquía `<h1>` a `<h6>` | Estructuración del título de la emisora y secciones. | Un único `<h1>` para el título de la radio y uso de `<h2>` y `<h3>` sin saltos directos. |
| **Reto 4** | ¿Cómo agrupar bloques temáticos de contenido y separarlos visualmente? | Elementos `<div>`, `<p>` y `<hr>` | Agrupación de secciones del panel de control con `<div>`. | Se organizan los contenidos en bloques `<div>` comentados (`<!-- ... -->`) y separados por `<hr>`. |
| **Reto 5** | ¿Cómo mostrar mensajes preformateados (frecuencias, listas alineadas) respetando espacios? | Etiqueta `<pre>` | Formateo del registro de frecuencias y horas. | Uso de `<pre>` en la tabla de frecuencias de transmisión del equipo. |
| **Reto 6** | ¿Cómo representar citas textuales largas de las transmisiones recibidas? | Etiqueta `<blockquote>` | Inserción de un testimonio transcrito de la época. | Inclusión de la última transmisión de 1999 con `<blockquote>`. |
| **Reto 7** | ¿Cómo insertar símbolos especiales reservando caracteres reservados de HTML? | Entidades HTML (`&amp;`, `&lt;`, `&gt;`, `&copy;`) | Inserción de entidad de copyright en el pie. | Inserción de `&copy; 2026 Radio Oculta` y entidades en el texto de las frecuencias. |
| **Reto 8** | ¿Cómo ocultar la pista mediante atributos semánticos de texto sin usar CSS ni JS? | Atributo `title` en `<abbr>` y documento secundario | Pruebas con metadatos de texto y paso de cursor. | Se usa `<abbr title="FRECUENCIA_888">104.5 MHz</abbr>` para mostrar la pista al pasar el cursor. |

---

## ⚖️ 5. Comparativa de Formas para Esconder la Pista (Solo HTML)

Para ocultar la pista utilizando únicamente la especificación de etiquetas y atributos HTML vistos en clase:

1. **Opción A (Metadatos de etiqueta mediante atributo `title`):**
   - **Funcionamiento:** Oculta la información dentro de la propiedad `title` de etiquetas como `<abbr>` o en atributos descriptivos.
   - **Ventajas:** No altera la maquetación inicial y requiere que el visitante inspeccione o pase el ratón deliberadamente sobre el texto.

2. **Opción B (Incrustación en documento secreto `pergamino.html`):**
   - **Funcionamiento:** La pista se redacta dentro de un archivo secundario cargado mediante un marco/documento adjunto (`<iframe>`).
   - **Ventajas:** Separa la pista del flujo principal de la portada.

**Elección final:** Se implementa la Opción A apoyada por el documento `pergamino.html`, integrando la pista dentro del texto del dial sin romper la validación ni requerir lenguajes adicionales.

---

## ✅ 6. Checklist de Calidad y Validación W3C

- [x] El archivo `index.html` pasa la validación sin errores según el estándar W3C (Captura en `docs/validacion.png`).
- [x] El archivo `pergamino.html` pasa la validación sin errores según el estándar W3C (Captura en `docs/validacion-pergamino.png`).
- [x] La estructura del proyecto respeta la convención de carpetas (`/css`, `/img`, `/docs`).
- [x] Historial de commits realizado de forma gradual con mensajes claros y descriptivos.

---

## 🛠️ 7. Recursos y Herramientas Utilizadas

- **Editor de Código:** Visual Studio Code (Atajos Emmet: `! + Tab`).
- **Validador Oficial:** [Servicio de Validación de Marcado W3C](https://validator.w3.org/).
- **Estilos Visuales:** Hoja de estilos `css/terror.css` proporcionada por el departamento.
- **Recursos Multimedia:**
  - `img/estudio.jpg`: Fotografía del estudio de radio abandonado.
  - `img/radio-antigua.jpg`: Detalle del dial y mando de la radio vintage. Markup Validation Service (captura en `docs/validacion.png`).
