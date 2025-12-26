flowchart LR
    A[Inicio del workflow] --> B[Recepción de alerta desde TheHive]

    B --> C[Extracción de hash del artefacto]
    C --> D{¿El hash existe?}

    D -- Sí --> E[Aplicar playbook predefinido]
    E --> F[Promover alerta a caso]
    F --> G[Crear tarea manual]
    G --> Z[Fin]

    D -- No --> H[Consulta a VirusTotal]
    H --> I[Análisis automatizado mediante IA]

    I --> J{¿Es falso positivo?}

    J -- Sí --> K[Actualizar estado de la alerta]
    K --> Z[Fin]

    J -- No --> L[Generación de playbook dinámico con IA]
    L --> M[Promover alerta a caso]
    M --> N[Creación automática de tareas]
    N --> Z[Fin]
