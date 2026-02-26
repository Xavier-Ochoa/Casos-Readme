# 🎫 Caso 4 — Sistema de Gestión de Tickets de Asistencia Técnica

Sistema web para la gestión de tickets de soporte técnico. Permite administrar clientes, técnicos y tickets con una relación muchos a muchos.

---

## 🗂️ Estructura del Proyecto

```
C4tickets_asistencia_tecnica/
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
| `clientes` | Datos de los clientes (con campo `dependencia`) |
| `tecnicos` | Técnicos de soporte |
| `tickets` | Relación muchos a muchos entre clientes y técnicos |

### Endpoints

#### Autenticación
| Método | Ruta | Descripción |
|---|---|---|
| POST | `/api/auth/registro` | Registrar nuevo usuario |
| POST | `/api/auth/login` | Iniciar sesión → devuelve JWT |
| GET | `/api/auth/perfil` | Perfil del usuario autenticado |

#### Clientes 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/clientes` | Listar todos |
| GET | `/api/clientes/:id` | Obtener uno |
| POST | `/api/clientes` | Crear |
| PUT | `/api/clientes/:id` | Actualizar |
| DELETE | `/api/clientes/:id` | Eliminar |

#### Técnicos 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/tecnicos` | Listar todos |
| GET | `/api/tecnicos/:id` | Obtener uno |
| POST | `/api/tecnicos` | Crear |
| PUT | `/api/tecnicos/:id` | Actualizar |
| DELETE | `/api/tecnicos/:id` | Eliminar |

#### Tickets 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/tickets` | Listar todos |
| GET | `/api/tickets/:id` | Obtener uno |
| POST | `/api/tickets` | Crear |
| PUT | `/api/tickets/:id` | Actualizar |
| DELETE | `/api/tickets/:id` | Eliminar |

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
- **Clientes** — CRUD completo
- **Técnicos** — CRUD completo
- **Tickets** — CRUD con relación cliente-técnico

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
