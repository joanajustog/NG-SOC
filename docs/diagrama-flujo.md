flowchart TD
    A([▶ Inicio]) --> B[[🛡️ TheHive<br/>Recepción de alerta]]

    B --> C[🔍 Extracción de hash<br/>del artefacto]
    C --> D{❓ ¿Existe hash?}

    D -- ❌ No --> E[📘 Playbook<br/>predefinido]
    E --> F[📂 Promover alerta<br/>a caso]
    F --> G[📝 Crear tarea<br/>manual]
    G --> Z([⏹ Fin])

    D -- ✅ Sí --> H[🌐 Consulta a<br/>VirusTotal]
    H --> I[🤖 Análisis<br/>automatizado con IA]

    I --> J{⚖️ ¿Falso positivo?}

    J -- ✅ Sí --> K[🔄 Actualizar estado<br/>de la alerta]
    K --> Z

    J -- ❌ No --> L[🧠 Playbook dinámico<br/>generado por IA]
    L --> M[📂 Promover alerta<br/>a caso]
    M --> N[⚙️ Crear tareas<br/>automáticas]
    N --> Z
