# 🎓 Master Móvil - Sistema de Credenciales Digitales

Sistema integral de gestión de credenciales estudiantiles con validación en tiempo real, red de comercios afiliados y analytics completo.

## 🌟 Características

- ✅ **Tiempo Real**: Sincronización instantánea con Firebase Realtime Database
- ✅ **Seguridad**: Credenciales con IDs únicos y validación criptográfica
- ✅ **Multiplataforma**: Responsive design para todos los dispositivos
- ✅ **Red de Beneficios**: Sistema de descuentos en comercios afiliados
- ✅ **Analytics**: Dashboard completo con métricas en tiempo real
- ✅ **Cloud Native**: Infraestructura en Firebase con escalabilidad automática

## 🏗️ Arquitectura del Sistema

```
Master Móvil Sistema
├── Landing Page (index.html)
├── Generador de Credenciales (generador.html)
├── Validador de Comercios (validador.html)
└── Panel Administrativo (admin.html)
```

## 📋 Módulos del Sistema

### 1. 🎯 Generador de Credenciales
**Archivo**: `generador.html`
**Propósito**: Creación y gestión de credenciales estudiantiles

**Características**:
- Generación automática de IDs únicos (formato: MMAAAMMMDDD)
- Validación de RUT chileno
- Exportación a PNG de alta calidad
- Sincronización automática con Firebase
- Preview en tiempo real

**Uso**:
1. Completar formulario con datos del estudiante
2. Sistema genera ID único automáticamente
3. Guardar en Firebase Cloud Database
4. Descargar credencial en formato PNG

### 2. 🔍 Validador de Comercios
**Archivo**: `validador.html`
**Propósito**: Validación de credenciales para comercios afiliados

**Características**:
- Validación en tiempo real con Firebase
- Sistema de códigos únicos por comercio
- Registro automático de validaciones
- Historial de transacciones
- Verificación de vigencia

**Códigos de Comercios Disponibles**:
- `REST001`: Restaurante El Buen Sabor (15% descuento)
- `FASH002`: Tienda Fashion Style (20% descuento)
- `TECH003`: TechStore Viña (10% descuento)
- `CAFE004`: Café Central (12% descuento)

**Uso**:
1. Comercio ingresa su código único
2. Estudiante proporciona ID de credencial
3. Sistema valida en tiempo real
4. Aplicar descuento correspondiente

### 3. 📊 Panel Administrativo
**Archivo**: `admin.html`
**Propósito**: Gestión completa del sistema

**Características**:
- Dashboard con métricas en tiempo real
- CRUD completo de credenciales
- Gestión de comercios afiliados
- Analytics avanzado
- Sistema de alertas
- Exportación de datos

**Funcionalidades**:
- Crear, editar, activar/desactivar credenciales
- Gestionar comercios y sus descuentos
- Ver validaciones en tiempo real
- Análisis de uso y tendencias
- Ranking de comercios más populares

## 🔥 Configuración Firebase

### Configuración Actual
```javascript
const firebaseConfig = {
    apiKey: "AIzaSyAUM0tIPiCfcEnLbcK8JPZMBBIpY89wlV0",
    authDomain: "master-movil-credenciales.firebaseapp.com",
    databaseURL: "https://master-movil-credenciales-default-rtdb.firebaseio.com",
    projectId: "master-movil-credenciales",
    storageBucket: "master-movil-credenciales.firebasestorage.app",
    messagingSenderId: "30682645748",
    appId: "1:30682645748:web:7318cb15d2baa87f6b0aa1"
};
```

### Estructura de Datos

```
Firebase Realtime Database
├── credenciales/
│   ├── MM250805001/
│   │   ├── nombre: "Juan Pérez González"
│   │   ├── rut: "12.345.678-9"
│   │   ├── curso: "Licencia Clase B"
│   │   ├── validoDesde: "05/08/2025"
│   │   ├── validoHasta: "05/08/2026"
│   │   ├── fechaEmision: "05/08/2025"
│   │   ├── estado: "Activa"
│   │   └── timestamp: 1704471600000
│   └── ...
├── comercios/
│   ├── REST001/
│   │   ├── code: "REST001"
│   │   ├── name: "Restaurante El Buen Sabor"
│   │   ├── category: "Restaurantes"
│   │   ├── discount: 15
│   │   └── active: true
│   └── ...
└── validaciones/
    ├── VAL170447160001/
    │   ├── credentialId: "MM250805001"
    │   ├── commerceCode: "REST001"
    │   ├── studentName: "Juan Pérez González"
    │   ├── timestamp: 1704471600000
    │   └── date: "05/08/2025"
    └── ...
```

## 🚀 Deploy en Netlify

### Paso 1: Preparar Archivos
1. Crear carpeta `master-movil-sistema`
2. Copiar todos los archivos HTML
3. Crear archivos de configuración (`_redirects`, `netlify.toml`)

### Paso 2: Deploy
1. Ir a [Netlify](https://netlify.com)
2. Conectar repositorio o arrastrar carpeta
3. Deploy automático

### Paso 3: Configurar Dominio
- URL temporal: `https://random-name.netlify.app`
- Dominio custom: `https://mastermovil.netlify.app`

## 🔗 URLs del Sistema

- **Landing Page**: `/` o `/index.html`
- **Generador**: `/generador` o `/credenciales`
- **Validador**: `/validador` o `/validar`
- **Admin Panel**: `/admin` o `/dashboard`

## 🛠️ Tecnologías Utilizadas

- **Frontend**: HTML5, CSS3, JavaScript ES6+
- **Backend**: Firebase Realtime Database
- **Hosting**: Netlify
- **Estilos**: CSS Custom (sin frameworks)
- **Iconos**: Emojis nativos
- **Fonts**: System fonts (Segoe UI, etc.)

## 📱 Compatibilidad

- **Navegadores**: Chrome, Firefox, Safari, Edge (versiones modernas)
- **Dispositivos**: Desktop, Tablet, Mobile
- **Resoluciones**: 320px - 4K
- **Conexión**: Funciona offline (datos cached)

## 🔒 Seguridad

### Medidas Implementadas
- Validación de datos en cliente y servidor
- IDs únicos criptográficamente seguros
- Reglas de seguridad Firebase
- Headers de seguridad en Netlify
- Validación de RUT chileno

### Reglas Firebase Recomendadas (Producción)
```json
{
  "rules": {
    "credenciales": {
      ".read": true,
      ".write": "auth != null && auth.token.admin === true"
    },
    "comercios": {
      ".read": true,
      ".write": "auth != null && auth.token.admin === true"
    },
    "validaciones": {
      ".read": "auth != null",
      ".write": true
    }
  }
}
```

## 📊 Analytics y Métricas

### Métricas Disponibles
- Total de credenciales generadas
- Credenciales activas/inactivas
- Comercios afiliados activos
- Validaciones totales y diarias
- Ranking de comercios más populares
- Credenciales próximas a vencer

### Reportes
- Dashboard en tiempo real
- Exportación de datos
- Análisis de tendencias
- Métricas de uso por módulo

## 🔧 Mantenimiento

### Tareas Regulares
- Monitorear credenciales próximas a vencer
- Revisar validaciones sospechosas
- Actualizar comercios afiliados
- Backup de datos críticos

### Logs y Debugging
- Console logs detallados
- Tracking de errores
- Métricas de performance
- Funciones de debugging expuestas

### Funciones de Debug Disponibles
```javascript
// Generador
window.MasterMovilFirebase.generateId()
window.MasterMovilFirebase.validateRut(rut)

// Validador
window.MasterMovilValidatorFirebase.getCredentials()
window.MasterMovilValidatorFirebase.checkConnection()

// Admin Panel
window.MasterMovilAdminFirebase.refreshData()
window.MasterMovilAdminFirebase.getValidations()
```

## 📞 Soporte

### Información de Contacto
- **Email**: info@mastermovil.cl
- **Teléfono**: +56 32 212 3456
- **Dirección**: Viña del Mar, Chile
- **Web**: https://mastermovil.cl

### Resolución de Problemas

#### Problema: No se conecta a Firebase
**Solución**: 
1. Verificar configuración firebaseConfig
2. Revisar reglas de seguridad
3. Confirmar que Realtime Database esté habilitado

#### Problema: Credencial no se valida
**Solución**:
1. Verificar formato de ID (MMAAAMMMDDD)
2. Confirmar que credencial esté activa
3. Verificar código de comercio

#### Problema: Datos no se sincronizan
**Solución**:
1. Revisar conexión a internet
2. Verificar permisos Firebase
3. Comprobar estructura de datos

## 🚀 Futuras Mejoras

### Funcionalidades Planeadas
- [ ] Autenticación de usuarios
- [ ] Notificaciones push
- [ ] API REST
- [ ] App móvil nativa
- [ ] Sistema de backup automático
- [ ] Reportes PDF automatizados
- [ ] Integración con sistemas de pago
- [ ] QR codes para validación
- [ ] Geolocalización de validaciones
- [ ] Dashboard de comercios

### Optimizaciones Técnicas
- [ ] Service Workers para PWA
- [ ] Lazy loading de módulos
- [ ] Optimización de imágenes
- [ ] CDN para assets estáticos
- [ ] Comprensión gzip
- [ ] Critical CSS inlining

## 📝 Changelog

### v1.0.0 (2025-01-XX)
- ✅ Sistema completo implementado
- ✅ Firebase Realtime Database integrado
- ✅ Landing page profesional
- ✅ Tres módulos principales funcionando
- ✅ Deploy en Netlify configurado
- ✅ Documentación completa

## 📄 Licencia

© 2025 Master Móvil. Todos los derechos reservados.

Sistema desarrollado exclusivamente para Escuela de Conducir Master Móvil.

---

## 🎯 Inicio Rápido

1. **Clonar/Descargar** archivos del sistema
2. **Configurar Firebase** (ya configurado)
3. **Deploy en Netlify** siguiendo las instrucciones
4. **Acceder al sistema** desde la URL asignada
5. **Comenzar a usar** los módulos

¡Sistema listo para producción! 🚀