# CompuLab — Armado & Reparación

Landing page cinemática e interactiva para un taller de armado y reparación de PCs de alto rendimiento.

> Demo de proyecto de UX/UI para **Codellege by Softtek**. No es un e-commerce tradicional: es una experiencia narrativa guiada por scroll, desde el deseo hasta la entrega de la PC.

## Concepto: "El deseo que se materializa"

La página cuenta una historia en actos en lugar de mostrar un catálogo estático:

1. **Acto I — El deseo (Spark):** lienzo oscuro con chispa amarilla neón que reacciona al cursor y revela el mensaje conceptual.
2. **Acto II — La idea:** ¿para qué la usarías? Crear, jugar, trabajar.
3. **Acto III — El plan:** reglas claras con CompuLab (compatibilidad, tiempo, pruebas, garantía) + blueprint / sello de trabajo.
4. **Acto IV — El Playground:** el ritual de armado. Simulador 3D interactivo donde el usuario instala Motherboard, CPU, RAM, Almacenamiento, PSU, GPU y Ventiladores, con validación de orden, compatibilidad y cálculo de consumo.
5. **Acto V — La configuración (El despertar):** tests de estrés, BIOS/setup y estándares de calidad.
6. **Acto VI — El encuentro y cierre (CTA):** vista de la PC armada + llamado a la acción ("Podrías ser tú, ¿empezamos?").

Ver la narrativa completa en [`proyecto_narrativa_masterplan.md`](./proyecto_narrativa_masterplan.md).

## Stack

- **React 19 + TypeScript + Vite 7**
- **Tailwind CSS 4** (sistema de diseño, paleta `#09090b` / `#facc15`, fuentes Outfit + Syne)
- **Three.js + @react-three/fiber + @react-three/drei** (simulador 3D del Acto IV, modelos procedurales, OrbitControls, bloom)
- **GSAP + ScrollTrigger** (timelines de scroll, pinning, transiciones)

## Requisitos

- Node.js 18+ (recomendado 20 LTS)
- npm 9+

## Instalación y uso

```bash
npm install
npm run dev      # servidor de desarrollo (Vite)
npm run build    # tsc + build de producción
npm run preview  # previsualizar el build
```

Abre `http://localhost:5173` en desarrollo.

## Estructura del proyecto

```
.
├── index.html                  # título, fuentes (Outfit + Syne), root
├── src/
│   ├── App.tsx                 # composición de actos + gating (completar config para continuar)
│   ├── main.tsx                # entry point
│   ├── index.css               # estilos globales / Tailwind
│   ├── data/
│   │   ├── content.ts          # copies, marca, contacto, servicios
│   │   ├── constellation.ts    # datos de constelación Acto III
│   │   └── sparkPath.ts        # path de la chispa Acto I
│   └── components/acts/
│       ├── ActSpark.tsx        # Actos I–III (deseo, idea, plan, unbox)
│       ├── ActUnbox.tsx        # apertura de cajas / transición
│       ├── ActPlayground.tsx   # Acto IV — simulador 3D de armado
│       ├── act4/
│       │   ├── main.ts         # escena principal (gabinete, slots, bloom,Raycasting)
│       │   └── models.tsx      # modelos 3D procedurales + visor de producto
│       ├── ActConfig.tsx       # Acto V — configuración / resumen
│       └── ActCta.tsx          # Acto VI — CTA + footer
├── public/                     # assets estáticos (favicon, taller.jpg, pc-hero.png, etc.)
├── scripts/
│   └── build-constellation-edges.mjs
└── proyecto_narrativa_masterplan.md  # guion narrativo y arquitectura visual
```

## Estado / backlog

Ver [`PROBLEMAS.md`](./PROBLEMAS.md) para issues abiertos (autoscroll, alineación de papersheet, salto Acto IV → V, etc.).

## Autores

Creado por:

- **Cesar Oliva** — https://github.com/CesarOliva
- **FissilePond** — https://github.com/FissilePond

Más contribuciones de otros integrantes del equipo durante el programa Codellege by Softtek.

## Atribuciones

- **Simulador 3D / inspiración del PC builder:** la lógica y escena del armador interactivo toma como referencia el proyecto open-source [three-pc-builder-simulator](https://github.com/carlomigueldy/three-pc-builder-simulator) de **carlomigueldy**. Los modelos 3D de este repo fueron reimplementados de forma procedural con Three.js para esta demo; todo el crédito por la idea original del simulador corresponde a dicho repositorio y su autor.
- **Three.js, GSAP, React, Tailwind CSS** — a sus respectivos autores y licencias open-source.

## Licencia y uso

Proyecto con fines **educativos y de demostración** para Codellege by Softtek. Sin licencia comercial definida. Si reutilizas código o assets de terceros (incluido el simulador referenciado arriba), respeta sus licencias originales.
