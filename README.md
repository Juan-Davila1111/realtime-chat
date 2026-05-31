# 💬 Aplicación de Chat en Tiempo Real con Persistencia

## 📌 Descripción

Aplicación de mensajería en tiempo real que permite a múltiples usuarios comunicarse mediante salas de chat. Todos los mensajes son almacenados de forma persistente en una base de datos para conservar el historial de conversaciones.

El objetivo es proporcionar una experiencia rápida, segura y escalable utilizando WebSockets para la comunicación en tiempo real y una base de datos relacional para la persistencia de datos.

---

## 🚀 Características

### Comunicación en tiempo real
- Envío y recepción instantánea de mensajes.
- Actualización automática de conversaciones.
- Gestión de conexiones y desconexiones.

### Persistencia de mensajes
- Almacenamiento permanente de conversaciones.
- Recuperación del historial al ingresar a una sala.
- Conservación de datos tras reinicios del servidor.

### Gestión de usuarios
- Registro e inicio de sesión.
- Autenticación mediante JWT.
- Gestión de perfiles.

### Salas de chat
- Creación de salas públicas y privadas.
- Unión y salida de salas.
- Historial independiente por sala.

### Escalabilidad
- Soporte para múltiples instancias.
- Integración con Redis para sincronización de eventos.
- Arquitectura preparada para despliegues distribuidos.

---

## 🏗️ Arquitectura

```text
Cliente (React/Vue)
        │
        │ WebSocket
        ▼
Servidor (Node.js + Socket.IO)
        │
 ┌──────┴──────┐
 ▼             ▼
Redis      PostgreSQL
Eventos    Persistencia
```

---

## 🛠️ Stack Tecnológico

### Frontend
- React
- TypeScript
- Tailwind CSS
- Socket.IO Client

### Backend
- Node.js
- Express
- TypeScript
- Socket.IO

### Base de Datos
- PostgreSQL
- Prisma ORM

### Infraestructura
- Docker
- Redis
- Nginx

---

## 📂 Estructura del Proyecto

```text
chat-app/
│
├── client/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   ├── services/
│   │   └── socket/
│   └── public/
│
├── server/
│   ├── src/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── socket/
│   │   └── database/
│   │
│   └── prisma/
│
├── docker/
├── docs/
└── README.md
```

---

## 🗄️ Modelo de Datos

### Usuario

```json
{
  "id": "uuid",
  "username": "usuario",
  "email": "usuario@email.com",
  "createdAt": "2026-01-01T00:00:00Z"
}
```

### Sala

```json
{
  "id": "uuid",
  "name": "general",
  "createdAt": "2026-01-01T00:00:00Z"
}
```

### Mensaje

```json
{
  "id": "uuid",
  "content": "Hola mundo",
  "userId": "uuid",
  "roomId": "uuid",
  "createdAt": "2026-01-01T00:00:00Z"
}
```

---

## 🔌 Eventos WebSocket

### Cliente → Servidor

#### Unirse a una sala

```json
{
  "event": "join_room",
  "payload": {
    "roomId": "room-123"
  }
}
```

#### Enviar mensaje

```json
{
  "event": "send_message",
  "payload": {
    "roomId": "room-123",
    "message": "Hola a todos"
  }
}
```

### Servidor → Cliente

#### Nuevo mensaje

```json
{
  "event": "new_message",
  "payload": {
    "id": "msg-123",
    "roomId": "room-123",
    "username": "Juan",
    "message": "Hola a todos",
    "timestamp": "2026-01-01T10:00:00Z"
  }
}
```

#### Usuario conectado

```json
{
  "event": "user_joined",
  "payload": {
    "username": "Juan"
  }
}
```

---

## ⚙️ Variables de Entorno

```env
PORT=3000

DATABASE_URL=postgresql://user:password@localhost:5432/chatdb

JWT_SECRET=your_secret_key

REDIS_HOST=localhost
REDIS_PORT=6379
```

---

## ▶️ Instalación

### Clonar repositorio

```bash
git clone https://github.com/tu-organizacion/chat-app.git
cd chat-app
```

### Instalar dependencias del backend

```bash
cd server
npm install
```

### Ejecutar migraciones

```bash
npx prisma migrate dev
```

### Iniciar backend

```bash
npm run dev
```

### Iniciar frontend

```bash
cd ../client
npm install
npm run dev
```

---

## 🐳 Docker

### Ejecutar todos los servicios

```bash
docker-compose up -d
```

### Detener servicios

```bash
docker-compose down
```

---

## 🔒 Seguridad

- Autenticación JWT.
- Validación de entradas.
- Protección contra spam.
- Rate Limiting.
- Sanitización de mensajes.
- Conexiones seguras mediante HTTPS.

---

## 🧪 Testing

### Ejecutar pruebas

```bash
npm run test
```

### Ver cobertura

```bash
npm run test:coverage
```

---

## 📈 Mejoras Futuras

- Mensajes privados.
- Indicador de escritura.
- Confirmaciones de lectura.
- Compartir archivos e imágenes.
- Notificaciones push.
- Moderación de salas.
- Búsqueda avanzada de mensajes.
- Reacciones y emojis.

---

## 🤝 Contribuciones

1. Crear una rama:

```bash
git checkout -b feature/nueva-funcionalidad
```

2. Realizar cambios:

```bash
git commit -m "feat: nueva funcionalidad"
```

3. Subir cambios:

```bash
git push origin feature/nueva-funcionalidad
```

4. Abrir un Pull Request.

---

## 📄 Licencia

Este proyecto está licenciado bajo la licencia MIT.

---

## 👨‍💻 Autor

Desarrollado como una solución de mensajería en tiempo real con persistencia de datos, escalabilidad y buenas prácticas de arquitectura de software.
