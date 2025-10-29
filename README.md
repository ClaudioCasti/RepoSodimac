# RepoSodimac
Claro, aquí tienes la versión del README.md sin emojis, con un tono completamente profesional.

Agente Funcional de Asistencia al Cliente para Sodimac
Este proyecto implementa un agente de inteligencia artificial autónomo diseñado para modernizar la atención al cliente de Sodimac. El agente utiliza un Modelo de Lenguaje Grande (LLM) orquestado por el framework LangChain Agents para comprender, planificar y ejecutar tareas complejas, yendo más allá de un simple sistema de preguntas y respuestas.

La solución combina una base de conocimiento interna (mediante RAG) con herramientas de acceso a información externa y memoria conversacional para ofrecer una asistencia dinámica, contextual y eficiente.

Características Principales
Razonamiento y Planificación (ReAct): El agente puede descomponer una pregunta compleja en una secuencia de pasos lógicos para resolverla.

Consulta de Base de Conocimiento Interna: Utiliza un pipeline RAG para responder preguntas específicas sobre productos, manuales y políticas de Sodimac con alta precisión, basándose en documentos internos.

Acceso a Información Externa: Integra una herramienta de búsqueda web para obtener datos en tiempo real, como precios de la competencia, tendencias o especificaciones de productos no catalogados.

Memoria Conversacional: Recuerda el contexto de la conversación, permitiendo preguntas de seguimiento y un diálogo mucho más natural y fluido.

Ejecución de Tareas: Puede realizar acciones concretas, como generar y guardar resúmenes o comparativas en archivos de texto.

Arquitectura de la Solución
El sistema se basa en un agente conversacional de tipo ReAct (Reasoning and Acting). El Agent Executor de LangChain actúa como el cerebro central, coordinando el LLM, la memoria y un conjunto de herramientas para formular un plan y ejecutarlo.

[Aquí puedes insertar tu diagrama de orquestación como una imagen]


Estructura del Proyecto
agente-sodimac/
├── src/
│   ├── agent_main.py         # Script principal para ejecutar el agente
│   ├── tools.py              # Definición de herramientas personalizadas (RAG)
│   └── data_ingestion.py     # Script para procesar documentos y crear la BD de vectores
├── data/
│   └── (documentos.pdf)      # Carpeta para los PDFs de Sodimac
├── vector_db/
│   └── (faiss_index)         # Almacenamiento del índice vectorial de FAISS
├── .env                      # Archivo para las claves de API (debe ser creado)
├── requirements.txt          # Lista de dependencias de Python
└── README.md                 # Esta documentación
Instalación y Configuración
Sigue estos pasos para poner en funcionamiento el agente en tu entorno local.

1. Prerrequisitos
Python 3.9 o superior.

Git.

2. Clonar el Repositorio
Bash

git clone https://github.com/[TU_USUARIO_GITHUB]/agente-sodimac.git
cd agente-sodimac
3. Configurar el Entorno
Se recomienda encarecidamente utilizar un entorno virtual para gestionar las dependencias.

Bash

# Crear un entorno virtual
python -m venv venv

# Activar el entorno virtual
# En Windows:
venv\Scripts\activate
# En macOS/Linux:
source venv/bin/activate
4. Instalar Dependencias
Bash

pip install -r requirements.txt
5. Configurar las Claves de API
Crea un archivo llamado .env en la raíz del proyecto y añade tus claves de API. Necesitarás acceso a un proveedor de LLMs (como Hugging Face) y a una API de búsqueda web (como SerpApi de Google).

Ini, TOML

# Ejemplo de archivo .env
HUGGINGFACEHUB_API_TOKEN="hf_xxxxxxxxxxxxxxxxxxxx"
SERPAPI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
Nota: Nunca compartas este archivo ni subas tus claves de API a un repositorio público. El archivo .gitignore debe contener una línea que diga .env.

Modo de Uso
Paso 1: Ingesta de Datos (Ejecutar solo una vez)
Antes de iniciar el agente por primera vez, debes procesar los documentos de Sodimac para crear la base de conocimiento vectorial.

Añade tus archivos PDF a la carpeta /data.

Ejecuta el siguiente comando en tu terminal:

Bash

python src/data_ingestion.py
Este script leerá los documentos, los procesará y creará un índice FAISS en la carpeta /vector_db.

Paso 2: Iniciar el Agente Interactivo
Una vez creada la base de datos, puedes iniciar el agente para empezar a conversar.

Bash

python src/agent_main.py
El agente te saludará y podrás comenzar a hacerle preguntas. Para finalizar la sesión, simplemente escribe salir.

Ejemplos de Interacción
Consulta simple (usa la herramienta RAG)
Tú: ¿Cuál es la política de devoluciones para herramientas eléctricas?

Consulta con memoria (recuerda el contexto)
Tú: ¿Y aplica lo mismo si el empaque está dañado?

Tarea compleja (requiere múltiples herramientas y planificación)
Tú: Compara el taladro Bauker de 18V de nuestro catálogo con el modelo equivalente de Makita que encuentres en el mercado y guarda un resumen en un archivo llamado comparativa.txt.

Tecnologías Utilizadas
Lenguaje: Python

Orquestación de IA: LangChain

Modelos de Lenguaje: Hugging Face Hub (configurable)

Base de Datos Vectorial: FAISS

Embeddings: SentenceTransformers (Hugging Face)

Búsqueda Web: SerpApi (Google Search)
