# config-repo

Repositorio de configuración centralizada del laboratorio **GLAB-S14** (Tecsup).

Consumido por `config-server` (puerto 8888). Cada archivo se llama igual que el
`spring.application.name` del servicio (minúsculas, sin tildes):

- `categoria-service.yml` / `-dev.yml` / `-prod.yml`
- `producto-service.yml` / `-dev.yml` / `-prod.yml`
- `cliente-service.yml` / `-dev.yml` / `-prod.yml`
- `pedido-service.yml` / `-dev.yml` / `-prod.yml`

## Perfiles

- **default** (sin perfil): propiedades comunes (`spring.jpa.*`, `mensaje.texto`).
- **dev**: puerto local y base de datos `bd_*_dev` en `localhost:3306`.
- **prod**: puerto de producción y host `servidor` (inexistente a propósito;
  nunca se arranca con este perfil en el laboratorio).

## Seguridad

No se versionan secretos: usuario y contraseña de MySQL se resuelven con
`${DB_USERNAME:root}` y `${DB_PASSWORD:}`. En producción real deben usarse
variables de entorno o cifrado (`{cipher}...`) con una clave externa.
