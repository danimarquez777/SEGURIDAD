# Práctica 1 de SAD · SecureCorp — Respuestas

**Nombre y apellidos: Daniel Corbacho
**Usuario: dcorbacho

Responde con tus palabras, en 1-3 líneas. En la defensa te preguntaré lo mismo en voz alta.

**Contraseñas que has usado** (solo porque es un laboratorio; en una empresa, jamás en un fichero):

- Tu usuario: SecureCorp2026
- mtorres: SecureCorp2026

---

**1. (A1)** ¿Quién es el `issuer` de tu `ca.crt`? ¿Hasta qué fecha es válido? ¿Por qué el `subject`
y el `issuer` de la CA son iguales y los de `ldap.crt` no?

El issuer soy yo porque lo he firmado yo y es valido hasta el 4 de octubre de 2036. Son distintos el subject y el issuer porque en el CA lo firmo yo y en el ldap lo firma directamente la CA.

**2. (A3)** Pega el comando y el resultado de tus dos búsquedas:

```
a) miembros de rrhh: Lucia y Marta

b) cn y mail de todas las personas:

CN: Marta Torres 
Email: mtorres@securecorp.local

CN: dcorbacho
Email: dcorbacho@securecorp.local

```

**3. (A4)** ¿Por qué la clave `ldap.key` tiene que ser de `openldap` y tener permisos 600?

Debe ser de openldap porque el demonio LDAP se ejecuta bajo ese usuario no privilegiado y necesita poder leer el archivo para iniciar el cifrado TLS. Debe tener permisos 600 por seguridad, la clave privada debe estar protegida para que ningún otro usuario local.

**4. (A4)** ¿Qué valor has puesto en `SLAPD_SERVICES` y por qué?

He puesto SLAPD_SERVICES="ldaps:/// ldapi:///". 

Permite conexiones cifradas mediante LDAPS por el puerto 636 y conexiones locales desde la propia máquina mediante, al eliminar ldap:/// se deshabilita el puerto 389.

**5. (A4)** Antes de añadir `TLS_CACERT` en el cliente, `ldaps://` no funcionaba. ¿Por qué?

Porque el cliente no confiaba en la Autoridad de Certificación (CA) que firmó el certificado del servidor LDAP.

**6. (B3)** Pega la salida de `klist` con tus dos tickets. ¿Para qué sirve cada uno? ¿Ha viajado tu
contraseña por la red?

``` krbtgt/SECURECORP.LOCAL@SECURECORP.LOCAL

``` host/web.securecorp.local@SECURECORP.LOCAL

**7. (C)** En el `docker-compose.yml`, ¿qué diferencia hay entre `build:` e `image:`? ¿Qué
significa la línea `- "8081:80"` del servicio `phpldapadmin`?

build le indica a Docker Compose la ruta de una carpeta donde hay un Dockerfile para construir una imagen personalizada.

image e indica que utilice directamente una imagen preconstruida o descargada.

Redirige el puerto 8081 de tu ordenador físico al puerto 80 dentro del contenedor de phpldapadmin.

**8. (C)** ¿Por qué en la máquina `web` no has tenido que escribir a mano `TLS_CACERT`, y en el
cliente sí? 

Porque en el Dockerfile de la máquina web se copió el certificado a la carpeta del sistema.

¿Qué pasaría con esa línea del cliente si hicieras `./lab.sh reset`?

Se destruirá el contenedor del cliente y sus archivos del sistema.