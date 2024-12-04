
````mermaid
%%{init: {'theme': 'forest', 'sequence': {'diagramMarginX': 10, 'diagramMarginY': 10, 'actorMargin': 50, 'width': 150, 'height': 60, 'orientation': 'vertical'}}}%%
sequenceDiagram
participant Usuario
participant OnPremise
participant Nube
participant Microservicio

    Usuario->>OnPremise: 1. Iniciar Grabación/Toma de Fotos
    OnPremise->>OnPremise: 2. Capturar Video/Fotos
    OnPremise->>OnPremise: 3. Dividir en Frames
    OnPremise->>OnPremise: 4. Almacenar Frames (local)
    OnPremise->>Nube: 5. Subir Frames a S3
    Nube->>Nube: 6. EventBridge (Notificación)
    Nube->>Nube: 7. Invocar Lambda
    Nube->>Nube: 8. Obtener Frames de S3
    Nube->>Nube: 9. Enviar URLs a SQS
    Nube->>Microservicio: 10. Recibir URLs de SQS
    Microservicio->>Nube: 11. Descargar Frames de S3
    Microservicio->>Microservicio: 12. Procesar Frames (MediaPipe)
    Microservicio->>Microservicio: 13. Entrenar Modelo
````