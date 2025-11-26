📘 Agente Sodimac — Asistente Inteligente con RAG y Observabilidad

Este proyecto implementa un Agente de Asistencia al Cliente para Sodimac basado en técnicas modernas de IA generativa, LangChain, RAG, y un sistema de orquestación de herramientas, orientado a brindar respuestas precisas, rápidas y contextualizadas sobre productos, políticas y servicios de la empresa.

El agente también incorpora observabilidad, trazabilidad, y un scaffolding modular que facilita su mantenimiento, monitoreo y escalabilidad.

🚀 Características Principales
✔️ 1. Razonamiento y Planificación (ReAct)

El agente utiliza el patrón ReAct (Reasoning + Acting) para resolver problemas complejos combinando razonamiento lógico, acceso al conocimiento interno y ejecución de herramientas.

✔️ 2. RAG – Base de Conocimiento Interna

Utiliza un pipeline Retrieval-Augmented Generation para responder consultas basadas en documentos reales de Sodimac:

manuales

políticas de devolución

especificaciones de productos

información interna cargada en vector stores

✔️ 3. Acceso a Información Externa

Incluye una herramienta opcional de búsqueda web para complementar información con datos en tiempo real:

precios de mercado

especificaciones externas

comparativas de productos

✔️ 4. Memoria Conversacional

Guarda el contexto de las interacciones para permitir:

seguimiento natural de la conversación

aclaraciones

preguntas dependientes de respuestas anteriores

✔️ 5. Ejecución de Tareas

El agente puede:

generar archivos .txt

hacer comparativas

resumir documentos

consultar bases vectoriales

realizar acciones autónomas planificadas

🧠 Arquitectura General de la Solución

La arquitectura se basa en un Agente ReAct orquestado por LangChain:

Usuario → LLM → Agente ReAct → Herramientas (RAG, Web, Memoria) → Respuesta Inteligente


El AgentExecutor coordina:

el LLM

el razonamiento paso a paso

el acceso a herramientas (Tools)

la memoria de conversación

y los componentes RAG

👉 Aquí puedes agregar tu diagrama de orquestación.

🗂️ Estructura del Proyecto
agente-sodimac/
├── src/
│   ├── agent_main.py           # Script principal del agente interactivo
│   ├── tools.py                # Herramientas personalizadas (RAG + WebSearch)
│   ├── data_ingestion.py       # Construcción del Vector Store
│   ├── agent/
│   │   └── sodimac_agent.py    # Lógica del agente con LangChain ReAct y RAG
│   ├── ingestion/
│   │   └── ingest.py           # Script scaffold para generar embeddings y BD
│   ├── memory/                 # Módulo para memoria conversacional
│   └── utils/                  # Funciones auxiliares
├── data/
│   └── *.pdf                   # Documentos internos de Sodimac
├── vector_db/
│   └── faiss_index             # Base vectorial generada
├── documents/                  # Documentos .txt para ingestión inicial (scaffold)
├── requirements.txt            
├── .env.example                
├── .env                        # Variables de entorno (NO se sube a GitHub)
└── README.md                   # Documentación del proyecto

⚙️ Instalación y Configuración
🔧 Prerrequisitos

Python 3.9+

Git

🔽 1. Clonar el Repositorio
git clone https://github.com/[TU_USUARIO_GITHUB]/agente-sodimac.git
cd agente-sodimac

🧬 2. Crear Entorno Virtual
python -m venv venv


Activar:

Windows:

venv\Scripts\activate


Mac/Linux:

source venv/bin/activate

📦 3. Instalar Dependencias
pip install -r requirements.txt

🔐 4. Configurar Variables de Entorno

Crear archivo .env en la raíz:

HUGGINGFACEHUB_API_TOKEN="hf_xxxxxxxxxxxxx"
SERPAPI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxx"
OPENAI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxx"


⚠️ Nunca subas este archivo a GitHub.

📥 Modo de Uso
Paso 1 — Ingesta de Datos

(Se realiza solo la primera vez)

Colocar PDFs en /data
Luego ejecutar:

python src/data_ingestion.py


Esto:

procesa documentos

genera embeddings

crea el índice FAISS o Chroma

Paso 2 — Ejecutar el Agente Interactivo
python src/agent_main.py


Luego puedes preguntar:

¿Cuál es la política de devoluciones?
¿Puedo devolver un producto sin boleta?
Compara este taladro con otro del mercado.

💬 Ejemplos de Interacción
❓ Consulta RAG

Tú:

¿Cuál es la política de devoluciones para herramientas eléctricas?

🧠 Pregunta con memoria

Tú:

¿Y aplica lo mismo si el empaque está dañado?

🛠️ Tarea Compleja (ReAct + RAG + WebSearch)

Tú:

Compara el taladro Bauker 18V con el Makita equivalente y guarda un resumen en comparativa.txt.

🧩 Tecnologías Utilizadas
Componente	Tecnología
LLM	Hugging Face / OpenAI
Agente	LangChain Agents
RAG	ChromaDB / FAISS + SentenceTransformers
Embeddings	OpenAI Embeddings
API	FastAPI + Uvicorn
Observabilidad	Logs + Métricas + Trazas
Web Search	SerpAPI
🧪 Análisis del Script de Scaffolding (Evaluación 3)

El archivo scaffold_agente_sodimac_evaluacion3.py genera automáticamente una estructura profesional de proyecto.

Puntos Clave del Análisis:
✔️ 1. Crea una estructura modular completa

Incluye carpetas como:

/agent

/tools

/memory

/ingestion

/utils

/documents

/tests

✔️ 2. Genera archivos esenciales

requirements.txt

.env.example

README.md

scripts listos para:

ingestión RAG

interacción RAG

exposición como API

✔️ 3. Implementa RAG completo

Incluye:

chunking con RecursiveCharacterTextSplitter

embeddings mediante OpenAIEmbeddings

almacenamiento persistente con ChromaDB

retrieval configurado (k=5)

cadena RAG lista (RetrievalQA.from_chain_type)

✔️ 4. API completa con FastAPI

Incluye endpoint:

POST /query


Para consultar usando:

agent.answer_question(query)

🏁 Conclusión

Este proyecto combina:

IA generativa

RAG profesional

agentes autónomos ReAct

observabilidad

buenas prácticas de ingeniería de software
