# Panera's 🞄 — Panadería y Pastelería Artesanal

Proyecto académico: sitio web estático (HTML + CSS) para una panadería y pastelería
artesanal, con catálogo de productos por categorías, carruseles y diseño adaptable
(móvil / tablet / escritorio).

🔗 **Sitio en producción:** <https://panaderia-panera-s.bqto.workers.dev>
📦 **Repositorio:** <https://github.com/Wiki2006/Panaderia-Panera-s>

---

## 🧁 Categorías del catálogo

| Categoría | Contenido |
|---|---|
| Panes Dulces | Bollos de crema, enrollados dulces, hojaldre, palmeras, pan de chocolate, pan de colores, pan de frutas, pan de tunja, pan piñita, pan de arequipe, entre otros |
| Panes Salados | Pan canilla, pan francés, pan de queso, pan de pizza, pan salado al ajillo, enrollados de jamón y queso, pan con jamón y queso, quesadilla, pan de la abuela |
| Pastelería | Galletas, donas, muffins, tortas y postres |
| Otros | Bollos, cortaditos y products especiales |

## 🛠️ Tecnologías

- **HTML5** semántico
- **CSS3** con variables CSS, `grid`, `flexbox` y animaciones CSS
- **Imágenes en WebP** (optimizadas de 57 MB a 3 MB)
- **Cloudflare Workers** con Assets estáticos
- **GitHub Actions** para despliegue automático

## 📁 Estructura

```
Proyecto Panera/
├── index.html            # Estructura completa del sitio
├── style.css             # Estilos, responsive y animaciones
├── img/                  # Imágenes .webp del catálogo
│   ├── panes-dulces/
│   ├── panes-salados/
│   ├── pasteleria/
│   └── tortas/
├── .github/workflows/
│   └── deploy.yml        # Despliegue automático a Cloudflare
├── wrangler.toml         # Configuración de Cloudflare Workers
├── .assetsignore         # Archivos excluidos del despliegue
└── .gitignore
```

## 🚀 Despliegue automático

Cada `git push` a la rama `main` dispara **GitHub Actions**, que publica el sitio
en Cloudflare Workers con la acción oficial `cloudflare/wrangler-action`.

```
git add .
git commit -m "descripcion del cambio"
git push origin main
```

El workflow está en `.github/workflows/deploy.yml` y usa dos secretos del repositorio
(**Settings → Secrets and variables → Actions**):

| Secreto | Valor |
|---|---|
| `CLOUDFLARE_API_TOKEN` | Token de API de Cloudflare con permiso **Workers Scripts: Edit** |
| `CLOUDFLARE_ACCOUNT_ID` | `ab64078d392dae383a5028e2373162d6` (también está en `wrangler.toml`) |

> Para crear el token: **Cloudflare → Perfil → API Tokens → Create Token** →
> plantilla *Edit Cloudflare Workers*. Ese token es el único dato sensible;
> si se filtra, revócalo desde el mismo panel.

Si el push falla, revisa **Actions → Deploy to Cloudflare Workers** en GitHub:
el log muestra exactamente qué paso falló.

### Despliegue manual (opcional)

```bash
npm install -g wrangler
wrangler login
wrangler deploy
```

## ✍️ Autores

- **Wiki2006** — desarrollo del sitio
- Equipo del proyecto — contenido y diseño de catálogo
