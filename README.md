# Meta Force App 💪

Aplicación completa de gestión de gimnasios con control de acceso mediante códigos QR, gestión de usuarios, centros, máquinas y clases.

## 📖 Descripción

Meta Force es una plataforma integral para la gestión de gimnasios que permite:

- **Control de acceso**: Sistema de entrada/salida mediante escaneo de códigos QR
- **Gestión de usuarios**: Administración completa con diferentes roles y permisos
- **Gestión de centros**: Control de múltiples ubicaciones de gimnasios
- **Gestión de máquinas**: Inventario y seguimiento de equipamiento
- **Gestión de clases**: Programación y administración de clases grupales
- **Multi-idioma**: Soporte para español, inglés y francés
- **Temas**: Modo claro y oscuro

## 🏗️ Arquitectura

El proyecto está dividido en dos repositorios principales que funcionan como submódulos:

```
Meta-Force-App/
├── front/          # Frontend (Angular)
└── back/           # Backend (Node.js + Express + PostgreSQL)
```

### Frontend
- **Repositorio**: [Meta_Force_front](https://github.com/Mariogarluu/Meta_Force_front)
- **Framework**: Angular 19.2
- **Tecnología**: TypeScript
- **Estilos**: Tailwind CSS
- **Puerto por defecto**: 4200

### Backend
- **Repositorio**: [Meta_Force_back](https://github.com/Mariogarluu/Meta_Force_back)
- **Framework**: Express 5.1
- **Runtime**: Node.js
- **Base de datos**: PostgreSQL
- **ORM**: Prisma 6.18
- **Puerto por defecto**: 3000

## 🚀 Tecnologías Principales

### Frontend
| Tecnología | Versión | Propósito |
|-----------|---------|-----------|
| **Angular** | 19.2 | Framework principal |
| **TypeScript** | 5.7 | Lenguaje de programación |
| **Tailwind CSS** | 3.4 | Framework de estilos |
| **ngx-translate** | 17.0 | Internacionalización (i18n) |
| **RxJS** | 7.8 | Programación reactiva |
| **html5-qrcode** | 2.3 | Generación y escaneo de QR |
| **jsonwebtoken** | 9.0 | Manejo de JWT |

### Backend
| Tecnología | Versión | Propósito |
|-----------|---------|-----------|
| **Node.js** | 18+ | Runtime JavaScript |
| **Express** | 5.1 | Framework web |
| **TypeScript** | 5.9 | Lenguaje de programación |
| **Prisma** | 6.18 | ORM para PostgreSQL |
| **PostgreSQL** | 14+ | Base de datos relacional |
| **JWT** | 9.0 | Autenticación con tokens |
| **bcrypt** | 6.0 | Hash de contraseñas |
| **Zod** | 4.1 | Validación de esquemas |
| **Jest** | 30.2 | Framework de testing |
| **Swagger** | - | Documentación de API |
| **Winston** | 3.18 | Sistema de logging |
| **Helmet** | 8.1 | Seguridad HTTP |
| **express-rate-limit** | 8.2 | Limitación de peticiones |

## 📋 Requisitos Previos

- **Node.js** (versión 18 o superior)
- **npm** (viene incluido con Node.js)
- **PostgreSQL** (versión 14 o superior)
- **Git**

## 🔧 Instalación Completa

### 1. Clonar el Repositorio Principal con Submódulos

```bash
# Clonar con todos los submódulos
git clone --recursive https://github.com/Mariogarluu/Meta-Force-App.git
cd Meta-Force-App

# Si ya clonaste sin --recursive, inicializa los submódulos:
git submodule init
git submodule update
```

### 2. Configurar el Backend

```bash
cd back

# Instalar dependencias
npm install

# Copiar archivo de configuración
cp .env.example .env

# Editar .env con tus configuraciones
# Asegúrate de configurar:
# - DATABASE_URL (PostgreSQL)
# - JWT_SECRET
# - PORT (por defecto 3000)

# Generar cliente de Prisma
npm run prisma:generate

# Ejecutar migraciones
npm run prisma:migrate

# Iniciar servidor de desarrollo
npm run dev
```

El backend estará disponible en `http://localhost:3000`

### 3. Configurar el Frontend

```bash
cd ../front

# Instalar dependencias
npm install

# Iniciar servidor de desarrollo
npm start
```

El frontend estará disponible en `http://localhost:4200`

## 🎯 Características Principales

### 🔐 Sistema de Autenticación
- Registro de nuevos usuarios
- Login con JWT
- Roles y permisos (SUPERADMIN, ADMIN_CENTER, TRAINER, CLEANER, USER)
- Estados de usuario (PENDING, ACTIVE, INACTIVE)

### 👥 Gestión de Usuarios
- CRUD completo de usuarios
- Asignación de roles
- Gestión de estados
- Vinculación con centros

### 🏢 Gestión de Centros
- Administración de múltiples ubicaciones
- Información detallada (nombre, descripción, dirección)
- Relación con usuarios y máquinas

### 🏋️ Gestión de Máquinas
- Inventario de equipamiento
- Tipos de máquinas
- Asignación por centro
- Control de disponibilidad

### 📅 Gestión de Clases
- Programación de clases grupales
- Control de capacidad
- Asignación de entrenadores
- Inscripción de usuarios

### 📱 Sistema QR
- Generación de códigos QR únicos por usuario
- Escaneo para entrada/salida
- Registro automático de accesos
- Historial de visitas

### 🌍 Internacionalización
- **Español** (idioma por defecto)
- **Inglés**
- **Francés**
- Cambio dinámico de idioma
- Persistencia de preferencias

### 🎨 Temas
- Modo claro
- Modo oscuro
- Toggle en todas las páginas
- Persistencia en localStorage

## 📚 Documentación de la API

La documentación completa de la API está disponible en **Swagger UI**:

**URL**: `http://localhost:3000/api-docs`

### Endpoints Principales

#### Autenticación
- `POST /api/auth/register` - Registro de usuarios
- `POST /api/auth/login` - Login y obtención de JWT

#### Usuarios (Requieren autenticación)
- `GET /api/users` - Listar usuarios
- `GET /api/users/me` - Perfil del usuario autenticado
- `GET /api/users/:id` - Obtener usuario por ID
- `PATCH /api/users/:id` - Actualizar usuario
- `DELETE /api/users/:id` - Eliminar usuario

#### Centros
- `GET /api/centers` - Listar centros
- `POST /api/centers` - Crear centro (SUPERADMIN)
- `GET /api/centers/:id` - Obtener centro por ID
- `PATCH /api/centers/:id` - Actualizar centro
- `DELETE /api/centers/:id` - Eliminar centro

#### Máquinas
- `GET /api/machines` - Listar máquinas
- `POST /api/machines` - Crear máquina
- `GET /api/machines/:id` - Obtener máquina por ID
- `PATCH /api/machines/:id` - Actualizar máquina
- `DELETE /api/machines/:id` - Eliminar máquina

#### Clases
- `GET /api/classes` - Listar clases
- `POST /api/classes` - Crear clase
- `GET /api/classes/:id` - Obtener clase por ID
- `PATCH /api/classes/:id` - Actualizar clase
- `DELETE /api/classes/:id` - Eliminar clase

#### Control de Acceso
- `POST /api/access/scan` - Escanear código QR para entrada/salida

## 🧪 Testing

### Backend
```bash
cd back

# Ejecutar todas las pruebas
npm test

# Modo watch
npm run test:watch

# Reporte de cobertura
npm run test:coverage
```

### Frontend
```bash
cd front

# Ejecutar pruebas
npm test
```

## 🐳 Despliegue con Docker

### Backend con Docker

```bash
cd back

# Desarrollo
docker-compose up

# Producción
docker-compose -f docker-compose.prod.yml up -d
```

## 🔒 Seguridad

El proyecto implementa múltiples capas de seguridad:

- ✅ **JWT**: Autenticación con tokens seguros
- ✅ **bcrypt**: Hash de contraseñas con salt
- ✅ **Helmet**: Protección de headers HTTP
- ✅ **CORS**: Configuración de origen cruzado
- ✅ **Rate Limiting**: Límite de peticiones por IP
- ✅ **Validación**: Validación de entrada con Zod
- ✅ **Roles y Permisos**: Control de acceso basado en roles

## 📁 Estructura del Proyecto

```
Meta-Force-App/
├── front/                          # Aplicación Frontend
│   ├── src/
│   │   ├── app/
│   │   │   ├── core/              # Servicios core (auth, theme, translation)
│   │   │   ├── pages/             # Páginas de la aplicación
│   │   │   │   ├── home/          # Página principal
│   │   │   │   ├── login/         # Login
│   │   │   │   ├── register/      # Registro
│   │   │   │   ├── dashboard/     # Dashboard
│   │   │   │   ├── users/         # Gestión de usuarios
│   │   │   │   ├── centers/       # Gestión de centros
│   │   │   │   ├── machines/      # Gestión de máquinas
│   │   │   │   ├── qr/            # Código QR
│   │   │   │   └── qr-scanner/    # Escáner QR
│   │   │   └── shared/            # Componentes compartidos
│   │   │       └── components/
│   │   │           ├── navbar/    # Barra de navegación
│   │   │           ├── theme-toggle/     # Toggle de tema
│   │   │           └── language-selector/ # Selector de idioma
│   │   └── assets/                # Recursos estáticos
│   ├── public/
│   │   └── assets/
│   │       └── i18n/              # Archivos de traducción (es, en, fr)
│   ├── angular.json               # Configuración de Angular
│   ├── tailwind.config.js         # Configuración de Tailwind
│   └── package.json
│
└── back/                           # API Backend
    ├── src/
    │   ├── app.ts                 # Configuración de Express
    │   ├── index.ts               # Punto de entrada
    │   ├── config/                # Configuraciones (DB, Swagger)
    │   ├── middleware/            # Middlewares (auth, validación, errores)
    │   ├── modules/               # Módulos de la aplicación
    │   │   ├── auth/              # Autenticación
    │   │   ├── users/             # Gestión de usuarios
    │   │   ├── centers/           # Gestión de centros
    │   │   ├── machines/          # Gestión de máquinas
    │   │   ├── classes/           # Gestión de clases
    │   │   └── access/            # Control de acceso (QR)
    │   ├── types/                 # Tipos TypeScript
    │   ├── utils/                 # Utilidades (logger, validación)
    │   └── tests/                 # Pruebas unitarias
    ├── prisma/
    │   ├── schema.prisma          # Esquema de base de datos
    │   └── migrations/            # Migraciones de Prisma
    ├── docs/                      # Documentación adicional
    ├── Dockerfile                 # Configuración Docker
    ├── docker-compose.yml         # Docker Compose
    └── package.json
```

## 📝 Scripts Disponibles

### Frontend
```bash
npm start              # Servidor de desarrollo
npm run build          # Compilar para producción
npm run watch          # Compilar en modo desarrollo con watch
npm test               # Ejecutar pruebas
```

### Backend
```bash
npm run dev            # Servidor de desarrollo con nodemon
npm run build          # Compilar TypeScript
npm start              # Servidor en producción
npm test               # Ejecutar pruebas
npm run test:coverage  # Reporte de cobertura
npm run prisma:migrate # Ejecutar migraciones
npm run prisma:studio  # Abrir Prisma Studio
```

## 🤝 Contribuir

### Flujo de Trabajo

1. **Crea una rama** con un nombre descriptivo:
   ```bash
   git checkout -b feature/nueva-funcionalidad
   ```

2. **Realiza tus cambios** siguiendo las convenciones del proyecto

3. **Prueba tus cambios** antes de hacer commit:
   ```bash
   # Backend
   cd back && npm test
   
   # Frontend
   cd front && npm test
   ```

4. **Commit y push**:
   ```bash
   git add .
   git commit -m "Descripción clara de los cambios"
   git push origin feature/nueva-funcionalidad
   ```

5. **Actualiza develop** antes de mergear:
   ```bash
   git checkout develop
   git pull origin develop
   git checkout feature/nueva-funcionalidad
   git merge develop
   ```

6. **Resuelve conflictos** si existen y prueba nuevamente

7. **Mergea a develop**:
   ```bash
   git checkout develop
   git merge feature/nueva-funcionalidad
   git push origin develop
   ```

### Convenciones

- ✅ Escribe código limpio y documentado
- ✅ Sigue las convenciones de código del proyecto
- ✅ Añade traducciones para nuevos textos (es, en, fr)
- ✅ Actualiza la documentación cuando sea necesario
- ✅ Escribe pruebas para nuevas funcionalidades
- ✅ Realiza commits frecuentes con mensajes descriptivos

## 📖 Documentación Adicional

- **Frontend**: Ver [front/README.md](./front/README.md)
- **Backend**: Ver [back/README.md](./back/README.md)
- **API Examples**: Ver `back/docs/API_EXAMPLES.md`
- **Changelog**: Ver `back/CHANGELOG.md`
- **Swagger UI**: `http://localhost:3000/api-docs`

## 🐛 Resolución de Problemas

### El backend no se conecta a la base de datos
- Verifica que PostgreSQL esté ejecutándose
- Revisa la configuración de `DATABASE_URL` en `.env`
- Ejecuta las migraciones: `npm run prisma:migrate`

### El frontend no se comunica con el backend
- Verifica que el backend esté ejecutándose en el puerto 3000
- Revisa la configuración de CORS en el backend
- Comprueba la URL de la API en el frontend

### Error al inicializar los submódulos
```bash
git submodule deinit -f .
git submodule init
git submodule update
```

## 👨‍💻 Autores

**Meta Force Team**

## 📄 Licencia

Este proyecto es privado y pertenece a Meta Force.

---

⭐ Si tienes alguna pregunta o sugerencia, no dudes en abrir un issue en GitHub.
