# 📘 DOCUMENTACIÓN TÉCNICA - REFACTOR MONTERREY NEW YORK LIFE

## 🎯 Objetivo del Proyecto
Reconstruir e implementar un refactor completo del sitio web institucional de Monterrey New York Life (https://www.mnyl.com.mx/), manteniendo su identidad corporativa ejecutiva mientras se mejora la experiencia UI/UX con tecnologías modernas.

---

## 1. SISTEMA DE DISEÑO BASE (DESIGN TOKENS)

### 🎨 Paleta de Colores

| Tipo | Nombre | Hex | Uso |
|------|--------|-----|-----|
| **Primarios** | Azul Marino Dark | `#153A5A` | Logotipo, botones principales, titulares |
| | Azul Marino Main | `#00335B` | Elementos corporativos, hover buttons |
| | Azul Interactive | `#3073C0` | Botones de acción, enlaces, iconos |
| **Neutros** | Blanco | `#FFFFFF` | Fondos principales, texto inverse |
| | Crema/Arena | `#F9F8F4` | Fondo Directorio Médico, secciones accent |
| | Gris Claro | `#F5F5F5` | Barra superior, fondos utilitarios |
| | Gris Medium | `#E0E0E0` | Bordes, inputs, separadores |
| | Gris Dark | `#666666` | Texto secundario |
| | Antracita | `#333333` | Texto primario |
| **Estados** | Hover | `#2A5A8A` | Estado hover de elementos interactivos |
| | Active | `#1A4A7A` | Estado active/presionado |
| | Focus | `#3073C0` | Estado de foco en formularios |

### 📝 Tipografía y Jerarquía CSS

#### Fuentes
- **Serif (Headings):** `'Playfair Display', 'Merriweather', Georgia, serif`
- **Sans-Serif (Body/UI):** `'Montserrat', 'Open Sans', Roboto, sans-serif`

#### Headings
| Etiqueta | Tamaño | Peso | Line-Height | Familia | Color |
|----------|--------|------|-------------|---------|-------|
| `h1` | 48px | 700 | 1.2 | Serif | #153A5A |
| `h2` | 36px | 700 | 1.3 | Serif | #153A5A |
| `h3` | 28px | 600 | 1.3 | Serif | #153A5A |
| `h4` | 24px | 600 | 1.4 | Sans-Serif | #153A5A |
| `h5` | 20px | 600 | 1.4 | Sans-Serif | #153A5A |
| `h6` | 18px | 600 | 1.4 | Sans-Serif | #153A5A |

#### Body Text
| Clase | Tamaño | Peso | Line-Height | Color |
|-------|--------|------|-------------|-------|
| Large | 18px | 400 | 1.6 | #333333 |
| Medium | 16px | 400 | 1.6 | #333333 |
| Small | 14px | 400 | 1.5 | #666666 |
| Caption | 12px | 400 | 1.4 | #666666 |

#### Enlaces
- **Default:** `#3073C0`
- **Hover:** `#153A5A`
- **Visited:** `#3073C0`

### 📐 Layout y Grid System

#### Espaciado Standard
```css
--spacing-xs: 4px
--spacing-sm: 8px
--spacing-md: 16px
--spacing-lg: 24px
--spacing-xl: 32px
--spacing-2xl: 48px
--spacing-3xl: 64px
--spacing-4xl: 96px
```

#### Container
- **Max Width:** 1200px
- **Padding Mobile:** 16px
- **Padding Tablet:** 24px
- **Padding Desktop:** 32px

#### Grid
- **Columnas:** 12
- **Gutter:** 24px
- **Margin:** 32px

#### Breakpoints
- **Mobile:** 320px
- **Tablet:** 768px
- **Desktop:** 1024px
- **Wide:** 1440px

---

## 2. ARQUITECTURA DE COMPONENTES

### 📋 Checklist de Implementación (Orden Top-to-Bottom)

| Orden | Componente | Descripción | Dependencias |
|-------|------------|-------------|--------------|
| 1 | **UtilityNav** | Barra superior de utilidades con enlaces segmentados | - |
| 2 | **Header** | Navegación principal con logo, menú, buscador y teléfono | UtilityNav |
| 3 | **HeroCarousel** | Carrusel principal con imagen, texto promocional y CTA | Header |
| 4 | **MedicalDirectoryWidget** | Buscador médico con selects en cascada y búsqueda abierta | HeroCarousel |
| 5 | **QuickToolsGrid** | Grid de herramientas rápidas (Trámites, Pagos, Tokenizador, Bancos) | MedicalDirectoryWidget |
| 6 | **ProductShowcase** | Sección de productos (Seguros de Vida y GMM) | QuickToolsGrid |
| 7 | **RecruitmentBanner** | Banner de reclutamiento de asesores | ProductShowcase |
| 8 | **FatFooter** | Pie de página con mapa del sitio, certificaciones y legales | RecruitmentBanner |

---

## 3. DESGLOSE MODULAR DETALLADO

### 3.1 UtilityNav (Barra de Utilidades Superior)

**Propósito:** Segmentación de usuarios para desviar tráfico específico a portales privados.

**Elementos UI:**
- Fondo: `#F5F5F5` (Gris Claro)
- Alineación: Derecha
- Tipografía: Sans-serif, 12px, uppercase
- Enlaces separados por `|`
- Links: "MI SMNYL CLIENTES", "DOCUMENTOS", "SOY ASESOR", "SOY PROVEEDOR"

**Comportamiento:**
- Hover en enlaces: Color `#3073C0`
- Todos los links abren en nueva pestaña (`target="_blank"`)

---

### 3.2 Header (Navegación Principal)

**Propósito:** Navegación core y conversión inbound con identidad corporativa visible.

**Estructura:**
- **Fondo:** `#FFFFFF` (Blanco)
- **Posicionamiento:** Sticky (fijo al hacer scroll)
- **Layout:** Flexbox (Logo izquierda, Nav centro, Acciones derecha)

**Elementos:**
1. **Logotipo:** 
   - Bloque azul con "NEW YORK LIFE" (serif blanca)
   - Texto "SEGUROS MONTERREY" (serif azul)

2. **Navegación Central:**
   - Links: "Seguros individuales", "Seguros grupales", "Blog", etc.
   - Hover: Color `#3073C0` o despliegue de megamenú

3. **Buscador Global:**
   - Input con bottom border only
   - Icono de lupa (SVG)
   - Placeholder: "Búsqueda abierta"

4. **Botón de Contacto:**
   - Background: `#153A5A`
   - Color texto: `#FFFFFF`
   - Texto: "800 906 2100"
   - Border-radius: 4px
   - Padding: 12px 24px

**Comportamiento:**
- Menú responsive con hamburguesa en mobile
- Sticky al hacer scroll hacia abajo
- Búsqueda con autocomplete (sugerido)

---

### 3.3 HeroCarousel (Carrusel Principal)

**Propósito:** Marketing de oportunidad y CTR para campañas activas.

**Estructura:**
- **Ancho:** Full-width
- **Fondo:** Imagen fotográfica HD con overlay degradado izquierdo
- **Controles:** Flechas izquierda/derecha en cajas blancas

**Contenido:**
- **Título (H1):** Serif, 48px, `#153A5A`
- **Subtítulo (P):** Sans-serif, 18px, `#666666`
- **CTA Button:** 
  - Texto: "Conoce más >>" o variable según campaña
  - Background: `#153A5A`
  - Color: `#FFFFFF`

**Comportamiento:**
- Auto-play cada 5 segundos (configurable)
- Pausa al hover
- Navegación con flechas y dots indicadores
- Transición: Fade o slide (0.5s ease)
- Tracking de clicks para analytics

---

### 3.4 MedicalDirectoryWidget (Buscador Médico)

**Propósito:** Herramienta transaccional de self-service para retención de clientes.

**Estructura:**
- **Fondo:** `#F9F8F4` (Crema)
- **Bordes:** Superior e inferior sutiles (`#E0E0E0`)
- **Layout:** CSS Grid o Inline-flex

**Encabezado:**
- Título: "DIRECTORIO DE PROVEEDORES MÉDICOS EN CONVENIO"
- Icono pequeño a la izquierda
- Tipografía: Sans-serif, 14px, uppercase, `#153A5A`

**Formulario (3 Selects + 1 Input + Button):**
1. **Select 1:** Planes (Individuales, Colectivos, etc.)
2. **Select 2:** Tipo de Proveedor (Hospitales, Clínicas, Médicos)
3. **Select 3:** Especialidad/Ubicación
4. **Input Texto:** Búsqueda abierta
5. **Botón BUSCAR:**
   - Background: `#3073C0`
   - Color: `#FFFFFF`
   - Padding: 12px 32px

**Accesos Rápidos Laterales:**
- Icono blanco en círculo azul (`#3073C0`)
- Texto en dos líneas debajo
- Links: "Proveedor dental", "Tabulador médico"

**Lógica de Negocio:**
- **Cascading Dropdowns:** Cada select filtra las opciones del siguiente
- **Validación:** Al menos un campo debe estar lleno
- **API Call:** REST/GraphQL para filtrar base de datos en tiempo real
- **Loading State:** Spinner durante la búsqueda
- **Error Handling:** Mensajes claros si no hay resultados

---

### 3.5 QuickToolsGrid (Herramientas Rápidas)

**Propósito:** Reducción de fricción para tareas post-venta comunes.

**Estructura:**
- **Layout:** Grid 4 columnas (desktop), 2 (tablet), 1 (mobile)
- **Cards:** Blanco con sombra suave

**Tarjetas:**
1. **Trámites GMM** - Icono de documento
2. **Pago en línea** - Icono de tarjeta/crédito
3. **Tokenizador** - Icono de seguridad/token
4. **Bancos** - Icono de institución bancaria

**Comportamiento:**
- Hover: Elevación de sombra (`0 4px 16px`)
- Click: Redirección a sección específica
- Iconos: SVG optimizados

---

### 3.6 ProductShowcase (Sección de Productos)

**Propósito:** Lead generation para usuarios en funnel de compra.

**Estructura:**
- **Layout:** 2 banners grandes o tarjetas horizontales
- **Productos:** 
  - Seguros de Vida
  - Seguros de Gastos Médicos Mayores

**Elementos por Producto:**
- Imagen representativa
- Título (H2/H3): Serif, `#153A5A`
- Descripción breve: Sans-serif, 16px
- CTA Button: "Conoce Más"

**Comportamiento:**
- Hover en tarjeta: Ligera elevación
- CTA: Redirección a landing page específica del producto
- Formulario de captura en landing page

---

### 3.7 RecruitmentBanner (Captación de Asesores)

**Propósito:** Expansión B2B / Recursos humanos para reclutar agentes.

**Estructura:**
- **Ancho:** Full-width
- **Fondo:** Imagen o color sólido (`#153A5A` o gradiente)
- **Layout:** Flexbox (Texto izquierda, CTA derecha) o centrado

**Contenido:**
- Título: "CONVIÉRTETE EN ASESOR..." (H2, Serif, blanco o azul)
- Subtítulo: Descripción de beneficios
- CTA Button: "Únete ahora" o "Conoce historias"

**Comportamiento:**
- Click: Redirección a microsite de reclutamiento
- Posible formulario modal inline

---

### 3.8 FatFooter (Pie de Página)

**Propósito:** SEO, compliance legal y construcción de confianza.

**Estructura:**
- **Fondo:** `#153A5A` o `#333333`
- **Texto:** Blanco o gris claro
- **Layout:** Grid 4-5 columnas

**Columnas Típicas:**
1. **Seguros** - Links a productos
2. **Conócenos** - Historia, misión, visión
3. **Únete** - Bolsa de trabajo, asesores
4. **Ayuda** - Contacto, FAQs, siniestros
5. **Legal** - Aviso de privacidad, términos

**Fila Inferior:**
- Logotipos de certificaciones:
  - Great Place to Work
  - PCI Security
  - Buró de Crédito
  - CONDUSEF
- Copyright y año actual
- Redes sociales (iconos)

**Comportamiento:**
- Links con hover: Underline o cambio de color
- Certificaciones: Static o link a validación
- Responsive: Columnas se apilan en mobile

---

## 4. NOTAS TÉCNICAS PARA IMPLEMENTACIÓN

### 🔧 Gestión de Estado Compleja
- **MedicalDirectoryWidget:** Requiere estado para dropdowns en cascada
- **HeroCarousel:** Estado para slide activo, auto-play, pausa
- **Header:** Estado para sticky nav y menú mobile

### ♿ Accesibilidad (WCAG 2.1 AA)
- Contraste mínimo 4.5:1 para texto normal
- Labels en todos los inputs de formulario
- Aria-labels en carrusel y botones iconográficos
- Navegación por teclado funcional
- Focus visible en todos los elementos interactivos

### ⚡ Optimización de Rendimiento
- **Imágenes:** Formato WebP con fallback JPG
- **Lazy Loading:** Para imágenes below the fold
- **Iconos:** SVG sprite o icon font
- **CSS:** Critical CSS inline, resto diferido
- **JavaScript:** Code splitting por componente

### 📱 Responsive Design
- Mobile-first approach
- Breakpoints definidos en tokens
- Testing en dispositivos reales
- Touch-friendly (mínimo 44px para targets táctiles)

### 🔒 Seguridad y Compliance
- HTTPS obligatorio
- Sanitización de inputs en buscador
- Protección CSRF en formularios
- Cumplimiento de normativa financiera mexicana

---

## 5. ARCHIVOS DE CONFIGURACIÓN GENERADOS

### ✅ JSON Tokens
📄 `/workspace/design-tokens.json`
- Contiene todos los tokens de diseño en formato JSON
- Ideal para importar en sistemas de diseño o frameworks

### ✅ CSS Variables
📄 `/workspace/css-variables.css`
- Variables CSS nativas (:root)
- Clases de utilidad base incluidas
- Listo para importar en cualquier proyecto

---

## 6. SIGUIENTES PASOS RECOMENDADOS

1. **Configurar entorno de desarrollo** (React/Vue/Angular + Tailwind o CSS puro)
2. **Importar tokens de diseño** desde JSON o CSS variables
3. **Implementar módulo por módulo** siguiendo el checklist:
   - Empezar por `UtilityNav`
   - Continuar con `Header`
   - Seguir con `HeroCarousel`
   - Y así sucesivamente...
4. **Testing** después de cada módulo (visual, funcional, performance)
5. **Optimización final** (SEO, accesibilidad, rendimiento)

---

## 📞 ¿Listo para comenzar?

Ahora que tienes la documentación completa, puedes solicitar la implementación módulo por módulo. Por ejemplo:

*"Basándote en los tokens de diseño, prográmame el componente **UtilityNav** usando React y Tailwind CSS"*

O especifica tu tecnología preferida y comenzamos con el primer módulo de la lista.
