# 🏥 Caso 3 — Sistema de Gestión de Citas Médicas

Sistema web para la gestión de citas médicas. Permite administrar pacientes, especialidades y citas con una relación muchos a muchos.

---

## 🗂️ Estructura del Proyecto

```
C3citas_medicas/
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
| `pacientes` | Datos de los pacientes |
| `especialidades` | Especialidades médicas disponibles |
| `citas` | Relación muchos a muchos entre pacientes y especialidades |

### Endpoints

#### Autenticación
| Método | Ruta | Descripción |
|---|---|---|
| POST | `/api/auth/registro` | Registrar nuevo usuario |
| POST | `/api/auth/login` | Iniciar sesión → devuelve JWT |
| GET | `/api/auth/perfil` | Perfil del usuario autenticado |

#### Pacientes 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/pacientes` | Listar todos |
| GET | `/api/pacientes/:id` | Obtener uno |
| POST | `/api/pacientes` | Crear |
| PUT | `/api/pacientes/:id` | Actualizar |
| DELETE | `/api/pacientes/:id` | Eliminar |

#### Especialidades 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/especialidades` | Listar todas |
| GET | `/api/especialidades/:id` | Obtener una |
| POST | `/api/especialidades` | Crear |
| PUT | `/api/especialidades/:id` | Actualizar |
| DELETE | `/api/especialidades/:id` | Eliminar |

#### Citas 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/citas` | Listar todas |
| GET | `/api/citas/:id` | Obtener una |
| POST | `/api/citas` | Crear |
| PUT | `/api/citas/:id` | Actualizar |
| DELETE | `/api/citas/:id` | Eliminar |

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
# Corre en http://localhost:3001
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
- **Pacientes** — CRUD completo
- **Especialidades** — CRUD completo
- **Citas** — CRUD con relación paciente-especialidad

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
2. Framework preset: **Vite**
