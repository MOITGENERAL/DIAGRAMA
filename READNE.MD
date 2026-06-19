```mermaid
graph TD
    A([Inicio: Necesidad de Material en Obra]) --> B[Consultar Fecha Requerida en Carta Gantt]
    B --> C[Calcular días de anticipación de la solicitud]
    C --> D{¿Se solicita con un mínimo<br>de 10 días de anticipación?}
    
    %% Camino Regular (Cumple el plazo)
    D -- SÍ --> E[Generar Solicitud de Material Estándar]
    E --> F[Enviar a Adquisiciones / Logística]
    F --> G[Gestión de Compra y Programación de Despacho]
    G --> H[Recepción de Material en Obra]
    
    %% Camino de Urgencia (No cumple el plazo)
    D -- NO --> I[Generar Solicitud con Alerta de Urgencia]
    I --> J[Residente justifica el retraso]
    J --> K{¿Aprobación Especial<br>por Jefatura/Gerencia?}
    
    K -- SÍ --> F
    K -- NO --> L[Rechazo de Solicitud / Reprogramar Actividad en Gantt]
    
    L --> M([Fin: Proceso Detenido])
    H --> N([Fin: Material Entregado])

    style D fill:#f9f,stroke:#333,stroke-width:2px
    style K fill:#f9f,stroke:#333,stroke-width:2px
    style I fill:#ffcccb,stroke:#f00,stroke-width:1px
