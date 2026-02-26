# 📚 Caso 1 — Sistema de Gestión de Matrículas

Sistema web para la gestión de matrículas académicas. Permite administrar estudiantes, materias y matrículas con una relación muchos a muchos.

---

## 🗂️ Estructura del Proyecto

```
C1sistema-matriculas/
├── backend/     → API REST con Node.js + Express + MongoDB
└── frontend/    → SPA con React + Vite
```

---

## ⚙️ Backend

### Tecnologías
- Node.js + Express 4
- MongoDB Atlas + Mongoose
- JWT para autenticación
- Desplegado en Vercel (Serverless)

### Colecciones MongoDB
| Colección | Descripción |
|---|---|
| `usuarios` | Usuarios del sistema |
| `estudiantes` | Datos de los estudiantes |
| `materias` | Materias disponibles |
| `matriculas` | Relación muchos a muchos entre estudiantes y materias |

### Endpoints

#### Autenticación
| Método | Ruta | Descripción |
|---|---|---|
| POST | `/api/auth/registro` | Registrar nuevo usuario |
| POST | `/api/auth/login` | Iniciar sesión → devuelve JWT |
| GET | `/api/auth/perfil` | Perfil del usuario autenticado |

#### Estudiantes 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/estudiantes` | Listar todos |
| GET | `/api/estudiantes/:id` | Obtener uno |
| POST | `/api/estudiantes` | Crear |
| PUT | `/api/estudiantes/:id` | Actualizar |
| DELETE | `/api/estudiantes/:id` | Eliminar |

#### Materias 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/materias` | Listar todas |
| GET | `/api/materias/:id` | Obtener una |
| POST | `/api/materias` | Crear |
| PUT | `/api/materias/:id` | Actualizar |
| DELETE | `/api/materias/:id` | Eliminar |

#### Matrículas 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/matriculas` | Listar todas |
| GET | `/api/matriculas/:id` | Obtener una |
| POST | `/api/matriculas` | Crear |
| PUT | `/api/matriculas/:id` | Actualizar |
| POST | `/api/matriculas/:id/materias` | Agregar materia |
| DELETE | `/api/matriculas/:id/materias/:idMateria` | Quitar materia |
| DELETE | `/api/matriculas/:id` | Eliminar |

> 🔒 Requieren header: `Authorization: Bearer <token>`

### Variables de Entorno (backend)
```env
MONGODB_URI=mongodb+srv://...
JWT_SECRET=tu_clave_secreta
NODE_ENV=production
```

### Instalación local
```bash
cd backend
npm install
npm run dev
# Corre en http://localhost:3000
```

---

## 🖥️ Frontend

### Tecnologías
- React 18 + Vite
- React Router DOM
- Axios
- Desplegado en Vercel

### Módulos
- **Login** — autenticación con JWT
- **Estudiantes** — CRUD completo
- **Materias** — CRUD completo
- **Matrículas** — CRUD + gestión de materias inscritas

### Variables de Entorno (frontend)
```env
VITE_API_URL=https://tu-backend.vercel.app/api
```

### Instalación local
```bash
cd frontend
npm install
npm run dev
# Corre en http://localhost:5173
```

---

## 🚀 Despliegue en Vercel

### Backend
1. Importar carpeta `backend` en Vercel
2. Agregar variables de entorno: `MONGODB_URI`, `JWT_SECRET`, `NODE_ENV=production`
3. Vercel detecta automáticamente el `vercel.json`

### Frontend
1. Importar carpeta `frontend` en Vercel
2. Agregar variable de entorno: `VITE_API_URL=https://url-del-backend.vercel.app/api`
3. Framework preset: **Vite**
