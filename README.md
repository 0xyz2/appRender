# API de Gestión de Tareas con Flask

Esta es una API REST para gestionar una lista de tareas con Flask.

## Métodos Disponibles

### 1. GET /tasks
**Descripción:** Obtiene todas las tareas

**Ejemplo:**
```bash
curl http://localhost:5000/tasks
```

**Respuesta:**
```json
[
  {
    "id": 1,
    "title": "Hacer compras",
    "description": "Comprar leche y pan",
    "completed": false
  }
]
```

---

### 2. GET /tasks/<id>
**Descripción:** Obtiene una tarea específica por su ID

**Ejemplo:**
```bash
curl http://localhost:5000/tasks/1
```

**Respuesta:**
```json
{
  "id": 1,
  "title": "Hacer compras",
  "description": "Comprar leche y pan",
  "completed": false
}
```

---

### 3. POST /tasks
**Descripción:** Crea una nueva tarea

**Ejemplo:**
```bash
curl -X POST http://localhost:5000/tasks \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Hacer compras",
    "description": "Comprar leche y pan",
    "completed": false
  }'
```

**Parámetros JSON:**
- `title` (string, requerido): Título de la tarea
- `description` (string, opcional): Descripción de la tarea
- `completed` (boolean, opcional): Estado de completación (default: false)

**Respuesta:**
```json
{
  "id": 1,
  "title": "Hacer compras",
  "description": "Comprar leche y pan",
  "completed": false
}
```

---

### 4. PUT /tasks/<id>
**Descripción:** Actualiza una tarea existente

**Ejemplo:**
```bash
curl -X PUT http://localhost:5000/tasks/1 \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Hacer compras actualizado",
    "completed": true
  }'
```

**Parámetros JSON:**
- `title` (string, opcional): Nuevo título de la tarea
- `description` (string, opcional): Nueva descripción
- `completed` (boolean, opcional): Nuevo estado

**Respuesta:**
```json
{
  "id": 1,
  "title": "Hacer compras actualizado",
  "description": "Comprar leche y pan",
  "completed": true
}
```

---

### 5. DELETE /tasks/<id>
**Descripción:** Elimina una tarea

**Ejemplo:**
```bash
curl -X DELETE http://localhost:5000/tasks/1
```

**Respuesta:**
```json
{
  "mensaje": "Tarea con ID 1 eliminada correctamente"
}
```

---

## Cómo Ejecutar

### 1. Activar el ambiente virtual
```bash
# En Windows (PowerShell)
.\env\Scripts\Activate.ps1

# En Windows (CMD)
env\Scripts\activate.bat

# En MacOS/Linux
source env/bin/activate
```

### 2. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 3. Ejecutar la aplicación
```bash
python app.py
```

La API estará disponible en `http://localhost:5000`

---

## Códigos de Respuesta HTTP

- **200 OK:** Solicitud exitosa
- **201 Created:** Recurso creado exitosamente
- **400 Bad Request:** Error en la solicitud (datos inválidos)
- **404 Not Found:** Tarea no encontrada

---

## Notas

- Las tareas se almacenan en memoria, por lo que se perderán al reiniciar la aplicación
- El ID se asigna automáticamente de forma incremental
- El servidor corre en modo debug por defecto para facilitar el desarrollo
