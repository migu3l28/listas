# Task List 26

## Descripción del proyecto

Task List 26 es una aplicación web básica creada con Django 6.0.5 que permite visualizar tareas existentes y acceder a la información detallada de cada una. El proyecto está diseñado como un ejemplo sencillo de un gestor de tareas con:

- Lista de tareas
- Detalle de cada tarea
- Modelo de datos `Task` con campos de título, descripción, estado de completado y timestamps
- Rutas limpias para la lista y los detalles
- Plantillas HTML con herencia de `base.html`
- Uso de archivos estáticos CSS

## Características principales

- Página principal (`/`): muestra la lista de tareas disponibles
- Página de detalle de tarea (`/tareas/<id>/`): muestra título, fecha de creación y descripción
- Administración de Django disponible en `/admin/`
- Base de datos SQLite local (`db.sqlite3`)

## Requisitos

- Python 3.11 (o compatible con Django 6.0.5)
- Virtualenv / entornos virtuales recomendados
- Dependencias listadas en `requirements.txt`

## Dependencias

El proyecto utiliza las siguientes librerías:

- Django==6.0.5
- asgiref==3.11.1
- sqlparse==0.5.5
- tzdata==2026.2

## Instalación y configuración

1. Abrir una terminal en la carpeta raíz del proyecto:

```bash
cd "c:\Users\lefsky\Desktop\Curso Programacion\task_list26"
```

2. Crear y activar un entorno virtual (recomendado):

```bash
python -m venv .venv
.venv\Scripts\Activate.ps1
```

3. Instalar las dependencias:

```bash
pip install -r requirements.txt
```

4. Ejecutar migraciones de la base de datos:

```bash
python manage.py migrate
```

5. Crear un superusuario para acceder al panel de administración (opcional):

```bash
python manage.py createsuperuser
```

## Ejecución del proyecto

Para iniciar el servidor de desarrollo de Django:

```bash
python manage.py runserver
```

Después, abrir en el navegador:

- Lista de tareas: `http://127.0.0.1:8000/`
- Panel de admin: `http://127.0.0.1:8000/admin/`

## Estructura del proyecto

```
./
├── base_project/         # Configuración principal de Django
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── tasks/                # Aplicación de tareas
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── migrations/           # Migraciones de la base de datos
│   └── 0001_initial.py
├── templates/            # Plantillas HTML del proyecto
│   ├── base.html
│   ├── task-detail.html
│   └── tasks_list.html
├── static/               # Archivos estáticos
│   └── css/style.css
├── db.sqlite3            # Base de datos SQLite local
├── manage.py             # Script de administración de Django
├── requirements.txt      # Dependencias del proyecto
└── README.md             # Documentación del proyecto
```

## Descripción de la aplicación `tasks`

La aplicación `tasks` incluye:

- Modelo `Task`:
  - `title` (CharField)
  - `description` (TextField)
  - `completed` (BooleanField)
  - `created_at` (DateTimeField auto creado)
  - `updated_at` (DateTimeField auto actualizado)
- Vista `TaskListView`: muestra todas las tareas con enlace al detalle
- Vista `TaskDetailView`: muestra los detalles de una tarea específica
- URLs definidas en `tasks/urls.py`

## Plantillas y estáticos

- `templates/base.html`: formato base compartido por todas las páginas
- `templates/tasks_list.html`: lista de tareas con enlaces a detalles
- `templates/task-detail.html`: detalle de cada tarea
- `static/css/style.css`: estilos personalizados para la aplicación

## Notas adicionales

- El proyecto está configurado para uso local con `DEBUG = True`.
- Para producción, es necesario ajustar `DEBUG`, `ALLOWED_HOSTS`, `SECRET_KEY` y los archivos estáticos.
- Si la base de datos `db.sqlite3` ya existe, no es necesario crearla de nuevo, solo ejecutar las migraciones.

## Buenas prácticas sugeridas

- Usar un entorno virtual para separar dependencias.
- No subir `db.sqlite3` ni el `SECRET_KEY` real a repositorios públicos en proyectos en producción.
- Usar `gitignore` para excluir `.venv/` y otros archivos locales si se comparte el proyecto.
