# Laboratorio #2 - Sistema de Autenticación en Laravel

## Requisitos Previos

### Tecnologías Requeridas
- **PHP** versión 8.0 o superior
- **Composer** última versión estable
- **Laravel Installer** o crear proyecto con `laravel new`
- **WAMP Server** funcionando
- **Base de datos** MySQL funcionando
- **Editor de código** Visual Studio Code
- **Node.js y NPM** para dependencias frontend

### Verificación del Ambiente
```bash
# Verificar instalaciones
php --version
composer --version
mysql --version
node --version
npm --version
```

---

## Proceso de Instalación
```bash
# Comandos ejecutados en este laboratorio:
composer create-project laravel/laravel lab-autenticacion
php artisan key:generate
php artisan migrate
composer require laravel/ui
php artisan ui bootstrap --auth
npm install
npm run dev
php artisan serve
```

---

## Introducción y Arquitectura MVC
Arquitectura Modelo-Vista-Controlador en Laravel
Laravel utiliza el patrón MVC para organizar el código de manera estructurada:
- Estructura Principal de Carpetas:
      - Controladores (app/Http/Controllers/)
      - Gestionan la lógica de la aplicación
      - Reciben peticiones HTTP y devuelven respuestas
      - Ejemplo: LoginController.php maneja el proceso de autenticación

- Modelos (app/Models/)
      - Representan los datos y la lógica de negocio
      - Interactúan con la base de datos mediante Eloquent ORM
      - Ejemplo: User.php representa la tabla de usuarios

- Vistas (resources/views/)
      - Contienen la presentación HTML de la aplicación
      - Utilizan el motor de plantillas Blade
      - Ejemplo: login.blade.php muestra el formulario de login

- Rutas (routes/)
      - Definen los endpoints de la aplicación
      - Mapean URLs a controladores específicos
      - Ejemplo: web.php contiene las rutas principales

---

## Screenshots del Laboratorio

---

## Base de Datos

En el archivo .env reemplazamos:
```bash
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=lab_autenticacion
DB_USERNAME=root
DB_PASSWORD=
```
y luego en la terminal realizamos las migraciones:
php artisan migrate
php artisan migrate:status

Como resultado deberiamos tener estas tablas:
    users - Almacena información de usuarios registrados
    password_resets - Maneja tokens para recuperación de contraseñas
    failed_jobs - Registra trabajos en cola fallidos
    sessions - Controla sesiones de usuarios activos
    cache - Almacenamiento en caché de la aplicación

---

## Dificultades

1. Error en Migración de Base de Datos
SQLSTATE[42000]: Syntax error or access violation: 
1071 Specified key was too long; max key length is 1000 bytes

Solución:
```bash
// En app/Providers/AppServiceProvider.php
use Illuminate\Support\Facades\Schema;

public function boot()
{
    Schema::defaultStringLength(191); // Reduce a 764 bytes
}
```

--- 

## Referencias

Laravel UI Package - GitHub
https://github.com/laravel/ui
Repositorio oficial del paquete de UI

MySQL Documentation
https://dev.mysql.com/doc/
Documentación para consultas específicas de base de datos

---

## Este laboratorio ha sido desarrollado por el estudiante de la Universidad Tecnológica de Panamá:
Nombre: Juan Iriarte 
Correo: juan.iriarte1@utp.ac.pa 
Curso: Ingeniería Web 
Instructor del Laboratorio: Irina Fong. 

