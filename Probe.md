# Laboratorio: Liveness y Readiness Probes en OpenShift

Este laboratorio tiene como objetivo mostrar cómo configurar y validar probes de salud para una aplicación basada en Apache HTTP Server (`httpd`) utilizando la consola web de OpenShift.

---

## Pasos del laboratorio

### Crear un nuevo proyecto

1. Inicia sesión en la consola web de OpenShift.
2. En el menú izquierdo, ve a **"Home" > "Projects"**.
3. Haz clic en **"Create Project"**.
4. Ingresa un nombre como:  
   `liveness-lab`
5. Haz clic en **"Create"**.

---

### Crear una aplicación con la imagen `httpd`

1. Dentro del proyecto `liveness-lab`, ve a **"Developer"** > **"Add"**.
2. Selecciona **"Container Image"**.
3. En el campo *Image Name*, escribe:  
   `httpd`
4. Verifica que el runtime sea detectado correctamente (puede mostrar "Apache HTTP Server").
5. En *Application Name*, puedes usar: `apache-app`
6. En *Name*, usa por ejemplo: `httpd`
7. Haz clic en **"Create"**.

---

### Agregar Liveness y Readiness Probes

1. Ve a la sección **"Workloads" > "Deployments"**.
2. Selecciona el deployment `httpd`.
3. Haz clic en la pestaña **"Actions" > "Edit Health Checks"**.
4. Configura la **Liveness Probe**:
   - Tipo: **HTTP GET**
   - Ruta: `/`  
   - Puerto: `8080` o el que esté expuesto (puede ser `80`)
   - Inicial delay: `10` segundos
   - Periodicidad: `10` segundos
5. Configura la **Readiness Probe** con valores similares:
   - Ruta: `/`  
   - Puerto: `8080` o `80`
   - Inicial delay: `5` segundos
   - Periodicidad: `10` segundos
6. Haz clic en **"Save"**.

---

### Validar el comportamiento

1. Ve a **"Pods"** en el proyecto.
2. Selecciona el pod en ejecución de la aplicación.
3. Abre la pestaña **"Logs"** o **"Events"** para ver si hay reinicios o fallos de la probe.
4. Puedes probar fallos intencionales modificando la imagen o la ruta del probe (ejemplo: `/invalid`).

---

## Resultado esperado

- Si las probes están correctamente configuradas, el pod debe mostrarse como *Running* y *Ready*.
- Si introduces rutas incorrectas o delays demasiado bajos, verás reinicios por fallos en las probes.

---

## Notas

- La imagen `httpd` sirve contenido en `/` por defecto en el puerto `80`, así que normalmente basta con usar esa configuración.
- Asegúrate de que las rutas estén bien definidas y que el contenedor haya arrancado completamente antes de que las probes inicien (usa el delay correctamente).

