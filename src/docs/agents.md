
# Guía de Agentes de IA - Proyecto AIA Web

Este documento sirve como contexto maestro para la generación de código y autocompletado en este proyecto.

---

## 1. Identidad Visual (Estricta)

Cualquier código generado debe usar **exclusivamente** estos valores hexadecimales. No usar colores aproximados de Tailwind.

### Paleta de Colores

| Nombre | Hex Code | Uso |
| :--- | :--- | :--- |
| **AIA Dark** (Principal) | `#221965` | Texto principal, Títulos, Inicio de Gradiente. |
| **AIA Light** (Acento) | `#4D40AC` | Botones, Enlaces, Hover, Final de Gradiente. |
| **AIA Background** | `#F4F5F0` | Color de fondo general de la página (Body). |
| **White** | `#FFFFFF` | Fondo de las tarjetas (Cards). |

### Estilos Visuales Clave

**1. El Gradiente "Hero" (Marca):**

* **CSS Original:** `linear-gradient(135deg, #221965 0%, #4D40AC 100%)`
* **Equivalente Tailwind:** `bg-gradient-to-br from-[#221965] to-[#4D40AC]`

**2. Efecto Hover en Tarjetas (Física):**

* **Comportamiento:** Al pasar el ratón, la tarjeta sube 5px y gana sombra.
* **Clases Tailwind a usar:**
  `transition-all duration-300 ease-out hover:-translate-y-1 hover:shadow-xl`
  *(Nota: La sombra personalizada es `0 10px 25px rgba(0,0,0,0.1)`)*

**3. Efecto Hover en Iconos:**

* **Comportamiento:** Escala suave al 110%.
* **Clases Tailwind a usar:**
  `transition-transform duration-300 hover:scale-110`

---

## 2. Reglas Técnicas (Stack: Astro + Tailwind)

1. **Estructura de Componentes:**
    * Convertir secciones HTML repetitivas en componentes `.astro` (ej: `EventCard.astro`, `Navbar.astro`).
    * Usar `Layouts` para el `<head>` y la estructura común (`<html>`, `<body>`).

2. **Estilos:**
    * **Prohibido** usar etiquetas `<style>` para CSS que se pueda hacer con Tailwind.
    * **Prohibido** usar CDNs (ej: `cdn.tailwindcss.com`). Tailwind debe estar instalado en el proyecto.

3. **Scripts:**
    * Evitar jQuery. Usar JavaScript moderno (Vanilla JS) dentro de etiquetas `<script>` en los componentes Astro si es necesaria interactividad (ej: menú móvil).

---

## 3. System Prompt (Copia esto a tu IA)

Usa este bloque cuando pidas código para asegurar que mantiene la marca:

```text
Actúa como un desarrollador experto en Astro y Tailwind CSS.
Estás migrando una landing page existente.

TUS REGLAS DE DISEÑO (INMUTABLES):
1. Fondo de la web: #F4F5F0
2. Color de texto principal: #221965
3. Color de acento/botones: #4D40AC
4. Gradientes: bg-gradient-to-br from-[#221965] to-[#4D40AC]
5. Interacciones: Usa "hover:-translate-y-1" para tarjetas interactivas.

TU TAREA:
Genera código limpio en Astro. No inventes clases de CSS, usa utilidades de Tailwind con valores arbitrarios (ej: bg-[#221965]) si no están configurados en el theme.

