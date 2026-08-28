# Changelog

Todos los cambios notables de este proyecto se documentan en este archivo.

El formato se basa en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/)
y este proyecto sigue [Versionado Semántico](https://semver.org/lang/es/).

## [Unreleased]

### Fixed

- Deploy en Cloudflare: `wrangler.toml` pasa al formato de Workers con assets
  estáticos (`[assets] directory = "./dist"`) para que `wrangler deploy`
  funcione; los scripts `deploy` / `cf:preview` usan `wrangler deploy` / `wrangler dev`.

## [1.0.0] - 2026-08-28

Primera versión pública del blog personal, construido sobre la plantilla
[Fuwari](https://github.com/saicaca/fuwari) (Astro) y personalizado para
[alvaroavila.dev](https://alvaroavila.dev).

### Added

- Configuración de despliegue en Cloudflare con Wrangler
  (`wrangler.toml`, `public/_headers`, scripts `deploy` y `cf:preview`).
- Banner con soporte de tema: imágenes independientes para claro y oscuro
  (`banner-light.png` / `banner-dark.png`) que se intercambian al cambiar de
  tema mediante la nueva opción `banner.srcDark` en `src/config.ts`.
- Fondo con patrón de cuadrícula (96×96 px) en `html`, con líneas atenuadas
  y valores propios para claro y oscuro.
- Perfil real en la barra lateral: nombre, bio y enlaces (Portafolio, GitHub,
  Email) con sus iconos.
- Página `/about/` (`src/content/spec/about.md`) con biografía, experiencia y
  enlaces reales.
- Variable de acento secundario `--secondary` (naranja `#fb923c`).

### Changed

- Identidad del sitio: título "Blog", subtítulo "Alvaro Avila Dev",
  idioma `es`.
- URL del sitio → `https://portfolio-blog.alvaroavila.dev` (`astro.config.mjs`
  y fallback de `rss.xml.ts`).
- Paleta de acento: azul como color principal (`hue` 264) para tags, enlaces,
  bordes activos y títulos; naranja como secundario para botones.
- Botones de acción (flechas de paginación, botón de "entrar al post") con
  relleno naranja y texto negro.
- Números de paginación como bloques sin relleno con borde naranja atenuado;
  la página actual con borde naranja pleno.
- Superficies en modo oscuro: fondo de página `#13151a`, tarjetas `#1c1c1f`
  con borde sutil, bloques de código más oscuros.
- Colores de texto en modo oscuro (`#e5e7eb` / `#93a3b8` / `#6b7280`).
- Estados hover: se elimina el cambio de color azul; ahora los elementos
  crecen ligeramente al pasar el cursor.
- Enlace de GitHub de la barra de navegación y del perfil →
  `github.com/Helien-Dev`.

### Removed

- Configuración de Vercel (`vercel.json`); el despliegue pasa a Cloudflare
  Pages (build `pnpm build`, salida `dist`).

### Fixed

- Banner oscuro descuadrado en la home (aparecía desplazado hacia abajo con un
  hueco arriba): el selector agrupado por coma
  `.enable-banner.is-home #banner, .enable-banner.is-home #banner-dark`
  hacía que el reescritor de la variante `lg:` de Tailwind convirtiera la
  segunda cláusula en un selector de descendiente. Se separan en reglas
  independientes.

[Unreleased]: https://github.com/Helien-Dev/portfolio-blog/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/Helien-Dev/portfolio-blog/releases/tag/v1.0.0
