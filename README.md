# 🇻🇪 TasaVe - Tasas de Cambio en Venezuela

Web App estática para visualizar las tasas de cambio en Venezuela en tiempo real (BCV Oficial USD/EUR y Binance P2P USDT) con calculadora reactiva bidireccional, gráfico de tendencia e histórico de cotizaciones.

---

## 🚀 Características

- 📊 **Tasas en tiempo real**: Dólar BCV, Euro BCV y USDT Binance P2P.
- 🧮 **Calculadora reactiva**: Conversión bidireccional inmediata entre VES, USD, EUR y USDT.
- 📈 **Histórico de precios**: Gráficos e historial diario con variación de tasas (`history.json`).
- 🌓 **Modo oscuro / claro**: Interfaz moderna tipo app financiera adaptable al usuario.
- ⚡ **Automatización en la nube**: Scraping automático cada hora mediante GitHub Actions.
- 🔍 **SEO & IA (GEO)**: Incluye `sitemap.xml`, `robots.txt` y `llms.txt` para optimización en Google Search Console y motores de Inteligencia Artificial (ChatGPT, Claude, Gemini, Perplexity).
- 📱 **Diseño Responsive**: Mobile-first optimizado para celulares, tablets y desktop.

---

## 🏗️ Estructura del Proyecto

```
.
├── index.html              # Interfaz web principal (HTML5 + JS + Tailwind CSS)
├── scraper.py              # Script en Python para obtener tasas actualizadas
├── data.json               # Tasas de cambio actuales (generado automáticamente)
├── history.json            # Histórico diario acumulado (generado automáticamente)
├── sitemap.xml             # Sitemap oficial para motores de búsqueda (actualizado automáticamente)
├── robots.txt              # Configuración de rastreo para web crawlers y bots de IA
├── llms.txt                # Estándar de contexto en Markdown para Inteligencias Artificiales
├── favicoin_tasaVe.png     # Favicon oficial de la aplicación
├── requirements.txt        # Dependencias de Python (requests)
└── .github/
    └── workflows/
        └── update.yml      # Workflow de GitHub Actions (ejecución horaria)
```

---

## 📋 Tecnologías

- **Frontend**: HTML5, Tailwind CSS, JavaScript Vanilla, Lucide Icons, Chart.js.
- **Backend / Scraping**: Python 3.11 (`requests`).
- **Hosting**: GitHub Pages.
- **Automatización**: GitHub Actions.
- **Estándares SEO & IA**: XML Sitemaps protocol, `robots.txt`, `llms.txt`.

---

## ⚙️ ¿Cómo funciona la Automatización?

El archivo `.github/workflows/update.yml` está programado para ejecutarse cada hora (`cron: '0 * * * *'`) y realiza las siguientes tareas:

1. Ejecuta `scraper.py`.
2. **BCV Rates**: Consulta la API de `ve.dolarapi.com` para obtener el dólar y euro oficial del Banco Central de Venezuela.
3. **Binance P2P**: Consulta la API pública de anuncios de Binance P2P (USDT/VES) para calcular el promedio de mercado.
4. Genera `data.json` con la información reciente.
5. Actualiza `history.json` agregando o actualizando la entrada del día.
6. Actualiza la fecha de modificación `<lastmod>` en `sitemap.xml`.
7. Si detecta cambios, realiza un `commit` y `push` automático al repositorio, desplegando los nuevos datos en GitHub Pages.

---

## 📊 Fuentes de Datos

- **BCV (Banco Central de Venezuela)**: Obtenido vía [ve.dolarapi.com](https://ve.dolarapi.com/).
- **USDT Binance P2P**: API pública P2P de Binance (Mercado de Venezuela).

---

## 🛠️ Instalación y Ejecución Local

### Prerrequisitos

- Python 3.11+

### Pasos

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/pjgs/TasaVE.git
   cd TasaVE
   ```

2. **Crear e inicializar un entorno virtual (opcional pero recomendado):**
   ```bash
   python -m venv .venv
   # En Windows:
   .venv\Scripts\activate
   # En Linux/macOS:
   source .venv/bin/activate
   ```

3. **Instalar dependencias:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Ejecutar el scraper manualmente:**
   ```bash
   python scraper.py
   ```

5. **Abrir la web:**
   Abre el archivo `index.html` directamente en tu navegador o mediante un servidor local (ej. Live Server en VS Code).

---

## 🔍 Indexación (SEO & LLMs)

- **Google Search Console**: Envía `sitemap.xml` en la sección de Sitemaps de Google Search Console.
- **LLMs / IA**: El archivo `llms.txt` permite que asistentes como ChatGPT, Perplexity y Claude interpreten y citen correctamente las tasas de TasaVe.

---

## ⚠️ Aviso Legal

Los datos mostrados en TasaVe tienen carácter **exclusivamente informativo**. Esta aplicación no representa ni está afiliada al Banco Central de Venezuela ni a ninguna entidad gubernamental. La única tasa oficial de cambio en Venezuela es la publicada por el BCV.

---

## 📝 Licencia

Este proyecto es de código abierto y está disponible bajo uso público con fines informativos.
