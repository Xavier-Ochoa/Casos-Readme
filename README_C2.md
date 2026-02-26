# 🚗 Caso 2 — Sistema de Gestión de Renta de Carros

Sistema web para la gestión de renta de vehículos. Permite administrar clientes, vehículos y reservas con una relación muchos a muchos.

---

## 🗂️ Estructura del Proyecto

```
C2renta_carros/
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
| `clientes` | Datos de los clientes |
| `vehiculos` | Vehículos disponibles para renta |
| `reservas` | Relación muchos a muchos entre clientes y vehículos |

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

#### Vehículos 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/vehiculos` | Listar todos |
| GET | `/api/vehiculos/:id` | Obtener uno |
| POST | `/api/vehiculos` | Crear |
| PUT | `/api/vehiculos/:id` | Actualizar |
| DELETE | `/api/vehiculos/:id` | Eliminar |

#### Reservas 🔒
| Método | Ruta | Descripción |
|---|---|---|
| GET | `/api/reservas` | Listar todas |
| GET | `/api/reservas/:id` | Obtener una |
| POST | `/api/reservas` | Crear |
| PUT | `/api/reservas/:id` | Actualizar |
| DELETE | `/api/reservas/:id` | Eliminar |

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
- **Vehículos** — CRUD completo
- **Reservas** — CRUD con relación cliente-vehículo

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
