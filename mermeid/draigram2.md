
````mermaid
%%{init: {'theme': 'forest', 'sequence': {'diagramMarginX': 10, 'diagramMarginY': 10, 'actorMargin': 50, 'width': 150, 'height': 60, 'orientation': 'vertical'}}}%%
sequenceDiagram
    participant Usuario
    participant OnPremise
    participant Nube
    participant Microservicio

    Microservicio->>Nube: 14. Guardar Pesos
    Usuario->>OnPremise: 15. Iniciar Traducción
    OnPremise->>Nube: 16. Descargar Pesos
    OnPremise->>OnPremise: 17. Capturar Frames
    OnPremise->>OnPremise: 18. Predecir Palabra (Modelo local)
    OnPremise->>OnPremise: 19. Generar Audio (Text-to-Speech)
    OnPremise->>Usuario: 20. Mostrar Palabra/Reproducir Audio

    Note right of Nube: Almacenamiento (S3)
    Note left of OnPremise: Programa de Muestreo y Traducción
    Note right of Microservicio: Procesamiento y Entrenamiento

````