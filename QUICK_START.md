# ⚡ Quick Start - Bicivik Orders

Comienza en 5 minutos.

## 🎯 Requisitos

- Node.js 18+
- PostgreSQL 14+ (o Docker)
- Git

## 🚀 Desarrollo Local (Sin Docker)

### 1️⃣ Clonar y preparar

```bash
# Clonar repositorio
git clone <tu-repo> bicivik-orders
cd bicivik-orders

# Instalar dependencias
npm install --prefix backend
npm install --prefix frontend
```

### 2️⃣ Base de datos

**Opción A: PostgreSQL local**
```bash
# En PostgreSQL CLI
psql -U postgres
CREATE DATABASE bicivik_orders;
\q
```

**Opción B: Docker (más fácil)**
```bash
docker run --name postgres_bicivik \
  -e POSTGRES_PASSWORD=postgres \
  -e POSTGRES_DB=bicivik_orders \
  -p 5432:5432 \
  -d postgres:15-alpine
```

### 3️⃣ Configurar variables de entorno

**Backend:**
```bash
cp backend/.env.example backend/.env
# Editar backend/.env (déjalo como está para desarrollo)
```

**Frontend:**
```bash
cp frontend/.env.example frontend/.env
# Editar frontend/.env (déjalo como está para desarrollo)
```

### 4️⃣ Inicializar base de datos

```bash
cd backend
npm run db:init      # Crear tablas
npm run db:seed      # Agregar datos de prueba
```

### 5️⃣ Iniciar los servidores

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
# ✅ Servidor en http://localhost:5000
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
# ✅ App en http://localhost:5173
```

### 6️⃣ Login

- **Email:** admin@bicivik.com
- **Contraseña:** password123

---

## 🐳 Con Docker Compose (Más Fácil)

```bash
# Asegúrate de tener Docker instalado

# Iniciar todo
docker-compose up

# En otra terminal, inicializar BD
docker-compose exec backend npm run db:init
docker-compose exec backend npm run db:seed

# Acceder
# Frontend: http://localhost:5173
# Backend: http://localhost:5000/api
```

---

## 📚 Usuarios de Prueba

```
admin@bicivik.com / password123 (Admin)
gerente1@bicivik.com / password123 (Gerente)
operario1@bicivik.com / password123 (Operario)
```

---

## 🚀 Deploy a Producción

Ver [DEPLOYMENT.md](./DEPLOYMENT.md) para instrucciones paso a paso.

**Resumen rápido:**
1. Railway para backend + BD (gratuito)
2. Vercel para frontend (gratuito)

---

## 📖 Documentación

- [README.md](./README.md) - Descripción general
- [DEPLOYMENT.md](./DEPLOYMENT.md) - Desplegar a producción
- [docs/API.md](./docs/API.md) - Documentación API REST

---

## 🐛 Troubleshooting

### Error: "Cannot connect to database"
```bash
# Verificar que PostgreSQL está corriendo
psql -U postgres -c "SELECT version();"

# Si no está instalado
brew install postgresql  # macOS
sudo apt-get install postgresql  # Ubuntu
choco install postgresql  # Windows
```

### Error: "Port 5000 already in use"
```bash
# Cambiar puerto en backend/.env
PORT=5001
```

### Error: "Cannot find node_modules"
```bash
npm install --prefix backend
npm install --prefix frontend
```

---

## 💡 Próximos Pasos

1. ✅ Explorar la app en desarrollo
2. ✅ Revisar [docs/API.md](./docs/API.md)
3. ✅ Crear pedidos y probar funcionalidades
4. ✅ Cuando esté listo, seguir [DEPLOYMENT.md](./DEPLOYMENT.md)

---

**¿Preguntas?** Ver documentación en `docs/` o crear un issue en GitHub.

Happy coding! 🎉
