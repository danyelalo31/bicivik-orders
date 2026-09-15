# 🚴 Bicivik - Sistema de Gestión de Pedidos Entre Sucursales

Sistema web para gestionar pedidos entre sucursales con trazabilidad completa, múltiples usuarios y hosting económico.

## 📦 Estructura del Proyecto

```
bicivik-orders/
├── backend/              # API REST (Node.js + Express)
├── frontend/             # Aplicación web (React + Vite)
├── docker-compose.yml    # Para desarrollo local
└── README.md
```

## 🚀 Inicio Rápido

### Opción 1: Desarrollo Local

**Requisitos:**
- Node.js 18+
- PostgreSQL 14+
- Git

**Pasos:**

```bash
# 1. Clonar y entrar al directorio
git clone <tu-repo>
cd bicivik-orders

# 2. Instalar dependencias del backend
cd backend
npm install

# 3. Configurar variables de entorno
cp .env.example .env
# Editar .env con tus datos

# 4. Crear base de datos e inicializar
npm run db:init
npm run db:seed

# 5. Iniciar servidor backend
npm run dev

# En otra terminal - Frontend
cd ../frontend
npm install
npm run dev
```

**Base de datos local:**
```bash
# Con Docker Compose
docker-compose up -d

# Sin Docker (asumiendo PostgreSQL instalado)
psql -U postgres -c "CREATE DATABASE bicivik_orders;"
```

### Opción 2: Deployment a Producción (Gratuito)

#### Backend + Base de datos en Railway.app

1. Crear cuenta en [railway.app](https://railway.app)
2. Conectar repositorio GitHub
3. Agregar servicio PostgreSQL
4. Agregar servicio Node.js
5. Configurar variables de entorno
6. Deploy automático

#### Frontend en Vercel

1. Crear cuenta en [vercel.com](https://vercel.com)
2. Importar repositorio
3. Configurar `VITE_API_URL` apuntando a Railway backend
4. Deploy automático en cada push

## 🗄️ Estructura de Base de Datos

### Tablas principales

```sql
-- Usuarios (con sucursal asignada)
-- Sucursales
-- Productos
-- Pedidos
-- Detalles de pedidos (items)
-- Historial/Auditoría
```

## 🔐 Autenticación

- Sistema de login por usuario
- JWT para sesiones
- Roles: Admin, Gerente, Operario
- Permisos por sucursal

## 📊 Funcionalidades

### Dashboard
- Resumen de pedidos: Pendientes, en tránsito, entregados, cerrados
- Gráficos de actividad
- Filtros por sucursal, estado, fecha

### Gestión de Pedidos
- Crear pedido (seleccionar sucursal origen/destino, productos, cantidad)
- Actualizar estado del pedido
- Agregar observaciones
- Ver historial completo

### Reportes
- Pedidos por período
- Trazabilidad completa
- Exportar a Excel

## 🌐 Variables de Entorno

### Backend (.env)
```
NODE_ENV=development
PORT=5000
DATABASE_URL=postgresql://user:password@localhost:5432/bicivik_orders
JWT_SECRET=tu_clave_secretas_aqui
JWT_EXPIRE=7d
CORS_ORIGIN=http://localhost:5173
```

### Frontend (.env)
```
VITE_API_URL=http://localhost:5000/api
```

## 📚 Documentación Adicional

- [API Documentation](./docs/API.md)
- [Database Schema](./docs/DATABASE.md)
- [User Guide](./docs/USER_GUIDE.md)

## 🤝 Contribuir

Las contribuciones son bienvenidas. Por favor:

1. Crear un branch para tu feature
2. Hacer commit de tus cambios
3. Push al branch
4. Abrir Pull Request

## 📄 Licencia

MIT

## 📞 Soporte

Para reportar problemas o sugerencias, crear un issue en GitHub.

---

**Versión:** 1.0.0  
**Última actualización:** 2026-09-15
