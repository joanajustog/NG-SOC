flowchart TD
    A([Inicio]) --> B[Creacion del fichero de prueba EICAR en el endpoint]
    B --> C[Wazuh Agent detecta evento de fichero creado\nRegla 554: File added to the system]
    C --> D[Calculo de hashes del fichero\nMD5, SHA1, SHA256]
    D --> E[Envio de datos al modulo de integracion Wazuh-MISP]
    E --> F[Consulta automatica a MISP con los hashes]
    F --> G{Coincide con IOC en MISP}
    
    G -- No --> H[Registrar evento sin correlacion\nCriticidad normal]
    H --> Z([Fin])

    G -- Si --> I[Generar alerta correlada en Wazuh\nRegla 100802: MISP file hash matched\nCriticidad alta]
    I --> J[Envio de alerta a TheHive]
    J --> K[Creacion de alerta/incidente en TheHive]
    K --> L[Adjuntar observable: hash del fichero]
    L --> M[Incluir contexto del endpoint afectado]
    M --> N[Priorizacion del incidente para triage]
    N --> Z([Fin])
