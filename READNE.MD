```mermaid
graph TD
    A([Inicio: Necesidad de Material en Obra]) --> B[Consultar Fecha Requerida en Carta Gantt]
    B --> C[Calcular días de anticipación de la solicitud]
    C --> D{¿Se solicita con un mínimo<br>de 10 días de anticipación?}
    
    %% Camino Regular (Cumple el plazo)
    D -- SÍ --> E[Generar Solicitud de Material Estándar]
    E --> F[Enviar a Adquisiciones / Logística]
    F --> G[Revisar solicitudes de compra]
    G --> H[Gestión de Compra y Emisión de OC]
    
    %% Logística de Retiro en Proveedor
    H --> H1[Camión asiste a buscar material donde el Proveedor]
    H1 --> H2[Chofer revisa la carga contra la OC]
    H2 --> H3{¿Carga coincide<br>exacto con la OC?}
    
    H3 -- NO --> H4[Exigir corrección de carga al Proveedor]
    H4 --> H1
    
    H3 -- SÍ --> H5[Chofer inicia traslado a Terreno y avisa a Obra]
    H5 --> I[Recepción de Material en Obra]
    
    %% Control y Validación en Terreno
    I --> IX{¿Quien recibe valida que llegue<br>todo lo que dice la OC?}
    IX -- SÍ --> R([Fin: Material Entregado y Conforme])
    
    %% CICLO DE RECLAMO A PROVEEDOR (Modificado)
    IX -- NO --> ALERTA[Aviso inmediato a Oficina Central / Adquisiciones]
    ALERTA --> RESP[Adquisiciones asume el caso y gestiona solución con el Proveedor]
    RESP --> SOL{¿Se resolvió el problema<br>y llegó el faltante?}
    
    SOL -- SÍ --> R
    SOL -- NO --> RESP[Insistir / Reclamar nuevamente al Proveedor]
    
    %% Camino de Urgencia Interno (No cumple el plazo de obra)
    D -- NO --> J[Generar Solicitud con Alerta de Urgencia]
    J --> K[Residente justifica el retraso]
    K --> M{¿Aprobación Especial<br>por Jefatura/Gerencia?}
    
    M -- SÍ --> F
    M -- NO --> O[Rechazo de Solicitud / Reprogramar Actividad en Gantt]
    
    O --> P([Fin: Proceso Detenido])

%% --- CONFIGURACIÓN DE ESTILOS ---
    style D fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    style H3 fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    style IX fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    style M fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    style SOL fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    
    style R fill:#d5e8d4,stroke:#82b366,stroke-width:2px
    
    style ALERTA fill:#f8cecc,stroke:#b85450,stroke-width:2px
    style RESP fill:#f8cecc,stroke:#b85450,stroke-width:2px1px
    style M fill:#f5f5f5,stroke:#666666,stroke-width:1px
