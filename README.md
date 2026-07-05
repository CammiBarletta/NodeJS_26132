# API REST — Productos y Autenticación

API REST desarrollada en Node.js con Express, Firebase Firestore y autenticación JWT. Proyecto final del curso de Node.js — Talento Tech.

🔗 **API en vivo:** https://nodejs-26132.onrender.com/

> Nota: al usar el plan gratuito de Render, el servidor puede tardar unos 30-50 segundos en responder la primera petición si estuvo inactivo.

## Tecnologías utilizadas

- Node.js (ESModules)
- Express 5
- Firebase / Firestore
- JSON Web Token (JWT)
- CORS
- Body-parser
- Dotenv

## Arquitectura

El proyecto está organizado en capas:

```
src/
├── routes/         # Definición de endpoints
├── controllers/     # Lógica de request/response
├── services/         # Lógica de negocio
├── models/           # Acceso a datos (Firestore)
├── middleware/       # Autenticación JWT
└── data/              # Configuración de Firebase y generación de tokens
```

## Instalación y uso local

1. Clonar el repositorio

```bash
git clone https://github.com/CammiBarletta/NodeJS_26132.git
cd NodeJS_26132
```

2. Instalar dependencias

```bash
npm install
```

3. Configurar variables de entorno

Crear un archivo `.env` en la raíz con las siguientes variables:

```
apiKey=
authDomain=
projectId=
storageBucket=
messagingSenderId=
appId=
PORT=3000
JWT_SECRET_KEY=
```

4. Correr el proyecto

```bash
npm run start
```

El servidor queda disponible en `http://localhost:3000`

## Endpoints

### Autenticación

| Método | Ruta | Descripción | Body |
|---|---|---|---|
| POST | `/auth/login` | Devuelve un Bearer Token si las credenciales son válidas | `{ "email": "...", "password": "..." }` |

### Productos

| Método | Ruta | Descripción | Protegida |
|---|---|---|---|
| GET | `/api/products` | Lista todos los productos | No |
| GET | `/api/products/:id` | Devuelve un producto por ID | No |
| POST | `/api/products/create` | Crea un nuevo producto | Sí (Bearer Token) |
| PUT | `/api/products/:id` | Actualiza un producto | Sí (Bearer Token) |
| DELETE | `/api/products/:id` | Elimina un producto | Sí (Bearer Token) |

Para las rutas protegidas, incluir el header:

```
Authorization: Bearer <token>
```

## Manejo de errores

| Código | Caso |
|---|---|
| 400 | Petición con datos faltantes o inválidos |
| 401 | Falta el token de autenticación |
| 403 | Token inválido o expirado |
| 404 | Ruta no encontrada o recurso inexistente |
| 500 | Error interno del servidor |

## Ejemplo de uso (con curl)

```bash
# Login
curl -X POST https://nodejs-26132.onrender.com/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@gmail.com","password":"123456"}'

# Obtener productos
curl https://nodejs-26132.onrender.com/api/products

# Crear producto (requiere token del login)
curl -X POST https://nodejs-26132.onrender.com/api/products/create \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer TU_TOKEN" \
  -d '{"producto":{"nombre":"Correa","precio":2500,"categoria":"accesorios"}}'
```

## Deploy

Desplegado en [Render](https://render.com/) con integración continua desde la rama `main`.

## Desarrolla

Camila Barletta
[@CammiBarletta](https://github.com/CammiBarletta)