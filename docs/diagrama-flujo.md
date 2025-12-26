## Diagrama de flujo – Automatización de respuesta a alertas

```mermaid
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

    J --> K{¿Es falso positivo?}

    L -- Sí --> M[Actualizar estado de alerta]
    M --> Z[Fin]

    L -- No --> N[Generación de playbook dinámico con IA]
    N --> O[Promover alerta a caso]
    P --> Q[Creación automática de tareas]
    Q --> Z[Fin]
