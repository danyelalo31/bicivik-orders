# 🤝 Guía de Contribución

¡Gracias por querer contribuir a Bicivik Orders!

## 📋 Antes de Empezar

1. Fork el repositorio
2. Clonar tu fork
3. Crear una rama para tu feature: `git checkout -b feature/nombre-feature`
4. Seguir las convenciones de código del proyecto

## 💻 Desarrollo

### Setup Local

```bash
npm install --prefix backend
npm install --prefix frontend
npm run db:init --prefix backend
npm run db:seed --prefix backend
```

### Estructura del Proyecto

```
backend/
├── src/
│   ├── config/       # Configuración (BD, etc)
│   ├── middleware/   # Middleware (auth, errores, logs)
│   ├── routes/       # Rutas API
│   └── scripts/      # Scripts de BD

frontend/
├── src/
│   ├── components/   # Componentes reutilizables
│   ├── pages/        # Páginas principales
│   ├── utils/        # Funciones auxiliares
│   └── styles/       # CSS
```

## 📝 Convenciones de Código

### Commits

Usar formato convencional:
```
feat: agregar nueva característica
fix: corregir bug
docs: actualizar documentación
style: cambios de formato
refactor: refactorizar código
test: agregar tests
chore: tareas de mantenimiento
```

### Ejemplos:
```
feat: agregar filtro de status a pedidos
fix: corregir validación de email en login
docs: mejorar instrucciones de deployment
```

### Git Workflow

```bash
# 1. Actualizar main
git checkout main
git pull origin main

# 2. Crear rama para feature
git checkout -b feat/mi-feature

# 3. Hacer cambios
# ... editar archivos ...

# 4. Commit
git add .
git commit -m "feat: descripción clara del cambio"

# 5. Push
git push origin feat/mi-feature

# 6. Crear Pull Request en GitHub
# - Título descriptivo
# - Descripción de cambios
# - Referencia a issues (Closes #123)
```

## 🧪 Testing

Antes de hacer commit, probar:

### Backend
```bash
cd backend
npm run dev
# Probar endpoints con curl o Postman
```

### Frontend
```bash
cd frontend
npm run dev
# Probar en http://localhost:5173
```

## 🔍 Code Review

Los maintainers revisarán tu PR y pueden:
- Sugerir cambios
- Pedir más tests
- Solicitar refactorización

Todos estamos aquí para mejorar juntos. ¡Sé respetuoso y abierto a feedback!

## 📖 Documentación

Si agregas features nuevas, actualizar:
- `README.md` - Si es importante
- `docs/API.md` - Si es un endpoint
- Comentarios en el código

## 🐛 Reportar Bugs

Crear un issue con:
- Descripción clara del bug
- Pasos para reproducir
- Comportamiento esperado
- Screenshot (si aplica)

## ✨ Sugerir Features

Crear un issue con:
- Descripción de la feature
- Caso de uso
- Beneficios

## 📋 Checklist Antes de Submit

- [ ] Código sigue convenciones del proyecto
- [ ] No hay console.log() en producción
- [ ] Cambios están bien documentados
- [ ] Commits tienen mensajes descriptivos
- [ ] PR tiene descripción clara

## 🎓 Recursos

- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)
- [React Best Practices](https://react.dev/learn)
- [PostgreSQL Docs](https://www.postgresql.org/docs/)

---

¡Gracias por contribuir! 🙌
