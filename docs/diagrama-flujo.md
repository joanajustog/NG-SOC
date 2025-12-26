## Diagrama de flujo – Automatización de respuesta a alertas

```mermaid
flowchart TD
    A([Inicio]) --> B[Recepción de alerta en TheHive]
    B --> C[Extracción de indicadores (hash del artefacto)]
    C --> D{¿Se dispone de hash?}

    %% Rama SIN hash: tratamiento genérico
    D -- No --> E[Aplicación de playbook predefinido]
    E --> F[Promoción de alerta a caso en TheHive]
    F --> G[Creación de tarea inicial de investigación]
    G --> H[Ejecución de acción automática de contención<br/>(p. ej., eliminación del fichero)]
    H --> I{¿Acción ejecutada correctamente?}
    I -- Sí --> J[Actualización del caso: Incidente confirmado (True Positive)]
    I -- No --> J2[Actualización del caso: Revisión requerida (Acción fallida)]
    J --> Z([Fin])
    J2 --> Z

    %% Rama CON hash: enriquecimiento y decisión
    D -- Sí --> K[Enriquecimiento mediante VirusTotal]
    K --> L[Análisis automatizado mediante IA (contextualización y decisión)]
    L --> M{¿Clasificado como falso positivo?}

    M -- Sí --> N[Actualización de la alerta: Falso positivo (False Positive)]
    N --> Z

    M -- No --> O[Generación de playbook dinámico mediante IA]
    O --> P[Promoción de alerta a caso en TheHive]
    P --> Q[Creación automática de tareas de respuesta]
    Q --> Z

