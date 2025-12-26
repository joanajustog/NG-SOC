## Diagrama de flujo – Automatización de respuesta a alertas

```mermaid
flowchart TD
    A([Inicio]) --> B[Recepcion de alerta en TheHive]
    B --> C[Extraccion de indicadores: hash del artefacto]
    C --> D{Se dispone de hash}

    D -- No --> E[Aplicacion de playbook predefinido]
    E --> F[Promocion de alerta a caso en TheHive]
    F --> G[Creacion de tarea inicial de investigacion]
    G --> H[Ejecucion de accion automatica de contencion: eliminacion del fichero]
    H --> I{Accion ejecutada correctamente}
    I -- Si --> J[Actualizar caso: Incidente confirmado - True Positive]
    I -- No --> J2[Actualizar caso: Revision requerida - Accion fallida]
    J --> Z([Fin])
    J2 --> Z

    D -- Si --> K[Enriquecimiento mediante VirusTotal]
    K --> L[Analisis automatizado mediante IA]
    L --> M{Clasificado como falso positivo}

    M -- Si --> N[Actualizar alerta: False Positive]
    N --> Z

    M -- No --> O[Generacion de playbook dinamico mediante IA]
    O --> P[Promocion de alerta a caso en TheHive]
    P --> Q[Creacion automatica de tareas de respuesta]
    Q --> Z


