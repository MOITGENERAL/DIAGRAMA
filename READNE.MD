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

%% --- CONFIGURACIÓN DE ESTILOS Y COLORES ---
    
    %% Estilo para Decisiones / Rombos (Amarillo/Naranja suave)
    style D fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    style K fill:#fff2cc,stroke:#d6b656,stroke-width:2px

    %% Estilo para el flujo Estándar / Éxito (Verde/Azul claro)
    style E fill:#dae8fc,stroke:#6c8ebf,stroke-width:1px
    style F fill:#dae8fc,stroke:#6c8ebf,stroke-width:1px
    style G fill:#dae8fc,stroke:#6c8ebf,stroke-width:1px
    style H fill:#d5e8d4,stroke:#82b366,stroke-width:2px
    style N fill:#d5e8d4,stroke:#82b366,stroke-width:2px

    %% Estilo para el flujo de Urgencia / Alerta (Rojo/Rosa claro)
    style I fill:#f8cecc,stroke:#b85450,stroke-width:1px
    style J fill:#f8cecc,stroke:#b85450,stroke-width:1px
    style L fill:#f5f5f5,stroke:#666666,stroke-width:1px
    style M fill:#f5f5f5,stroke:#666666,stroke-width:1px
