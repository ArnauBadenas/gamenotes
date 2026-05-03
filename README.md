🎮 gamenotes
Notas personales de videojuegos publicadas con Quartz v4 en GitHub Pages.
🔗 Web: https://arnaubadenas.github.io/gamenotes/
📊 Dashboard: https://arnaubadenas.github.io/gamenotes/dashboard.html

Cómo funciona

Las notas viven en source/content/ como archivos .md (Obsidian)
Al hacer push a main, GitHub Actions construye y despliega automáticamente
Los archivos en source/raw_html/ se copian tal cual al build (para HTML custom como el dashboard)


Añadir notas nuevas

Crea el .md en Obsidian dentro de source/content/
Usa la estructura de carpetas existente:

League of legends/Champions/NombreCampeón.md → notas de campeón
League of legends/ → notas generales de LoL


Haz commit y push — la web se actualiza sola en ~1 min


Usar el dashboard
Abre https://arnaubadenas.github.io/gamenotes/dashboard.html

Busca un campeón por nombre (ej. Syndra, Aurora, Miss Fortune)
Muestra habilidades desde la DDragon API (siempre actualizado al último parche)
Si tienes una nota en League of legends/Champions/NombreCampeón.md, la carga automáticamente al lado
El panel "Preguntas que hacerse cada partida" es el checklist general — se resetea con el botón o al cerrar el navegador

Añadir nota de campeón nueva
source/content/League of legends/Champions/Syndra.md   ✅ aparece en el dashboard
source/content/League of legends/Champions/Yasuo.md    ✅ aparece en el dashboard
El nombre del archivo debe coincidir exactamente con el nombre del campeón (mayúsculas incluidas).

Estructura
source/
├── content/                  # Notas en Markdown (Obsidian)
│   └── League of legends/
│       ├── Champions/        # Una nota por campeón
│       └── ...               # Notas generales
├── raw_html/                 # HTML que se sirve directamente
│   └── dashboard.html        # Dashboard de campeones
└── quartz.config.ts          # Config de Quartz
