# Definir un LimitRange con valores restringidos

Establece límites bajos para los siguientes recursos para forzar ajustes en la aplicación:

1. Crear un nuevo proyecto de laboratorio  
2. Crear un LimitRange con valores restringidos  
3. Crear una aplicación sin recursos explícitos  
4. Asignar recursos por encima del límite  
5. Monitorear el comportamiento de la aplicación con los recursos asignados  

## Tabla de rangos y valores

| Tipo de valor       | CPU (m)       | Memoria (Mi)      |
|---------------------|---------------|-------------------|
| **Min (mínimo)**    | 100m          | 128Mi             |
| **Max (máximo)**    | 500m          | 512Mi             |
| **Default**         | 250m          | 256Mi             |
| **Default Request** | 200m          | 200Mi             |
| **Valores prohibidos** | > 500m      | > 512Mi           |
| **Valores válidos manuales** | 300m–500m | 256Mi–512Mi     |

---
