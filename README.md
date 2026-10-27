# Backend Clínica Petsalud

Proyecto Spring Boot 3.3.6, Java 17+, Spring Security, Spring Data JPA y MySQL. Se conserva el backend funcional original y su configuración de autenticación basada en usuarios de la base de datos.

## Requisitos
- JDK 17 o superior (con JDK 24, Lombok 1.18.40 está configurado para evitar incompatibilidad del compilador).
- MySQL Server en ejecución.

## Base de datos
La configuración predeterminada de `src/main/resources/application.properties` utiliza `petsalud_db`, usuario `root` y contraseña vacía, e intenta crear la base de datos automáticamente si el usuario tiene permisos. Si tu instalación de MySQL usa otros datos, define las variables de entorno `DB_URL`, `DB_USERNAME` y `DB_PASSWORD`; no es necesario editar el código.

## Ejecutar en macOS/Linux
Desde esta carpeta del proyecto:

```bash
chmod +x mvnw
./mvnw clean compile
./mvnw spring-boot:run
```

En Windows, usar `mvnw.cmd clean compile` y `mvnw.cmd spring-boot:run`.

## Seguridad incluida
- `UsuarioDetailsService` recupera las cuentas desde el repositorio de usuarios.
- `BCryptPasswordEncoder` para el hash de contraseñas.
- Spring Security configura autenticación HTTP Basic, protección CSRF y autorización por autoridades `ADMIN` y `VETERINARIO`; las demás rutas requieren autenticación.
- El registro y login se mantienen públicos según la configuración actual del proyecto.

## Antes de entregar
La compilación debe verificarse en el equipo donde se ejecute. Para probar endpoints protegidos se necesita una cuenta válida en la base de datos y una contraseña almacenada con BCrypt. Esta configuración no sustituye una auditoría de seguridad completa; se deben revisar las validaciones de entradas y los controles de autorización de cada controlador antes de desplegar en producción.
