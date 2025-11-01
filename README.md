Guía para Poner en Marcha el Proyecto Multi-Agent LLM App
Voy a ayudarte a poner en marcha este proyecto paso a paso. Es una aplicación full-stack con un backend en Flask/Python usando CrewAI y un frontend en Next.js/React.
📋 Prerrequisitos
Antes de empezar, asegúrate de tener instalado:

Python 3.11.4 (con pyenv recomendado)
Node.js (versión 18 o superior)
npm o yarn

🚀 Instalación y Configuración
1️⃣ Clonar o Descargar el Proyecto
Primero, asegúrate de tener todos los archivos del proyecto en tu máquina local.
2️⃣ Configurar el Backend
Crear el entorno virtual
bash# Navega al directorio raíz del proyecto
cd [nombre-del-proyecto]

# Crea un entorno virtual con Python 3.11.4
pyenv virtualenv 3.11.4 multiagent-env

# Activa el entorno virtual
pyenv activate multiagent-env

# Instala las dependencias desde requirements.txt
pip install -r requirements.txt
Instalar dependencias con Poetry (en el directorio backend)
bash# Ve al directorio backend
cd backend

# Instala las dependencias con Poetry
poetry install --no-root
Configurar las Variables de Entorno
Crea un archivo .env en el directorio backend/ con el siguiente contenido:
env# OpenAI API Key (obligatorio)
OPENAI_API_KEY=tu_clave_api_de_openai

# YouTube API Key (obligatorio para búsquedas de YouTube)
YOUTUBE_API_KEY=tu_clave_api_de_youtube

# Serper API Key (obligatorio para búsquedas en internet)
SERPER_API_KEY=tu_clave_api_de_serper

# LangSmith (opcional, para tracking)
LANGCHAIN_TRACING_V2=true
LANGCHAIN_ENDPOINT=https://api.smith.langchain.com
LANGCHAIN_API_KEY=tu_clave_api_de_langchain
LANGCHAIN_PROJECT=level3multiagent-v1
Obtener las API Keys necesarias:
OpenAI API Key:

Ve a https://platform.openai.com/api-keys
Crea una cuenta o inicia sesión
Genera una nueva API key

YouTube API Key:

Ve a Google Cloud Console
Crea un nuevo proyecto
Ve a "APIs & Services" > "Enable APIs and Services"
Busca y habilita "YouTube Data API v3"
Ve a "Credentials" > "Create Credentials" > "API Key"
Copia la clave generada

Serper API Key:

Ve a https://serper.dev/
Regístrate (es gratis)
Copia tu API key del dashboard

3️⃣ Configurar el Frontend
bash# En una nueva terminal, ve al directorio frontend
cd frontend

# Instala las dependencias exactas del proyecto
npm ci
▶️ Ejecutar la Aplicación
Necesitarás dos terminales abiertas simultáneamente:
Terminal 1: Backend
bash# Asegúrate de estar en el directorio backend
cd backend

# Activa el entorno virtual si no lo está
pyenv activate multiagent-env

# Ejecuta el servidor Flask
python api.py
```

Deberías ver algo como:
```
* Running on http://127.0.0.1:3001
Terminal 2: Frontend
bash# En una segunda terminal, ve al directorio frontend
cd frontend

# Ejecuta el servidor de desarrollo de Next.js
npm run dev
```

Deberías ver algo como:
```
ready - started server on 0.0.0.0:3000
🌐 Usar la Aplicación

Abre tu navegador en http://localhost:3000
Verás dos secciones de entrada:

Technologies: Añade tecnologías (ej: "Generative AI")
Business Areas: Añade áreas de negocio (ej: "Customer Service")


Haz clic en el botón "Start" para iniciar la búsqueda
Los agentes de IA comenzarán a buscar artículos de blog y videos de YouTube
Los resultados aparecerán en la sección de salida, y el log de eventos mostrará el progreso

🔧 Solución de Problemas Comunes
Error: "Module not found"

Asegúrate de haber ejecutado pip install -r requirements.txt y poetry install --no-root en el backend
Asegúrate de haber ejecutado npm ci en el frontend

Error: "Invalid API Key"

Verifica que todas las API keys en el archivo .env sean correctas
Asegúrate de que el archivo .env esté en el directorio backend/

Error: CORS

El backend ya tiene CORS configurado, pero si hay problemas, verifica que la línea CORS(app, resources={r"/api/*": {"origins": "*"}}) esté en api.py

El backend se queda "pensando" mucho tiempo

Es normal, las aplicaciones multi-agente con LLMs pueden tardar varios minutos
Revisa el log en la terminal del backend para ver el progreso
Puede costar aproximadamente $0.20 por ejecución usando GPT-4

📝 Notas Importantes
⚠️ Costos: Esta aplicación usa GPT-4 y puede generar costos en tu cuenta de OpenAI. Ten cuidado con el uso intensivo.
⚠️ Tiempo de ejecución: Una búsqueda completa puede tardar 2-5 minutos dependiendo de la complejidad.
⚠️ API Limits: Respeta los límites de las APIs (YouTube, Serper, OpenAI) para evitar bloqueos.
🎯 Ejemplo de Uso
Prueba con estos valores para verificar que funciona:

Technology: "Generative AI"
Business Area: "Marketing"

La aplicación buscará 3 artículos de blog y 3 videos de YouTube relacionados con Generative AI en Marketing.