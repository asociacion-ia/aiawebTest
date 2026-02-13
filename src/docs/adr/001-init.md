Reunión Web
Migración de HTML no modular a Astro, Framework
Estático
1. Análisis Comparativo: Situación Actual vs. Propuesta
Característica Arquitectura Actual (HTML
Puro)
Arquitectura Propuesta (Astro)
Renderizado Cliente (El navegador
construye el estilo)
Estático (Build-time). El HTML llega ya
construido.
JavaScript Bloqueante (Carga todo al
inicio)
Islands Architecture. Carga JS solo
donde es interactivo.
Estilos Tailwind vía CDN (Pesado,
~3MB)
Tailwind Compilado. CSS purgado y
minificado (<10KB).
Mantenibilidad Baja. Copiar/Pegar código en
cada página.
Alta. Componentes reutilizables.
Datos "Hardcoded" en el HTML. Separados en JSON/Markdown
(Content Collections).
2. Estructura de Componentes Propuesta
Para solucionar la rigidez del diseño actual, se propone atomizar la interfaz en componentes
reutilizables. Esta estructura elimina la duplicación y facilita cambios de diseño globales.
/src/layouts
/src/components
MainLayout.astro : El contenedor maestro.
Contiene el <head> unificado (SEO, Favicons, Metadatos).
Inyecta globalmente la tipografía y los estilos base.
Maneja la estructura <html> y <body> .
Navbar.astro : Barra de navegación.
/src/pages
3. Ventajas y Desventajas
Pros (Beneficios)
Contras (Costes)
Mejora: Detecta automáticamente en qué página estás para resaltar el enlace activo.
Lógica: Incluye el script del menú móvil encapsulado solo aquí.
Footer.astro : Pie de página con enlaces sociales y copyright dinámico (año automático).
Hero3D.astro : Componente aislado para la animación.
Solución Vanta: Carga Three.js y Vanta.js solo cuando este componente está
presente. Evita errores en páginas que no lo usan.
EventCard.astro : Tarjeta unitaria de evento.
Recibe datos ( titulo , fecha , imagen ) como props. Garantiza que todas las
tarjetas sean visualmente idénticas.
Button.astro : Componente de botón estándar con variantes (primario/secundario) para
asegurar consistencia en el diseño (UI Kit).
index.astro : Página de inicio. Importa los componentes y ensambla la estructura.
events.astro : Página de eventos. Consume el archivo datos2.json y genera una rejilla
de <EventCard /> automáticamente.
1. Rendimiento Extremo: Astro elimina por defecto todo el JavaScript que no sea
estrictamente necesario. La web cargará casi instantáneamente.
2. Gestión de Dependencias: Soluciona automáticamente el problema de Tailwind CDN.
Astro compila el CSS durante el despliegue.
3. Encapsulamiento de Scripts: El problema de Vanta.js se aísla. Si la animación falla, solo
falla dentro de su componente, no rompe el resto de la página.
4. SEO Automatizado: Podemos generar sitemaps y metadatos dinámicos automáticamente
para cada página.
5. Escalabilidad de Contenido: Si mañana hay 50 eventos, no hay que copiar 50 veces el
HTML. Solo se añaden al JSON y Astro genera las 50 tarjetas.
1. Curva de Aprendizaje: La sintaxis de Astro (muy similar a HTML, pero con lógica).
2. Tiempo de Compilación: Ya no se puede "editar y subir". Se requiere un paso de "build"
(construcción) antes de desplegar, aunque GitHub Actions puede automatizar esto.
Cambios pendientes
Cosas pendientes
Añadir foto donde título, únete y proximos eventos como background
Hacer un grid 2x2
Dar mayor importancia al hackathon y arreglar placeholders para poner eventos de verdad
Modo oscuro
JSON con eventos futuros, información de asociación, etc... (base de datos)
Github test nueva web
Pasar manual de marca