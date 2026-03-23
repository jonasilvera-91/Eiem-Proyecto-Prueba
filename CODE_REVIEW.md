# Revisión de buenas prácticas

Fecha: 2026-03-23

## Hallazgos principales

1. **Markup inválido en el footer**
   - Hay etiquetas de cierre `</a>` extra en múltiples páginas, lo que rompe la estructura HTML.
2. **Seguridad en enlaces externos**
   - Los enlaces con `target="_blank"` no incluyen `rel="noopener noreferrer"`.
3. **Accesibilidad de imágenes**
   - Muchos `alt` son genéricos (por ejemplo, `carousel1`, `logo EIEM`) y no describen propósito o contenido.
4. **Accesibilidad y semántica en botones**
   - Se usa `<a><button>...</button></a>`, patrón no semántico y conflictivo para lectores de pantalla.
5. **Contenido temporal desactualizado**
   - En footer figura `© 2025`; conviene parametrizar o actualizar para evitar deuda de mantenimiento.
6. **Duplicación estructural**
   - Header/footer repetidos en todas las páginas, sin un mecanismo de componentes/plantillas.
7. **Calidad de contenido y consistencia**
   - Errores tipográficos (`linkeding`, `Boostrap`, `BOOTRSAP`) y placeholders sin implementar (`VIDEO_ID`, `href="#"`).
8. **Rendimiento web**
   - Falta `loading="lazy"` en imágenes no críticas y dimensiones explícitas para prevenir CLS.
9. **Estilos globales en archivo de variables**
   - `_variables.scss` mezcla tokens de diseño con estilos base globales; dificulta escalabilidad.
10. **Responsive limitado**
   - Hay un único breakpoint móvil (`max-width: 430px`) que puede quedar corto para tablets y móviles grandes.

## Recomendaciones priorizadas

### Alta prioridad
- Corregir HTML inválido y ejecutar validación W3C.
- Agregar `rel="noopener noreferrer"` a todos los enlaces externos.
- Reemplazar `a > button` por `a` estilizado como botón o `button` con evento real.

### Media prioridad
- Mejorar textos alternativos (`alt`) y revisar jerarquía de encabezados por página.
- Reemplazar placeholders (`VIDEO_ID`, `#`) por rutas reales o deshabilitar visualmente.
- Agregar `loading="lazy"`, `width` y `height` en imágenes de contenido.

### Baja prioridad (arquitectura)
- Separar tokens (`_variables.scss`) de estilos base (`_base.scss`).
- Definir más breakpoints y una escala tipográfica responsive.
- Reducir duplicación con componentes (SSR, includes o generador estático).

## Checklist sugerido

- [ ] Validación HTML en todas las páginas.
- [ ] Revisión de accesibilidad con Lighthouse/axe.
- [ ] Revisión SEO técnico (metadatos OG/Twitter, canonical, sitemap, robots).
- [ ] Pipeline de build: mantener SCSS como fuente y evitar editar `assets/css/style.css` manualmente.
