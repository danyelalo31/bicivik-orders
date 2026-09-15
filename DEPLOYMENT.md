# 🚀 Guía de Deployment

Esta guía te ayudará a desplegar tu aplicación Bicivik Orders a producción de forma **GRATUITA**.

## 📋 Opciones de Deployment

### Opción 1: Railway.app (Backend + Base de Datos) ⭐ RECOMENDADO

Railway es la opción más fácil con plan gratuito generoso (hasta $5/mes).

#### Pasos:

1. **Crear cuenta en Railway**
   - Ir a https://railway.app
   - Crear cuenta con GitHub/Email
   - Confirmar email

2. **Crear nuevo proyecto**
   - Click en "New Project"
   - Seleccionar "Deploy from GitHub repo"
   - Conectar repositorio de GitHub

3. **Agregar PostgreSQL**
   - En el proyecto, click "Add"
   - Seleccionar "PostgreSQL"
   - Click "Deploy"

4. **Agregar servicio Node.js**
   - Click "Add"
   - Seleccionar "GitHub Repo"
   - Seleccionar tu repositorio
   - Configurar:
     - **Root Directory:** `backend`
     - **Start Command:** `npm install && npm run db:init && npm run db:seed && npm start`

5. **Configurar variables de entorno**
   - En el servicio Node.js, ir a Variables
   - Agregar las siguientes:
     ```
     NODE_ENV=production
     PORT=3000
     JWT_SECRET=tu_clave_super_secreta_aqui_minimo_32_caracteres
     JWT_EXPIRE=30d
     CORS_ORIGIN=https://tu-dominio-frontend.vercel.app
     ```
   - La variable `DATABASE_URL` se crea automáticamente desde PostgreSQL

6. **Obtener URL del backend**
   - Railway asigna automáticamente un dominio como `https://tu-app-prod-xxx.railway.app`
   - Copiar esta URL

### Opción 2: Render.com (Backend + Base de Datos)

Alternativa a Railway con plan gratuito.

#### Pasos rápidos:

1. Crear cuenta en https://render.com
2. Crear servicio PostgreSQL (Base de Datos)
3. Crear servicio Web (Node.js) desde GitHub
4. Configurar variables de entorno
5. Deploy automático

### Opción 3: Heroku (Backend + Base de Datos)

**Nota:** Heroku ya no ofrece plan gratuito. Solo usar si tienes créditos.

---

## 🌐 Vercel.app (Frontend)

Vercel es **100% GRATUITO** para static sites y tiene excelente rendimiento.

#### Pasos:

1. **Crear cuenta en Vercel**
   - Ir a https://vercel.com
   - Crear cuenta con GitHub/Email

2. **Importar repositorio**
   - Click "New Project"
   - Seleccionar tu repositorio de GitHub
   - Click "Import"

3. **Configurar proyecto**
   - **Framework:** Vite
   - **Root Directory:** `frontend`
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`

4. **Configurar variables de entorno**
   - En Project Settings → Environment Variables
   - Agregar:
     ```
     VITE_API_URL=https://tu-app-prod-xxx.railway.app/api
     ```
   (Reemplazar con la URL real de tu backend en Railway)

5. **Deploy**
   - Click "Deploy"
   - Vercel desplegará automáticamente cada vez que hagas push a `main`

6. **Tu sitio estará en:**
   - https://bicivik-orders.vercel.app (o similar)

---

## 🔄 Flujo de Deployment Completo

### Primer Deploy:

```bash
# 1. Push tu código a GitHub
git push origin main

# 2. Railway desplegará automáticamente el backend
#    - Crea la BD
#    - Corre db:init y db:seed
#    - Inicia el servidor

# 3. Vercel desplegará automáticamente el frontend
#    - Compila el código React
#    - Publica en CDN global

# 4. ¡Tu app está viva en internet!
```

### Para futuros cambios:

Solo haz push a GitHub y ambas plataformas desplegarán automáticamente:

```bash
git add .
git commit -m "Fix: descripción de cambios"
git push origin main
```

---

## 🔑 Variables de Entorno por Ambiente

### Development (Local)

**Backend (.env):**
```
NODE_ENV=development
PORT=5000
DATABASE_URL=postgresql://postgres:postgres@localhost:5432/bicivik_orders
JWT_SECRET=tu_clave_local_cambiar_en_prod
JWT_EXPIRE=7d
CORS_ORIGIN=http://localhost:5173
```

**Frontend (.env):**
```
VITE_API_URL=http://localhost:5000/api
```

### Production (Railway + Vercel)

**Backend (Railway):**
```
NODE_ENV=production
PORT=3000
DATABASE_URL=postgresql://user:pass@host:5432/db  # Auto-generado
JWT_SECRET=clave_super_secreta_de_32_caracteres_minimo
JWT_EXPIRE=30d
CORS_ORIGIN=https://bicivik-orders.vercel.app
```

**Frontend (Vercel):**
```
VITE_API_URL=https://tu-app-prod-xxx.railway.app/api
```

---

## 📊 Costos Estimados

| Servicio | Plan Gratuito | Límite |
|----------|---------------|--------|
| **Railway Backend** | $5/mes incluidos | 500GB/mes egress |
| **Railway PostgreSQL** | Incluido | 10GB |
| **Vercel Frontend** | $0 | Ilimitado |
| **Total Mensual** | **$0** - **$5** | ✅ Perfecto para pequeñas empresas |

---

## 🐛 Troubleshooting

### Error: "Cannot find module 'pg'"
```bash
cd backend
npm install
npm start
```

### Error: "Connection refused to database"
- Verificar que PostgreSQL está corriendo localmente
- O esperar a que Railway termine de desplegar

### Error: "CORS blocked"
- Asegúrate que `CORS_ORIGIN` en Railway coincida con tu URL de Vercel
- Ejemplo: Si tu frontend está en `https://my-app.vercel.app`, la variable debe ser exactamente eso

### Error: "Token inválido"
- Cambiar `JWT_SECRET` en todas partes puede invalidar tokens existentes
- Solo cambiarla en desarrollo, nunca en producción (a menos que fuerces logout de todos)

---

## 🔐 Checklist Pre-Producción

- [ ] Cambiar `JWT_SECRET` a una cadena aleatoria larga
- [ ] Revisar `CORS_ORIGIN` en backend
- [ ] Cambiar contraseña de PostgreSQL
- [ ] Eliminar usuarios de prueba o cambiar sus contraseñas
- [ ] Activar HTTPS (automático en Railway y Vercel)
- [ ] Hacer backup de la base de datos
- [ ] Configurar alertas en Railway
- [ ] Probar flujo completo en producción

---

## 📞 Soporte

- **Railway Docs:** https://docs.railway.app
- **Vercel Docs:** https://vercel.com/docs
- **PostgreSQL:** https://www.postgresql.org/docs

---

**¡Listo! Tu aplicación está desplegada y accesible desde cualquier lugar del mundo.** 🌍🎉
