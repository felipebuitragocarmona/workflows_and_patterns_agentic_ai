# IA agéntica: flujos de trabajo y patrones

Colección de ejemplos en Python para aprender a construir flujos de trabajo y
patrones de agentes con la API de Google Gemini. Cada archivo presenta un
concepto de forma independiente y utiliza casos sencillos para mostrar su
funcionamiento.

## Contenido

```text
.
├── module_1/
│   ├── i_workflows/
│   │   ├── i_PromptChaining.py       # Encadenamiento de prompts
│   │   ├── ii_PromptRouter.py        # Enrutamiento según la consulta
│   │   └── iii_Parallelization.py    # Ejecución concurrente y agregación
│   └── ii_patterns/
│       ├── i_react.py                # Generación, evaluación y reflexión
│       ├── ii_tools.py               # Uso de herramientas (function calling)
│       ├── iii_planning.py           # Planificación con salida estructurada
│       └── iv_multiagent.py          # Handoff entre agentes especializados
└── slides/
    └── i_Introducción_v01.pptx       # Material introductorio
```

## Requisitos

- Python 3.10 o superior
- Una clave de API de Google Gemini
- Los paquetes `google-genai` y `pydantic`

## Instalación

Se recomienda crear un entorno virtual:

```bash
python -m venv .venv
```

Actívalo en Windows (PowerShell):

```powershell
.\.venv\Scripts\Activate.ps1
```

En macOS o Linux:

```bash
source .venv/bin/activate
```

Instala las dependencias:

```bash
pip install google-genai pydantic
```

## Configuración

Define la variable de entorno `GEMINI_API_KEY` antes de ejecutar los ejemplos.

En PowerShell:

```powershell
$env:GEMINI_API_KEY="tu_clave_de_api"
```

En macOS o Linux:

```bash
export GEMINI_API_KEY="tu_clave_de_api"
```

No guardes la clave directamente en el código ni la incluyas en el repositorio.

## Ejecución

Ejecuta cualquier ejemplo desde la raíz del proyecto:

```bash
python module_1/i_workflows/i_PromptChaining.py
python module_1/i_workflows/ii_PromptRouter.py
python module_1/ii_patterns/i_react.py
python module_1/ii_patterns/ii_tools.py
python module_1/ii_patterns/iii_planning.py
python module_1/ii_patterns/iv_multiagent.py
```

El archivo `iii_Parallelization.py` contiene `await` en el nivel superior, por
lo que está pensado para ejecutarse en un entorno interactivo compatible, como
Jupyter Notebook. Si se utiliza como script de Python, la llamada final debe
envolverse con `asyncio.run()`:

```python
result = asyncio.run(parallel_tasks())
print(f"\n--- Aggregated Summary ---\n{result}")
```

## Conceptos demostrados

- **Prompt chaining:** utiliza la salida de una llamada como entrada de la
  siguiente.
- **Routing:** clasifica una consulta mediante una salida estructurada y la
  envía al flujo apropiado.
- **Parallelization:** ejecuta varias solicitudes de manera concurrente y
  combina sus resultados.
- **Reflection:** evalúa una respuesta y la mejora de forma iterativa.
- **Tool use:** permite que el modelo solicite la ejecución de una función
  definida por la aplicación.
- **Planning:** genera un plan tipado y asigna cada paso a un rol.
- **Multi-agent handoff:** transfiere una solicitud entre agentes
  especializados.

## Consideraciones

- Las llamadas a Gemini consumen cuota de la API.
- Algunos nombres de modelos usados en los ejemplos son versiones *preview* y
  podrían dejar de estar disponibles. Sustitúyelos por un modelo compatible si
  la API devuelve un error.
- La función meteorológica de `ii_tools.py` es una simulación y siempre devuelve
  un valor fijo; no consulta un servicio meteorológico real.

## Licencia

Este repositorio no incluye actualmente una licencia. Añade una antes de
distribuir o reutilizar el contenido fuera de su contexto educativo.
