# Todo API con TypeScript, Express y PostgreSQL

Una API REST para gestión de tareas (todos) construida con TypeScript, Express.js y PostgreSQL, configurada con Docker Compose.

## 🚀 Características

- API REST completa para gestión de tareas
- Base de datos PostgreSQL con Docker
- TypeScript para tipado estático
- Migraciones de base de datos
- Endpoints para CRUD completo

## 📋 Prerrequisitos

- Node.js (versión 16 o superior)
- Docker y Docker Compose
- Git

## 🛠️ Instalación

1. **Clonar el repositorio**
   ```bash
   git clone <url-del-repositorio>
   cd ts-express-postgres
   ```

2. **Instalar dependencias**
   ```bash
   npm install
   ```

3. **Configurar variables de entorno**
   Crear un archivo `.env` en la raíz del proyecto:
   ```env
   DATABASE_URL=postgresql://appuser:supersecret_dev@localhost:5432/appdb
   PORT=3000
   ```

4. **Iniciar la base de datos**
   ```bash
   docker-compose up -d
   ```

5. **Ejecutar migraciones**
   ```bash
   npm run db:migrate
   ```

6. **Iniciar la aplicación**
   ```bash
   npm run dev
   ```

## 📚 Scripts disponibles

- `npm run dev` - Inicia la aplicación en modo desarrollo
- `npm run build` - Compila TypeScript a JavaScript
- `npm start` - Inicia la aplicación compilada
- `npm run db:migrate` - Ejecuta las migraciones de la base de datos

## 🔗 Endpoints de la API

### Base URL: `http://localhost:3000`

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/health` | Verificar estado de la aplicación |
| GET | `/todos` | Obtener todas las tareas |
| POST | `/todos` | Crear una nueva tarea |
| GET | `/todos/:id` | Obtener una tarea específica |
| PUT | `/todos/:id` | Actualizar una tarea |
| DELETE | `/todos/:id` | Eliminar una tarea |

## 📝 Ejemplos de uso

### Crear una tarea
```bash
curl -X POST http://localhost:3000/todos \
  -H "Content-Type: application/json" \
  -d '{"title": "Mi primera tarea"}'
```

### Obtener todas las tareas
```bash
curl http://localhost:3000/todos
```

### Actualizar una tarea
```bash
curl -X PUT http://localhost:3000/todos/1 \
  -H "Content-Type: application/json" \
  -d '{"title": "Tarea actualizada", "done": true}'
```

### Eliminar una tarea
```bash
curl -X DELETE http://localhost:3000/todos/1
```

## 🗄️ Estructura de la base de datos

La tabla `todos` tiene la siguiente estructura:

```sql
CREATE TABLE todos (
  id SERIAL PRIMARY KEY,
  title TEXT NOT NULL,
  done BOOLEAN NOT NULL DEFAULT false,
  created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);
```

## 🏗️ Estructura del proyecto

```
ts-express-postgres/
├── src/
│   ├── app.ts              # Configuración de Express
│   ├── db.ts               # Configuración de PostgreSQL
│   ├── index.ts            # Punto de entrada
│   └── todos/
│       ├── todo.model.ts   # Modelo de datos
│       ├── todo.routes.ts  # Rutas de la API
│       └── todo.service.ts # Lógica de negocio
├── scripts/
│   └── migrate.ts          # Script de migración
├── docker-compose.yml      # Configuración de Docker
├── package.json
├── tsconfig.json
└── README.md
```

## 🐳 Docker

El proyecto incluye un `docker-compose.yml` que configura:
- PostgreSQL 16 Alpine
- Puerto 5432 expuesto
- Volumen persistente para datos
- Health check para la base de datos

## 🤝 Contribuir

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para detalles.

## 👨‍💻 Autor

Desarrollado en clase como ejemplo de API REST con TypeScript, Express y PostgreSQL.