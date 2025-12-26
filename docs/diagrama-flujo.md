## Diagrama de flujo – Automatización de respuesta a alertas

```mermaid
flowchart TD
    A([▶ Inicio]) --> B[[🛡️ TheHive<br/>Recepción de alerta]]

    B --> C[🔍 Extracción de hash<br/>del artefacto]
    C --> D{❓ ¿Existe hash?}

    %% Rama SIN hash (playbook predefinido)
    D -- ❌ No --> E[📘 Playbook<br/>predefinido]
    E --> F[📂 Promover alerta<br/>a caso]
    F --> G[📝 Crear tarea]
    G --> H[💻 Ejecutar comando<br/>automático]
    H --> I{🔎 ¿Condición cumplida?}
    I --> J[🔄 Actualizar caso]
    J --> Z([⏹ Fin])

    %% Rama CON hash (enriquecimiento)
    D -- ✅ Sí --> K[🌐 Consulta a<br/>VirusTotal]
    K --> L[🤖 Análisis<br/>automatizado con IA]

    L --> M{⚖️ ¿Falso positivo?}

    M -- ✅ Sí --> N[🔄 Actualizar estado<br/>de la alerta]
    N --> Z

    M -- ❌ No --> O[🧠 Playbook dinámico<br/>generado por IA]
    O --> P[📂 Promover alerta<br/>a caso]
    P --> Q[⚙️ Crear tareas<br/>automáticas]
    Q --> Z
